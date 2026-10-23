# Felder für EHS_Bauteil, EHS_Projekt und die Datenbank-Anbindung – Sicht ADM

Stand 23.10.2026 · nur Text, nichts gebaut. Grundlage: `Vorschlag_Tabellen_ADM.md` (T1–T16), `Bericht_ADM.md`
und die Erfahrung mit dem heutigen ADM-Abgleich (Export/Import mit Export-Nr., Handle und Zeichnungskennung).

## 0 Regeln für Feldnamen (aus Sicht ADM, Excel und XML)

- **Nur Buchstaben und Ziffern, ohne Umlaute, ohne Punkt, ohne Leerzeichen, nicht mit einer Ziffer beginnend**
  (`Kennzeichen`, `Raumnummer`). Der ADM-XML-Export bildet Elementnamen `Satz.Feld`. `TAGBauteil:SystemAbkz.` (Punkt)
  und Umlaute haben dort schon Ärger gemacht. Den Anzeigenamen mit Umlaut und Einheit liefert der Feldkatalog.
- **Einheit nie im Feldnamen**, sondern im Katalog. Zahlen als Real oder Integer, nicht als Text. ADM prüft beim Import
  den Typ: „12,5 kW“ in einem Real-Feld ist ein Fehler, „12,5“ nicht.
- **Ein Ort je Angabe.** Ergebnisse von ANA bleiben in den ANA-Sätzen. `EHS_Bauteil` trägt, was das Bauteil *ist* und
  *wo* es ist, dazu die Kennung für die Datenbank.
- **Listenfelder** (Auswahl) nur, wo die Werte fest sind (Bauteilart, Status). Die Werteliste steht in den Stammdaten,
  ADM öffnet sie schon heute als Auswahlliste.

## 1 EHS_Bauteil – Felder am Bauteil

Legende: **S** = schreibt, **L** = liest. Kennung = Datenbank-Anbindung (Abschnitt 3).

