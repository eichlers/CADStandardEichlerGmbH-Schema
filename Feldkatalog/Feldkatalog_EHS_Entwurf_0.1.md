# Feldkatalog EHS – Entwurf 0.1

Stand 23.10.2026 · AMK · nur Text, nichts gebaut. Zusammengeführt aus `Felder_ATT.md`, `Felder_ADM.md`,
`Felder_ANA.md`, `README.md` und `Pruefung/Entscheidungsliste_EHS_0.1.md`. Eigene Vorschläge sind als **Vorschlag AMK**
gekennzeichnet; alle anderen Felder stammen aus mindestens einer Modulliste.

## 1 Zweck und Grundsätze

**Zweck:** Der Katalog legt fest, welche Felder der neue Basis-Satz `EHS_Bauteil` hat, wer jedes Feld schreibt und wer
es liest. Neue Stempel (ATT), neue Tabellen (ADM), die neue Datenbank-Anbindung (ADM) und ANA beziehen sich nur auf
diesen Katalog. `TAGBauteil` entfällt in der EHS-Vorlage; alte Zeichnungen behalten ihn, ein Umstellbefehl übernimmt die
Werte einmal (README Grundsatz 3). Keine CustomUser-Felder in `EHS_Bauteil`.

**Grundsätze:**

1. **Ein Schreiber je Wert.** Jedes Feld hat genau einen Schreiber (ein Modul, die Hand des Planers über genau ein
   Fenster, oder automatisch aus Stil, Leitung bzw. Raum). Kein Wert steht in zwei Sätzen.
2. **Eingabe ≠ Ergebnis.** Was der Planer vorgibt oder aus dem Datenblatt übernimmt, ist ein anderer Wert als das, was
   ANA rechnet. Eingaben und Ergebnisse haben getrennte Felder; ein Ergebnis überschreibt nie eine Eingabe.
3. **Namensregel (aus ADM):** Feldnamen nur aus Buchstaben und Ziffern, keine Umlaute, keine Punkte, keine
   Leerzeichen, nicht mit einer Ziffer beginnend. Der Anzeigename mit Umlaut steht im Katalog.
   *Vorschlag AMK:* auch keine Unterstriche in Feldnamen von `EHS_*`-Sätzen (die ATT-Vorschläge `Kennzeichen_Anlage` usw.
   werden zu `Anlage`, `KennzeichenNummer` …). Satznamen behalten das Präfix `EHS_`. Die ANA-Felder `Erg_…` bleiben, wie
   sie sind (ATT-Beschriftungen und Anzeigethemen hängen am Namen).
4. **Einheiten nur im Katalog**, nie im Feldnamen und nie im Wert. Zahlen als **Real** oder **Integer**, nicht als Text
   („12,5“, nicht „12,5 kW“).
5. **Listenfelder** nur mit fester Werteliste; die Liste steht in den Stammdaten.
6. **Was das Bauteil ist und wo es ist** gehört in `EHS_Bauteil`; **was gerechnet wird** bleibt im Satz des rechnenden
   Moduls; **Projektwünsche** gehören in `EHS_Projekt`.

Abkürzungen: **auto** = automatisch (Stil, Leitung/System oder Raum, kein Modul schreibt), **P** = Pflicht.

## 2 `EHS_Bauteil` – Felder

Hängt an jedem Schemasymbol (Bauteil), nicht an Leitungen und nicht an Beschriftungen.

### 2.1 Kennung und Kennzeichen

| Feldname | Bedeutung | Typ / Einheit | Schreiber | Leser | P | ersetzt |
|---|---|---|---|---|---|---|
| `Kennung` | dauerhafte, weltweit eindeutige Kennung des Bauteils (Datenbankschlüssel) | Text (GUID, 36 Zeichen), nur lesen | das Modul, das den Satz anhängt, einmalig; ADM repariert nur auf Befehl (siehe Konflikt d) | ADM (Datenbank, Excel/XML, Projektansicht), alle Module intern | ja | – (heute Handle + Zeichnungskennung + Export-Nr.) |
| `KennungHandle` | Handle, für den die Kennung vergeben wurde; anderes Handle = Kopie | Text, nur lesen | wie `Kennung` | ADM, alle Module beim Prüfen | ja | – |
| `Kennzeichen` | vollständiges Anlagenkennzeichen (TAG), z. B. `01VDV01` | Text | ATT (Nummerieren; Handänderung nur über die ATT-Palette, wird als „von Hand“ markiert) | Stempel, ADM/Datenbank (eindeutig), ANA (Bericht, Fenster), Listen | ja, wenn getaggt | `TAGBauteil.PosNr`, `ANA_Hydraulik.Kennzeichen` |
| `Anlage` | Teil 1 des Kennzeichens: Anlagen- bzw. Systemnummer, z. B. `01`, RLT-Anlage `03` | Text (2 Stellen, führende Null) | ATT beim Nummerieren | ADM (Filter, Listenkopf), ATT | ja, mit Kennzeichen | Anteil von `TAGBauteil.PosNr`; Anlage im ATT-Register |
| `KennzeichenNummer` | Teil 3 des Kennzeichens: laufender Zähler je Anlage + Kürzel | Integer (1–99 999) | ATT | ATT (Lücken, Fortsetzen), ADM (sortieren) | ja, mit Kennzeichen | Anteil von `TAGBauteil.PosNr` (offen, Frage 4) |
| `KennzeichenGesperrt` | Kennzeichen freigegeben/eingefroren, ATT ändert es nicht mehr | Ja/Nein | ATT (Sperren/Freigeben) | ADM, alle Module (Warnung) | nein | Spiegel der Freigaben im ATT-Register (offen, Frage 5) |
| `Taggen` | soll das Bauteil ein Kennzeichen bekommen: ja / optional / nie / ausgeschlossen | Liste | Vorgabe auto aus dem Stil (Stammdaten); „ausgeschlossen“ setzt nur ATT | ATT, ADM | nein | AKS-Liste „taggen“ + Ausschluss im ATT-Register |

### 2.2 Klassifikation

| Feldname | Bedeutung | Typ / Einheit | Schreiber | Leser | P | ersetzt |
|---|---|---|---|---|---|---|
| `Kuerzel` | Bauteilkürzel, z. B. `VDV`, `PU`, `FMW` | Text, auto | auto aus der Stilbeschreibung (gepflegt von ASG am Stil) | ATT (Kennzeichen), ANA (Erkennung), ADM (Legende T1, Listen), Stempel | ja (auto) | `TAGBauteil.KurzZeichenSymbol`, `StilSchemaSymbol.KurzZeichenSymbol` |
| `Benennung` | Benennung laut Stammdaten (= Name des Symbolstils) | Text, auto | auto aus dem Stil (ASG) | ADM (Legende T1, Spalte „Bauteil“), ATT, Stempel | ja (auto) | `StilSchemaSymbol.Stil`; Feld „Bauteilart = Stilname“ aus der ATT-Liste |
| `Bauteilart` | Gruppe/Funktion: Armatur, Pumpe, Verbraucher, Erzeuger, Systemtrennung, Verteiler, Speicher, Luftdurchlass, Filter, Messstelle, Sensor, Sonstiges (ADM); ANA nennt zusätzlich Weiche, Formstück | Liste, auto | auto aus dem Stil über die Stammdaten (ASG) | Auswahlregel aller Listen T2–T16 (ADM), ANA (statt Rolle), ATT | ja (auto) | – (heute nur Stilname bzw. `ANA_Hydraulik.Rolle`) |
| `Armaturart` | Unterart bei Armaturen und Formstücken (Regelventil, PICV, Schmutzfänger, Reduzierung, Materialwechsel …) | Liste (Werte aus dem ANA-Enum) | Vorbelegung aus den Stammdaten beim Einfügen; Änderung nur über das ANA-Fenster (siehe Konflikt b) | ANA, ADM (Ventilliste T2), ATT | nein | `ANA_Armatur.ArmaturArt` |
| `System` | Systemkürzel = LabelName der Systemdefinition = AKS, z. B. `PWW-VL` | Text, auto | auto aus Leitung/System | ATT (Kennzeichen), ADM (Listen, Filter), ANA, Stempel | ja (auto) | `TAGBauteil.SystemAbkz.`, `TAGBauteil.System` |
| `SystemBenennung` | voller Systemname, z. B. „Pumpen-Warm-Wasser-Vorlauf“ | Text, auto | auto aus der Systemdefinition | ATT, Stempel | nein | `TAGBauteil.System` (**Vorschlag AMK** für den Namen, siehe Konflikt g) |