| Feld (Vorschlag) | Bedeutung | Typ / Einheit | S | L | Pflicht | ersetzt heute |
|---|---|---|---|---|---|---|
| `Kennung` | dauerhafte, weltweit eindeutige Kennung des Bauteils | Text (GUID, 36 Zeichen), nur lesen | jedes Modul beim ersten Anlegen, ADM beim Prüfen | ADM (Datenbank, Excel/XML), alle Listen intern | **ja** | – (heute Handle + Zeichnungskennung + Export-Nr.) |
| `KennungHandle` | Handle, für den die Kennung vergeben wurde. Ist es ein anderes, ist das Objekt eine Kopie (Abschnitt 3) | Text, nur lesen | wie `Kennung` | ADM, alle Module beim Prüfen | **ja** | – |
| `Kennzeichen` | Anlagenkennzeichen nach Hausregel (Anlagennr. + Kürzel + lfd. Nr., z. B. `01VDV01`) | Text | ATT (Tagging), Nutzer über ADM | alle Listen (erste Spalte), Stempel, ADM-Redundanzprüfung (eindeutig) | **ja** (für Listen) | `TAGBauteil:PosNr` |
| `Anlage` | Anlagennummer bzw. Netz, Teil des Kennzeichens | Text | ATT | Listen (Filter, Kopf), ATT-Kennzeichenregel | ja | Anteil von `PosNr`, `TAGBauteil:Modul` |
| `Kuerzel` | Bauteilkürzel (VDV, PU …) | Text, **automatisch aus dem Symbolstil** | ASG (am Stil) | Legende T1, Listen, Stempel, ATT | ja (automatisch) | `TAGBauteil:KurzZeichenSymbol`, `StilSchemaSymbol:KurzZeichenSymbol` |
| `Benennung` | Benennung des Bauteils laut Stammdaten | Text, **automatisch aus dem Symbolstil** | ASG (am Stil) | Legende T1, alle Listen (Spalte „Bauteil“) | ja (automatisch) | `StilSchemaSymbol:Stil` |
| `Bauteilart` | Gruppe für die Listen: Armatur, Pumpe, Verbraucher, Erzeuger, Systemtrennung, Verteiler, Speicher, Luftdurchlass, Filter, Messstelle, Sensor, Sonstiges | Liste, **automatisch aus dem Symbolstil** | ASG (Stammdaten) | **Auswahlregel aller Listen T2–T16**, ANA (statt `Rolle`?) | ja (automatisch) | – (heute nur über Stilname oder `ANA_Hydraulik:Rolle`) |
| `System` | Systemkürzel (= LabelName der Systemdefinition = AKS) | Text, **automatisch aus der Leitung/dem System** | AutoCAD (automatisch) | Listen, Stempel, Filter | ja (automatisch) | `TAGBauteil:System`, `TAGBauteil:SystemAbkz.` |
| `Bezeichnung` | Freitext zum Bauteil („Heizregister RLT 3“) | Text | Nutzer (ADM, ATT) | Listen (Verbraucher, Erzeuger), Stempel | nein | `TAGBauteil:BezeichnungFreitext` |
| `Gebaeude` | Gebäude | Text | Nutzer/ATT, ADM (Füllen) | Listen, Filter | nein | – |
| `Geschoss` | Geschoss | Text | Nutzer/ATT, ADM | Listen, Filter, Raumbuch | nein | `PositionsAnker:Geschoss` (nur mit Räumen) |
| `Zone` | Zone bzw. Bereich | Text | Nutzer/ATT, ADM | Listen (T2, T5, T6), Filter | nein | `TAGBauteil:Zone` |
| `Raumnummer` | Raum, in dem das Bauteil wirkt | Text | Nutzer/ATT, ADM; wahlweise automatisch aus einem Raum | Verbraucherliste T6, RLT-Listen T15 | nein | `PositionsAnker:Nummer` |
| `Raumname` | Name dieses Raums | Text | wie oben | wie oben | nein | `PositionsAnker:Name` |
| `Hersteller` | festgelegter Hersteller | Text | Nutzer über ADM; ANA nur beim Übernehmen seines Vorschlags | Listen T2, T5, T7, Stempel | nein | `TAGBauteil:Fabrikat`, (Vorschlag: `ANA_Armatur:Erg_HerstellerGewaehlt`) |
| `Typ` | festgelegter Typ bzw. Produkt | Text | wie `Hersteller` | wie oben | nein | `TAGBauteil:Typ`, (`ANA_Armatur:Erg_Produkt`) |
| `Artikelnummer` | Artikelnummer des festgelegten Produkts | Text | wie `Hersteller` | Ventilliste T2, Excel | nein | (`ANA_Armatur:Erg_Artikelnummer`) |
| `Status` | Planungsstand: neu, Bestand, Rückbau, entfällt | Liste | Nutzer über ADM | alle Listen (Filter, Kennzeichnung), Datenbank | nein (Vorgabe „neu“) | – (heute keins) |
| `Anzahl` | Stückzahl, wenn ein Symbol mehrere gleiche Bauteile vertritt | Integer, Vorgabe 1 | Nutzer | Listen (Menge), Stückliste T14 | nein | `TAGRLTFilter:Anzahl` |
| `Bemerkung` | Bemerkung | Text | Nutzer | Listen (letzte Spalte) | nein | `TAGBauteil:Bemerkung` |

**Bewusst nicht in EHS_Bauteil** (ein Ort je Angabe):
- Leistung, Volumenstrom, Δp, Temperaturen, Einstellwerte, DN, kvs, Kreisname → **ANA-Sätze** (Vorgaben und
  Ergebnisse). Die Listen lesen sie dort, siehe Abschnitt 2.
- Projektwünsche → `EHS_Projekt` (Abschnitt 4).
- Kennung der Zeichnung und Synchronisationsstand der ganzen Zeichnung → **Zeichnungsebene** (Abschnitt 3), nicht am
  Bauteil.