### 2.3 Ort

| Feldname | Bedeutung | Typ / Einheit | Schreiber | Leser | P | ersetzt |
|---|---|---|---|---|---|---|
| `Gebaeude` | Gebäude | Text | Planer über ADM oder ATT (ADM „Füllen“) | Listen, Filter | nein | – |
| `Geschoss` | Geschoss | Text | Planer über ADM oder ATT | Listen, Filter, Raumbuch | nein | `PositionsAnker.Geschoss` |
| `Zone` | Zone bzw. Bereich | Text | Planer über ADM oder ATT | Listen T2, T5, T6, Filter, Stempel | nein | `TAGBauteil.Zone` |
| `Raumnummer` | Raum, in dem das Bauteil wirkt | Text | Planer über ADM oder ATT; Füllhilfe aus dem Raum (`PositionsAnker`) auf Befehl (siehe Konflikt h) | ATT (Profile „nach Raum“), ADM (T6, T15) | nein | `PositionsAnker.Nummer` |
| `Raumname` | Name dieses Raums | Text | wie `Raumnummer` | wie `Raumnummer` | nein | `PositionsAnker.Name` |

### 2.4 Produkt

| Feldname | Bedeutung | Typ / Einheit | Schreiber | Leser | P | ersetzt |
|---|---|---|---|---|---|---|
| `Hersteller` | festgelegter Hersteller | Text | Planer: über ADM von Hand, oder über ANA nur mit Knopf „Übernehmen“ (siehe Konflikt c) | Listen T2, T5, T7, Stempel, ANA | nein | `TAGBauteil.Fabrikat`, `ANA_Armatur.Hersteller`, `ANA_Armatur.Erg_HerstellerGewaehlt` |
| `Produktreihe` | Serie | Text | wie `Hersteller` | ANA, ADM | nein | `ANA_Armatur.Produktreihe` |
| `Typ` | festgelegter Typ bzw. Produkt | Text | wie `Hersteller` | Listen, Stempel | nein | `TAGBauteil.Typ`, `ANA_Armatur.Erg_Produkt` |
| `Artikelnummer` | Bestellnummer des Herstellers | Text | wie `Hersteller` | ADM (T2, Excel), ATT | nein | `ANA_Armatur.ProduktAuswahl`, `ANA_Armatur.Erg_Artikelnummer` |
| `Bestelltext` | Langtext für LV/Bestellung | Text | wie `Hersteller` (ANA aus dem Messstellen-Katalog nur beim Übernehmen) | ADM (T2) | nein | `ANA_Armatur.Erg_Bestelltext` |
| `Merkmale` | technische Daten produktneutral („Anzeigebereich: 0 … 120 °C“) | Text | Planer über das ANA-Fenster | ATT, ADM | nein | `ANA_Armatur.Merkmale` |

### 2.5 Nennwerte / Auslegung (Eingaben des Planers bzw. Datenblattwerte – siehe Konflikt a)