**Zu entscheiden:**
- **Hersteller, Typ, Artikelnummer:** Ein Ort in `EHS_Bauteil` (festgelegt). ANA schreibt seinen Vorschlag weiter in
  `Erg_…` und übernimmt ihn nur auf Knopfdruck nach `EHS_Bauteil`. Sonst hätten Ventile (ANA) und Pumpen (Nutzer) zwei
  verschiedene Orte.
- **`Bauteilart` statt `ANA_Hydraulik:Rolle`:** Zwei Felder mit gleicher Bedeutung sind zwei Orte. Vorschlag:
  `Bauteilart` aus dem Stil ist führend. ANA übernimmt sie oder verfeinert sie nur, z. B. „Erzeuger mit eingebauter Pumpe“.

## 2 Felder, die die Listen aus den ANA-Sätzen lesen (Schreiber: ANA)

Diese Felder bleiben, wo sie sind. Sie müssen aber in den Katalog, weil Listen und Stempel sich auf ihn beziehen. Die
Namen sind von heute. Benennt ANA sie um, ändert sich nur der Katalogeintrag.

| Liste | Felder aus `ANA_Hydraulik` (AH) und `ANA_Armatur` (AA) |
|---|---|
| T2 Ventile | AA: ArmaturArt, Unterart, Nennweite, Erg_DNGewaehlt, Erg_DNLeitung, Erg_Reduzierung, Erg_Kvs, Erg_Bestelltext; AH: Erg_Uebergang |
| T3 Einstellung | AH: Erg_Volumenstrom; AA: Erg_DruckverlustVentil, Erg_KvErforderlich, Erg_KvIst, Erg_Voreinstellung, Erg_EinheitEinstellung, Erg_Ventilautoritaet, Erg_Bewertung |
| T4 Abgleich | AH: Kreisname, Erg_Volumenstrom, Erg_DruckverlustFliessweg, Erg_DruckverlustAbgleich, Erg_Foerderhoehe, Erg_Sockeldruck |
| T5 Pumpen | AH: Kreisname, Erg_Volumenstrom, VolumenstromGewaehlt, Erg_Foerderhoehe, Erg_FoerderhoeheGewaehlt, PumpenBauart, PumpenRegelung, Erg_LeistungElektrisch, Erg_Medium, Erg_TemperaturVorlauf, Erg_TemperaturRuecklauf, PumpeImErzeuger, Erg_Stromkosten |
| T6 Verbraucher | AH: Kreisname, Leistung, Spreizung, TemperaturVorlauf, TemperaturRuecklauf, Erg_Volumenstrom, DruckverlustBauteil, AnschlussDN, Erg_Nennweite |
| T7 Erzeuger | AH: Nennleistung, Erg_Leistung, Erg_TemperaturVorlauf/-Ruecklauf, Erg_Volumenstrom, DruckverlustBauteil, PumpeImErzeuger |
| T8 Systemtrennung | AH: TrennungLeistung, TrennungTemperatur…, TrennungDruckverlust…, Erg_Trennung… (primär/sekundär), Erg_TrennungAbweichung |
| T9 Leistungsbilanz | AH: Kreisname, Erg_LeistungGesamt, Gleichzeitigkeit, Leistungsreserve, Erg_LeistungMitReserve, Erg_Leistungsbilanz |
| T10 Verteiler | AH: Erg_VerteilerDN, VerteilerDurchmesserGewaehlt, Erg_VerteilerDurchmesserErf, Erg_VerteilerGeschwindigkeit |
| T11 Wasserinhalt | AH: Erg_InhaltRohre, Erg_InhaltVerbraucher, Erg_InhaltErzeuger, Erg_InhaltSystemtrennung, Erg_InhaltSpeicher, Erg_InhaltUebrige, Erg_InhaltGesamt, Erg_InhaltHinweis, PufferVolumen |
| T12 Teilstrecken | AH an Leitungen: Erg_Teilstrecke, Erg_DNGewaehlt, Erg_Laenge, Erg_Volumenstrom, Erg_Geschwindigkeit, Erg_Rohrreibung, Erg_Druckverlust, Erg_Rohrabmessung |
| alle | AH: **Erg_BerechnetAm** (Stand im Listenkopf) |