| Feldname | Bedeutung | Typ / Einheit | Schreiber | Leser | P | ersetzt |
|---|---|---|---|---|---|---|
| `NennweiteAnschluss` | DN der Anschlüsse laut Datenblatt (0 = unbekannt) | Integer, DN | Planer über ADM oder ANA-Fenster; ANA-Produktwahl nur mit „Übernehmen“ | ANA (Reduzierungsprüfung), ATT (Stempel), ADM | nein | `ANA_Hydraulik.AnschlussDN`, `ANA_Armatur.Nennweite`, `TAGBauteil.Groesse` |
| `Nennleistung` | Leistung laut Auslegung/Datenblatt: am Verbraucher Bedarfsleistung, an Erzeuger und Systemtrennung Nennleistung | Real, kW | Planer über ADM oder ANA-Fenster | ANA (Eingabe), ATT, ADM (T6, T7, T8) | nein | `ANA_Hydraulik.Leistung`, `.Nennleistung`, `.TrennungLeistung`; `TAGBauteil.Leistung`; `EDaten.Leistung` |
| `Spreizung` | Auslegungsspreizung | Real, K | Planer | ANA, ATT, ADM (T6) | nein | `ANA_Hydraulik.Spreizung` |
| `VolumenstromNenn` | Volumenstrom laut Datenblatt bzw. Auslegungspunkt der Pumpe | Real, m³/h | Planer über ADM oder ANA-Fenster | ANA (Soll-Volumenstrom Pumpe), ATT, ADM (T5) | nein | `ANA_Hydraulik.VolumenstromGewaehlt`; `TAGBauteil.DurchFluss` (Eingabeteil); EDaten-Volumenstrom |
| `DruckverlustNenn` | Δp bei Nennvolumenstrom laut Datenblatt | Real, kPa | Planer über ADM oder ANA-Fenster | ANA, ADM (T6, T7) | nein | `ANA_Hydraulik.DruckverlustBauteil` |
| `Wasserinhalt` | Inhalt laut Datenblatt | Real, l | Planer über ADM oder ANA-Fenster | ANA (Anlageninhalt), ADM (T11) | nein | `ANA_Hydraulik.Wasserinhalt` |
| `ElektrischeLeistung` | P1 laut Hersteller (Pumpe, Gerät) | Real, W (siehe Konflikt i) | Planer über ADM oder ANA-Fenster | ANA (Pumpenenergie), Elektro, ADM | nein | `ANA_Hydraulik.PumpenP1Hersteller`; `EDaten.Leistung` (Elektro) |

### 2.6 Status und Sonstiges

| Feldname | Bedeutung | Typ / Einheit | Schreiber | Leser | P | ersetzt |
|---|---|---|---|---|---|---|
| `Status` | Planungsstand: neu, Bestand, Rückbau, entfällt | Liste, Vorgabe „neu“ | Planer über ADM | alle Listen, Datenbank (gelöscht ≠ entfällt) | nein | – |
| `Betrieb` | Laufend / Reserve | Liste | Planer über ANA-Fenster oder ADM | ANA, ADM | nein | `ANA_Hydraulik.Betrieb` |
| `Anzahl` | Stückzahl, wenn ein Symbol mehrere gleiche Bauteile vertritt | Integer, Vorgabe 1 | Planer | Listen, Stückliste T14 | nein | `TAGRLTFilter.Anzahl` |
| `Bezeichnung` | Freitext zum Bauteil („Heizregister RLT 3“) | Text | Planer über ADM oder ATT | Listen T6, T7, Stempel | nein | `TAGBauteil.BezeichnungFreitext` |
| `Bemerkung` | Bemerkung | Text | Planer | Listen (letzte Spalte), Stempel | nein | `TAGBauteil.Bemerkung` |

**Summe: 36 Felder** (7 Kennung/Kennzeichen · 6 Klassifikation · 5 Ort · 6 Produkt · 7 Nennwerte · 5 Status/Sonstiges),
davon 6 automatisch (`Kuerzel`, `Benennung`, `Bauteilart`, `System`, `SystemBenennung`, Vorgabe von `Taggen`).

**Bewusst nicht in `EHS_Bauteil`:**
- alle Rechenergebnisse `Erg_…` (Volumenstrom, Leistung, Δp, DN gewählt, Voreinstellung, kv, Förderhöhe …) → ANA-Sätze;
- ANA-eigene Eingaben (Temperaturen, Kreisname, Trennung je Seite, Pumpenbauart/-regelung, Verteiler, Behälter,
  ReduzierungImAnschluss, PumpeImErzeuger …) → `ANA_Hydraulik` / `ANA_Armatur`;
- `Medium` → System/Kreis (Konflikt f);
- freie Beschriftungszeilen (`Beschriftung01–04`, `XTagZeile01–10`), weitere Kennzeichen (z. B. Roche `FilterNummer`),
  Profilbausteine (`Luftart`, `RaumKurz`, `Modul`, `Operation`) → `EHS_Projekt`;
- Zeichnungskennung, Abgleichstand, „GeaendertAm“, Löschmarke → Zeichnungsebene bzw. Datenbank (ADM Abschnitt 3);
- `Druck` (bar) und `Einstellwert` aus den alten ATT-Stempeln: `Einstellwert` ist das ANA-Ergebnis
  `ANA_Armatur.Erg_Voreinstellung`; für `Druck` nennt keine Quelle eine feste Bedeutung → erst aufnehmen, wenn sie
  geklärt ist (**Vorschlag AMK**, Frage 1).

## 3 Andere Sätze und Ablagen

| Satz / Ablage | Zweck | hängt an |
|---|---|---|
| `EHS_Projekt` | optionale Projektfelder mit sprechenden Namen aus dem Projektprofil (Typ, Werteliste, ggf. „eindeutig“ für die ADM-Redundanzprüfung); ATT schreibt nur in Felder, die das Profil als Ziel nennt. Wiederkehrende Felder wandern später nach `EHS_Bauteil`. Keine eigene Kennung. | nur Bauteile, die es brauchen |
| `EHS_Stil` (**Vorschlag AMK**, von ADM als Möglichkeit genannt) | stilbasierter Satz, der `Kuerzel`, `Benennung`, `Bauteilart`, Vorgabe `Taggen` und Vorbelegung `Armaturart` aus Stilbeschreibung/Stammdaten liefert; `EHS_Bauteil` zeigt sie als automatische Felder | Symbolstile (ASG) |
| `ANA_Hydraulik` | ANA-Eingaben am Bauteil und alle Ergebnisse `Erg_…`; andere Module lesen nur | Schemasymbole, die ANA beim Erfassen anhängt; heute auch Leitungen; nie Beschriftungen (C3) |
| `ANA_Armatur` | Armaturdaten von ANA: KvsVorgabe, Schliessfeder, Einbaulage, VolumenstromVorgabe, TemperaturSekundaerVorlauf und alle `Erg_…` | nur Armaturen |
| `ANA_Leitung` (Vorschlag ANA) | schlanker Satz für Leitungen: 3 Eingaben (Gleichzeitigkeit, Auslegung, LaengeVorgabe) + Ergebnisse (Volumenstrom, v, R, Teilstrecke …), statt ~115 Felder `ANA_Hydraulik` | Schemalinien |
| `ATT_REGISTER` | Xrecord im Wörterbuch der Zeichnung: Freigaben, Höchststand je Nummernkreis, Ausschlüsse mit Grund, Prüfausschluss, „von Hand geändert“, Anlage je Bauteil (Lüftung), Zeichnungswerte, Profilwahl | Zeichnung (kein Satz am Bauteil) |
| `ATT_BAUGRUPPE_FREMD` | RegApp/XData für Baugruppen, kein Satz | Bauteile in Baugruppen |
| `EHS_Zeichnung` (ADM) | Wörterbuch-Eintrag: ZeichnungsKennung (GUID), gespeicherter Dateipfad, Projekt, Nummer/Zeit des letzten Abgleichs | Zeichnung |
| `EHS_Raum` (ADM) | Raumsatz für das Raumbuch T13: Nummer, Name, Geschoss, Fläche, Höhe, Volumen (Formel), Zu-/Ab-/Umluft, Temperatur, Feuchte, Druckstufe, Reinraumklasse; ersetzt `HVACRaum` | Räume |
| `EHS_BMK` (Vorschlag ATT) | ein Satz statt 4 × `TAGBMK*`: `BMKArt` (Fremd/Gebäude/Monitoring/Prozess), `BMKNummer`, `BMKFunktion`, `BMKAuswertung`; von Hand (MSR), ATT prüft Doppelungen | MSR-Bauteile |
| `EHS_Filter` (Vorschlag ATT) | Typsatz RLT-Filter: Filterklasse, Nennluftmenge, Abmessungen, Messstutzen; ersetzt `TAGRLTFilter` | Filter |
| `EHS_Luft`, `EHS_MSR` (Kandidaten ADM, noch nicht festlegen) | Lüftung/MSR/Elektro: Luftvolumenstrom, Filterklasse, Abmessung, Messstellennummer, BMK-Zählnummer, Funktion, elektrische Leistung, Spannung; ersetzen `TAGRLTFilter`, `TAGBMK…`, `EDaten` | – (siehe Konflikt j) |

## 4 Konflikte zwischen den Modulen