**T13 Raumbuch:** Falls Räume bleiben, gehört das in einen eigenen Raumsatz `EHS_Raum` (Nummer, Name, Geschoss, Fläche,
Höhe, Volumen als Formel, Zu-/Ab-/Umluft, Temperatur, Feuchte, Druckstufe, Reinraumklasse) und nicht in `EHS_Bauteil`.
Ersetzt `HVACRaum`.
**T15/T16 (Lüftung, MSR, Elektro):** Diese Bauteile rechnet ANA nicht. Kandidaten für einen späteren Satz (zum Beispiel
`EHS_Luft` und `EHS_MSR`), noch nicht festlegen: Luftvolumenstrom (m³/h), Filterklasse (Liste), Abmessung L×B×H (mm),
Messstellennummer, BMK-Zählnummer, Funktion, elektrische Leistung (kW), Spannung (V). Sie ersetzen `TAGRLTFilter`,
`TAGBMK…` und `EDaten`.

## 3 Datenbank-Anbindung

### Was sie braucht

| Was | wo | Zweck |
|---|---|---|
| **Kennung des Bauteils** (GUID) | `EHS_Bauteil:Kennung` | Schlüssel in der Datenbank, über Zeichnungen und Kopien hinweg |
| **Kopierschutz** | `EHS_Bauteil:KennungHandle` | COPY, Spiegeln, Kopieren über die Zwischenablage und Blockeinfügen kopieren den Satz mit, also auch die Kennung. Stimmt `KennungHandle` nicht mit dem Handle des Objekts überein, ist es eine Kopie: neue Kennung vergeben, die alte als Herkunft melden. Gilt auch beim Einfügen in eine andere Zeichnung. Dort kann der Handle zufällig gleich sein, deshalb zusätzlich die Zeichnungskennung prüfen (nächste Zeile) |
| **Kennung der Zeichnung** | Wörterbuch der Zeichnung (`EHS_Zeichnung`: ZeichnungsKennung als GUID, Projekt) | `Database.FingerprintGuid` reicht nicht, denn eine **Dateikopie** (Explorer, SaveAs) behält ihn. Eine eigene Zeichnungskennung mit dem gespeicherten Dateipfad erkennt eine kopierte Zeichnung (Pfad anders): nachfragen, ob Kopie oder Umzug |
| **Änderungsstand** | **kein Feld am Bauteil**, sondern eine Prüfsumme der Werte in der Datenbank | Ein Feld „GeaendertAm“ am Bauteil stimmt nicht, wenn jemand in der Eigenschaftenpalette tippt, ohne dass ein Modul läuft. Sicher ist: Die Datenbank speichert beim Abgleich je Kennung die Werte (oder eine Prüfsumme). Beim nächsten Abgleich ist jede Abweichung in der Zeichnung eine Änderung, in der Datenbank ebenso, und beides zugleich ein Konflikt. **Das macht ADM heute schon so** (Exportstand in der Begleitdatei, Import zeigt orange, Konflikte rot) |
| **Löschen** | keine Löschmarke am Bauteil | Wird ein Objekt gelöscht, ist auch sein Satz weg, eine Marke daran ginge verloren. Gelöscht heißt: Kennung in der Datenbank, aber nicht mehr in der Zeichnung (bei vollständigem Lesen derselben Zeichnungskennung). Für „bleibt gezeichnet, entfällt aber“ dient `Status = entfällt` |
| **Stand der Zeichnung** | Wörterbuch der Zeichnung: Nummer und Zeit des letzten Abgleichs | Listenkopf, Bericht, Erkennen „Zeichnung seit Abgleich geändert“. ADM führt heute schon eine Revisionsnummer in `ADM_EICHLER/Revision` |
| **Zugriff** | Datenbank außerhalb der Zeichnung (Datei/Server), nie in der DWG | Mehrere Zeichnungen und Mehrbenutzer, Excel-Formulare, Auswertungen |

### Wie ADM damit umginge