**(a) Nennleistung, VolumenstromNenn, DruckverlustNenn, Nennweite.**
ANA will die Datenblatt-/Auslegungswerte einmal in `EHS_Bauteil` und keine eigene Kopie mehr. ADM will Leistung,
Volumenstrom, Δp und DN nicht in `EHS_Bauteil`, sondern alles in den ANA-Sätzen (Grund: „ein Ort je Angabe“, Ergebnisse
bleiben bei ANA). Die frühere Entscheidungsliste (C2) sagte „ANA-Sätze führend“ – damals mit `TAGBauteil` als
Transportkopie.
**Vorschlag AMK:** Planer- und Datenblattwerte (`NennweiteAnschluss`, `Nennleistung`, `Spreizung`, `VolumenstromNenn`,
`DruckverlustNenn`, `Wasserinhalt`, `ElektrischeLeistung`) stehen in `EHS_Bauteil`; Rechenergebnisse `Erg_…` nur in ANA.
Begründung:
1. ADMs eigener Maßstab ist „was das Bauteil *ist*“ – ein Datenblattwert gehört dazu, ein Rechenergebnis nicht.
2. „Ein Ort je Angabe“ bleibt erfüllt, weil ANA seine Eingabefelder (`Leistung`, `Nennleistung`, `TrennungLeistung`,
   `AnschlussDN`, `DruckverlustBauteil`, `VolumenstromGewaehlt`, `Wasserinhalt`, `PumpenP1Hersteller`) streicht.
3. Bauteile, die ANA nicht rechnet (Lüftung, Elektro), brauchen Nennwerte trotzdem; die Datenbank liefert sie über ADM.
4. Stempel zeigen wahlweise Eingabe oder Ergebnis, ohne dass einer den anderen überschreibt (beantwortet die ATT-Frage
   „Volumenstrom: Ergebnis oder Vorgabe?“).
5. Für ADM ändert sich nur der Katalogeintrag der Listen T5–T8, T11 (ADM sagt selbst: Umbenennung ändert nur den Katalog).
Ausnahme: ANA-only-Eingaben (Temperaturen, Trennung je Seite, Kreisname) bleiben in ANA. Ein von ANA gewähltes DN
(`Erg_DNGewaehlt`) ist ein Ergebnis und geht nur mit „Übernehmen“ nach `NennweiteAnschluss` – ANA hatte es dort als
„ersetzt“ geführt.

**(b) Bauteilart ↔ ANA-Rolle ↔ Armaturart.**
ADM: `Bauteilart` automatisch aus dem Stil, führend; ANA darf nur verfeinern. ANA: `Bauteilart` als Liste, die der Planer
setzt (aus Kurzzeichen vorbelegt), ersetzt `Rolle`; dazu `Armaturart`. Ein automatisches Feld kann der Planer nicht
überschreiben.
**Vorschlag AMK:** `Bauteilart` = automatisch aus Stil/Stammdaten (ein Schreiber: ASG über die Stammdaten).
`ANA_Hydraulik.Rolle` bleibt ANA-intern mit Vorgabe „Automatisch“ (= aus `Bauteilart`) und wird nur gesetzt, wenn ANA
anders rechnen soll (z. B. „Erzeuger mit eingebauter Pumpe“). `Armaturart` kommt nach `EHS_Bauteil` (Ventilliste T2
liest sie), vorbelegt aus den Stammdaten, geändert nur im ANA-Fenster. Die Wertelisten von `Bauteilart` (ADM 12 Werte,
ANA zusätzlich Weiche, Formstück) werden in den Stammdaten zu einer Liste zusammengeführt.

**(c) Hersteller / Typ / Artikelnummer.**
Heute an drei Orten (`TAGBauteil.Fabrikat/Typ`, `ANA_Armatur.Hersteller` + `Erg_…`). ADM und ANA sind sich im Kern
einig. **Vorschlag AMK:** ein Ort `EHS_Bauteil` (`Hersteller`, `Produktreihe`, `Typ`, `Artikelnummer`, `Bestelltext`).
ANA schreibt seinen Vorschlag weiter in `ANA_Armatur.Erg_…` und überträgt ihn nur auf ausdrücklichen Knopfdruck
„Übernehmen“, nie beim Rechnen. Danach gilt der Wert in `EHS_Bauteil`; ANA warnt, wenn er vom eigenen Vorschlag abweicht.
`ANA_Armatur.Hersteller` als Eingabe entfällt bzw. wird Filter im ANA-Fenster.

**(d) Kennung / KennungHandle – wer vergibt?**
ADM schlägt vor: jedes Modul, das einen `EHS_Bauteil`-Satz anhängt, vergibt sie sofort; ADM prüft beim Lesen und
repariert nur auf Befehl (`-ADMKENNUNG`), nie still. ANA und ATT äußern sich nicht dazu.
**Vorschlag AMK:** so übernehmen. Der Hauptweg ist ASG beim Einfügen eines Symbols; ANA beim Erfassen des Netzes (AMK-Regel
„Sätze beim Erfassen“) und ATT beim Taggen nur, wenn der Satz noch fehlt. Die Vergabe ist eine gemeinsame Bibliotheksregel
(GUID + Handle, gleiche Logik in allen Modulen). Ein Modul, das eine abweichende `KennungHandle` findet, meldet „Kopie“,
ändert aber nichts – die Reparatur macht nur ADM.

**(e) Kennzeichen-Teilfelder.**
ATT schlägt drei Teilfelder vor (Anlage, Kürzel, Nummer) als Spiegel; ADM nimmt nur `Anlage` auf; ANA keines.
**Vorschlag AMK:** `Anlage` und `KennzeichenNummer` ja (Filter und Sortierung in der Datenbank); kein eigenes
Kürzel-Teilfeld, weil `Kuerzel` schon automatisch am Bauteil steht – bei Projektsyntaxen (Roche: Luftart) steht der
Baustein in `EHS_Projekt`. `Kennzeichen` bleibt führend, ATT meldet Abweichungen, überschreibt nichts still. Zusätzlich
offen: ADM ordnet `TAGBauteil.Modul` der `Anlage` zu, ATT führt `Modul` als Zeichnungs-/Projektwert (`EHS_Projekt`) –
beim Umstellbefehl einheitlich lösen (Vorschlag AMK: `Modul` → `EHS_Projekt`).

**(f) Medium.**
ANA führt `Medium` am Erzeuger (leer = aus `Kreise.json`/System), sieht es aber selbst eher beim System bzw. Kreis.
Entscheidungsliste B6: im Hausstandard PWW = Wasser, Antifrogen nur im Projekt.
**Vorschlag AMK:** `Medium` nicht in `EHS_Bauteil`. Es gehört zum System/Kreis (`Kreise.json`, Systemdefinition). Eine
abweichende Projektwahl bleibt als ANA-Eingabe am Erzeuger (`ANA_Hydraulik.Medium`), weil nur ANA damit rechnet.

**(g) Feldname `System`.**
ATT: `System` = voller Name, `System_Kuerzel` = LabelName. ADM: `System` = Kürzel. Gleicher Name, andere Bedeutung.
**Vorschlag AMK:** `System` = Kürzel (alle Regeln und das AKS hängen am Kürzel), voller Name als `SystemBenennung`.

**(h) Raumnummer: automatisch oder von Hand.**
ATT: automatisch aus `PositionsAnker`. ADM: von Hand, wahlweise automatisch. Ein Feld kann nicht beides sein; ohne Räume
ist `PositionsAnker` leer (C5).
**Vorschlag AMK:** `Raumnummer`/`Raumname` in `EHS_Bauteil` als Eingabefeld; ADM füllt sie auf Befehl aus dem Raum
(Füllregel mit Vorschau). `PositionsAnker` bleibt als MEP-Quelle, ATT liest künftig `EHS_Bauteil.Raumnummer`.

**(i) Einheit der elektrischen Leistung.**
ANA: `ElektrischeLeistung` in W; ADM (Kandidat `EHS_MSR`): elektrische Leistung in kW.
**Vorschlag AMK:** ein Feld `ElektrischeLeistung` in `EHS_Bauteil` (nicht zusätzlich in `EHS_MSR`), Einheit einmal im
Katalog festlegen; Empfehlung W wie ANA, weil Pumpen-P1 im Datenblatt so steht – ADM rechnet für Listen um.