1. **Kennung prüfen beim Einlesen** (ohne zu schreiben): fehlt, doppelt bzw. kopiert (Handle passt nicht), fremde
   Zeichnung. Anzeige in der Tabelle mit eigener Farbe. Die Spalten `Kennung` und `KennungHandle` sind nur lesbar.
2. **Kennungen vergeben bzw. reparieren** nur auf Befehl (Rechtsklick ▸ Daten → „Kennungen vergeben“, `-ADMKENNUNG` für
   Skripte), ein Rückgängig-Schritt, mit Eintrag im Änderungsprotokoll („Kopie von …“). Nie still im Hintergrund, denn
   das wäre eine Zeichnungsänderung beim bloßen Ansehen.
3. **Export, Import und Datenbank-Abgleich mit der Kennung als Schlüssel** statt Handle + Export-Nr. Alles andere bleibt
   wie heute: Vorschau farbig, annehmen oder ablehnen je Zelle, ein Rückgängig-Schritt, Revisionswolken. Neu: „in der
   Datenbank, aber nicht in der Zeichnung“ = gelöscht (Zeile grau mit Grund, Rechtsklick „in DB als gelöscht
   bestätigen“), „in der Zeichnung, nicht in der DB“ = neu.
4. **Projektansicht über mehrere Zeichnungen** (heute `ADMPROJEKT`) mit der Kennung: findet dasselbe Bauteil, auch wenn
   es in eine andere Zeichnung verschoben wurde (gleiche Kennung, andere Zeichnungskennung = Umzug).
5. **Redundanzprüfung** auf `Kennzeichen` (fachlich eindeutig) und zusätzlich auf `Kennung` (technisch eindeutig;
   doppelt = Kopie, die noch nicht geprüft ist).
6. **Alte Zeichnungen:** Zuordnung `TAGBauteil:*` → `EHS_Bauteil:*` als Umstellbefehl (AMK-Ablauf Schritt 6). ADM kann
   dafür die Füllregel (`{Satz:Feld}`) nutzen, mit Vorschau und einem Rückgängig-Schritt. Kennungen werden dabei neu
   vergeben.

## 4 EHS_Projekt – was ADM braucht

- Felder mit **sprechenden Namen aus dem Projektprofil**, für ADM gewöhnliche Spalten. ADM braucht nur feste Namen je
  Projekt (Filter, Exporte und Formulare hängen daran) und Typen (Text, Real, Integer, Liste).
- Das **Projektprofil** sollte je Feld die Werteliste mitbringen, dann öffnet ADM sie als Auswahlliste.
- Optional: Eines der Felder kann im Profil als „eindeutig“ markiert werden. ADM übernimmt es als Redundanzkriterium
  (statt heute in den ADM-Einstellungen von Hand).
- `EHS_Projekt` nur an Objekten, die es brauchen (optional, wie gesagt). Eine Kennung bekommt es nicht, es hängt
  über `EHS_Bauteil:Kennung` am Bauteil.

## 5 Fragen für den Katalog

1. Pflichtfelder bestätigen: `Kennung`, `KennungHandle`, `Kennzeichen`, `Anlage`, dazu die automatischen `Kuerzel`,
   `Benennung`, `Bauteilart`, `System`.
2. Stilbasierte Felder (`Kuerzel`, `Benennung`, `Bauteilart`): als automatisches Feld in `EHS_Bauteil`, das aus einem
   Stilsatz (`EHS_Stil`) kommt, oder direkt im Stilsatz? Für ADM gleich, für Stempel und Listen ist ein Ort am Bauteil
   einfacher.
3. Hersteller, Typ, Artikelnummer: festgelegt in `EHS_Bauteil` und ANA nur als Vorschlag (siehe 1)?
4. `Bauteilart` führend statt `ANA_Hydraulik:Rolle`?
5. Wer vergibt die Kennung beim Neuzeichnen: ASG (Symbol einfügen), ATT (Tagging) oder ADM (Prüfen)? Vorschlag: jedes
   Modul, das einen EHS_Bauteil-Satz anhängt, vergibt sie sofort. ADM repariert nur.