**(j) Lüftung, Filter, BMK: zwei Satzvorschläge.**
ATT schlägt `EHS_Filter` und `EHS_BMK` vor, ADM die Kandidaten `EHS_Luft` und `EHS_MSR` mit teils gleichem Inhalt
(Filterklasse, BMK-Zählnummer, Funktion). **Vorschlag AMK:** `EHS_BMK` (ATT-Aufbau) und `EHS_Filter` festlegen; `EHS_Luft`
und `EHS_MSR` erst bauen, wenn Felder übrig bleiben, die keiner der beiden trägt. `Anzahl` steht in `EHS_Bauteil`, nicht
im Filtersatz.

**(k) Kennzeichen: wer schreibt?**
ATT: nur ATT (Hand über die ATT-Palette). ADM: ATT und „Nutzer über ADM“. ANA: Planer bzw. ATT, ADM.
**Vorschlag AMK:** ein Schreiber ATT. ADM zeigt `Kennzeichen` lesend und leitet eine Änderung an ATT weiter; der
Datenbank-Abgleich schlüsselt über `Kennung`, nicht über `Kennzeichen`. ANA streicht `ANA_Hydraulik.Kennzeichen`.

**(l) Umstellung alter Zeichnungen.**
ADM bietet einen Umstellbefehl über die Füllregel an (Kennungen neu), ANA will alte Felder beim ersten Rechnen übernehmen
(nur wenn leer, mit Meldung). **Vorschlag AMK:** **ein** Umstellbefehl (README Ablauf Schritt 6) mit einer Zuordnungsliste
aus Spalte „ersetzt“ dieses Katalogs, Vorschau und einem Rückgängig-Schritt; ANA übernimmt nicht zusätzlich still beim
Rechnen, sondern weist auf den Befehl hin.

## 5 Fragen an den Nutzer

1. **Datenblattwerte und Rechenergebnisse getrennt?** Nennleistung, Volumenstrom, Δp, Anschluss-DN, Wasserinhalt,
   P1 laut Datenblatt kommen in `EHS_Bauteil`, was ANA rechnet, bleibt in ANA. Und: was bedeutete `Druck` (bar) im alten
   Stempel? **Empfehlung:** ja, getrennt; `Druck` erst aufnehmen, wenn die Bedeutung klar ist.
2. **Hersteller/Typ/Artikelnummer an einem Ort?** In `EHS_Bauteil`; ANA schreibt dort nur, wenn Sie im Fenster auf
   „Übernehmen“ drücken. **Empfehlung:** ja.
3. **Bauteilart aus dem Symbolstil führend?** ANA-„Rolle“ nur noch als Ausnahme, Armaturart in `EHS_Bauteil`.
   **Empfehlung:** ja.
4. **Kennzeichen-Teile als eigene Felder?** `Anlage` und laufende Nummer ja, Kürzel steht schon im Feld `Kuerzel`. Dazu
   Hausregel `{Anlage}{Kuerzel}{Nummer}` (z. B. `01VDV01`) als Grundregel bestätigen. **Empfehlung:** ja zu beidem.
5. **Sperre und Ausschluss sichtbar am Bauteil?** `KennzeichenGesperrt` und `Taggen = ausgeschlossen` als Spiegel des
   ATT-Registers, damit ADM und die Datenbank sie sehen. **Empfehlung:** ja.
6. **Kennung und Pflichtfelder:** Die Kennung vergibt das Modul, das den Satz anhängt (meist ASG beim Einfügen), ADM
   repariert nur auf Befehl. Pflicht: `Kennung`, `KennungHandle`, `Kennzeichen`, `Anlage` + automatisch `Kuerzel`,
   `Benennung`, `Bauteilart`, `System`. **Empfehlung:** so bestätigen.
7. **Medium am Bauteil oder am System/Kreis?** **Empfehlung:** am System/Kreis; eine Projektwahl (z. B. Antifrogen) bleibt
   als ANA-Eingabe am Erzeuger.
8. **Begleitsätze:** 4 × `TAGBMK*` → ein `EHS_BMK`? Probe/Entnahme/Beprobung im Kennzeichen aufgehen lassen?
   `TAGRLTFilter` → `EHS_Filter`? `ANA_Leitung` für Leitungen abspalten (berührt ATT-Beschriftungen und Anzeigethemen –
   jetzt, wo Stempel neu entstehen, ist der günstigste Zeitpunkt)? **Empfehlung:** viermal ja.
