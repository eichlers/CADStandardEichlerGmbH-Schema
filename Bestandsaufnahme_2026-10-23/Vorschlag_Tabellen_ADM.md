# Vorschlag Tabellen im Eichler-Hausstandard (EHS) – Sicht ADM

Stand 23.10.2026 · nur Text, nichts gebaut. Grundlage: `Bericht_ADM.md` (Bestand), `hausstandard\README.md`,
`AMK_Konzept.md` Punkt 1/2/8. Feldnamen stammen aus der Inventur der Basis (`adm_lauf\adm_inventur.txt`).

## 1 Grundsatzfrage: AutoCAD-Tabelle oder AEC-Bauteiltabelle?

| | AEC-Bauteiltabelle (ScheduleTable) | AutoCAD-Tabelle, von einem Modul gefüllt |
|---|---|---|
| Zeilen | eine Zeile je Objekt (gleiche Zeilen zusammenfassbar mit „Menge“) | frei: je Objekt, je Kreis, je Netz, Summen, Zwischenüberschriften |
| Auswahl der Objekte | Objektart + „hat Satz X“ + Klassifizierung + Layer bzw. Auswahl. **Kein Filter nach Feldwert** (z. B. `ANA_Hydraulik:Rolle = Pumpe` geht nicht) | jede Regel, z. B. Symbolstil laut Stammdaten, `Rolle`, `ArmaturArt` |
| Werte anderer Objekte | nein, nur Sätze des Objekts selbst | ja (z. B. Kreisname vom Netz, Summen je Strang) |
| Aktualität | AutoCAD aktualisiert selbst (live) | erst nach dem Aktualisierungsbefehl; dafür mit Stand und Hinweis „neu rechnen“ |
| Grafik in der Zelle (Symbol) | nein | ja (Block in der Zelle) |
| Pflege | Stil in der Vorlage, ohne Code | Listendefinition (Datei/Stammdaten) und ein Befehl im Modul |
| Gefahr | ANA hängt `ANA_Hydraulik` an fast alles → „hat Satz“ trennt Bauteilarten nicht | Liste kann veralten → Stand und Warnung in die Kopfzeile |

**Vorschlag:**
- **AutoCAD-Tabellen, von einem Modul gefüllt**, für alle Listen aus Konzeptpunkt 8 (Ventil-, Einstell-, Pumpen-,
  Verbraucher-, Erzeugerliste, Abgleich, Leistungsbilanz …) und für die Legende. Grund: Diese Listen brauchen Filter
  nach Art, Gruppen je Kreis und Summen, und für die Legende Symbolgrafik. Das kann die AEC-Tabelle nicht.
- **AEC-Bauteiltabelle** nur dort, wo eine Zeile je Objekt reicht und die Objektart allein schon trennt: **Raumbuch**
  (Räume). Wahlweise eine schlichte, live mitlaufende **Stückliste „alle Schemasymbole“** (Kennzeichen, Benennung,
  Menge), die ohne Rechnung und ohne Befehl stimmt.
- Spaltenköpfe und Felder beziehen sich auf den **Feldkatalog** (AMK). Die Listendefinition nennt Katalognamen, und das
  Modul setzt sie in `Satz:Feld` um. So muss bei einem neuen Kunden oder Feldnamen nur der Katalog geändert werden.

**Wer füllt die AutoCAD-Tabellen?** Vorschlag: **ADM**. ADM liest heute schon alle Sätze, kennt Filter und Gruppen und hat
den Excel-Export. Konzept 8 sagt: „Export nur über ADM“. Liste und Excel kämen damit aus derselben Definition. ANA löst
nach der Rechnung nur „Listen aktualisieren“ aus (Befehl oder Ereignis), rechnet aber nichts in der Liste selbst.
Alternative: ANA füllt die hydraulischen Listen selbst. Dann gäbe es zwei Tabellenbauer, und der Export bliebe trotzdem
bei ADM. **Entscheidung beim Nutzer.**

## 2 Gemeinsamer Aufbau aller neuen Listen

- **Kopf:** Titel, Anlage/Netz (Filter), **Stand der Rechnung** (`ANA_Hydraulik:Erg_BerechnetAm`, ältester und neuester
  Wert). Ist das Schema seit der Rechnung geändert, steht „**neu rechnen**“ in Rot im Kopf (Frage an ANA: Woran ist eine
  Änderung erkennbar?).
- **Erste Spalte immer das Kennzeichen** `TAGBauteil:PosNr` (Regel: Anlagennummer + Kürzel + lfd. Nr.). Dann
  `TAGBauteil:KurzZeichenSymbol` (automatisch) und die Benennung des Symbolstils (Stammdaten).
- **Ein Ort je Angabe:** Leistung, Volumenstrom, Einstellwerte nur aus den ANA-Sätzen, nie aus TAGBauteil (dort bleiben die
  Altfelder liegen).
- **Leere Ergebnisfelder** bleiben leer (nicht „0“), solange nicht gerechnet ist. Vorgaben sind ohne Rechnung lesbar.
- **Tabellenstil (AutoCAD):** ein EHS-Stil `EHS_Liste` (Titel, Kopf, Daten; Textstil und Höhen nach Hausstandard,
  Layer `Z_Tabellenobjekte` wie heute). Die alten Bauteiltabellenstile werden ersetzt.
- **Einheiten im Spaltenkopf** (kW, m³/h, kPa, K …) aus dem Feldkatalog, Zahlen gerundet nach Katalog.
- **Sortierung:** nach Kennzeichen, bei Kreislisten nach Kreisname und dann nach Kennzeichen.

## 3 Welche Tabellen braucht der Hausstandard?

Felder: TB = `TAGBauteil`, AH = `ANA_Hydraulik`, AA = `ANA_Armatur`, PA = `PositionsAnker`.

| # | Tabelle | Art | Zeilen | Spalten (Feld) | Stand der Felder |
|---|---|---|---|---|---|
| T1 | **Legende** | AutoCAD | je verwendetem Symbolstil | Symbol (Block), Kürzel (TB:KurzZeichenSymbol), Benennung (Stammdaten), optional Anzahl | Stammdaten von ASG; ersetzt die Legendenblöcke `eaklLeg-…` (die tragen heute Sätze, Bericht K3) |
| T2 | **Ventilliste** | AutoCAD | Armaturen (AA vorhanden; Art laut AA:ArmaturArt) | Kennzeichen TB:PosNr · Art AA:ArmaturArt/Unterart · DN AA:Erg_DNGewaehlt (Vorgabe AA:Nennweite) · Leitung AA:Erg_DNLeitung · Übergang AA:Erg_Reduzierung bzw. AH:Erg_Uebergang · kvs AA:Erg_Kvs · Hersteller AA:Erg_HerstellerGewaehlt · Produkt AA:Erg_Produkt · Art.-Nr. AA:Erg_Artikelnummer · Bestelltext AA:Erg_Bestelltext | vorhanden (ANA) |
| T3 | **Einstellliste** (Inbetriebnahme) | AutoCAD | Armaturen mit Einstellung | Kennzeichen · V̇ AH:Erg_Volumenstrom · Δp Ventil AA:Erg_DruckverlustVentil · kv erf. AA:Erg_KvErforderlich · kv ist AA:Erg_KvIst · Voreinstellung AA:Erg_Voreinstellung + AA:Erg_EinheitEinstellung · Autorität AA:Erg_Ventilautoritaet · Bewertung AA:Erg_Bewertung | vorhanden; ANA hat schon eine Inbetriebnahmeliste → Spalten abgleichen |
| T4 | **Hydraulischer Abgleich** | AutoCAD | je Kreis (AH:Kreisname), darunter die Ventile | Kreis · Soll-V̇ · Δp ungünstigster Fließweg AH:Erg_DruckverlustFliessweg · Δp Abgleich AH:Erg_DruckverlustAbgleich · Einstellwert · Förderhöhe AH:Erg_Foerderhoehe · Sockeldruck AH:Erg_Sockeldruck | vorhanden; „ungünstigster Fließweg je Kreis“ muss ANA liefern (ein Feld am Kreis oder an der Pumpe?) |
| T5 | **Pumpenliste** | AutoCAD | Pumpen (Art laut Stammdaten/AH:Rolle) | Kennzeichen · Kreis AH:Kreisname · V̇ AH:Erg_Volumenstrom (gewählt AH:VolumenstromGewaehlt) · H AH:Erg_Foerderhoehe / AH:Erg_FoerderhoeheGewaehlt · Bauart AH:PumpenBauart · Regelung AH:PumpenRegelung · P el AH:Erg_LeistungElektrisch · Medium AH:Erg_Medium · VL/RL AH:Erg_TemperaturVorlauf/-Ruecklauf · im Erzeuger AH:PumpeImErzeuger · Stromkosten AH:Erg_Stromkosten | vorhanden |
| T6 | **Verbraucherliste** | AutoCAD | Verbraucher (AH:Rolle) | Kennzeichen · Art (Symbolstil) · Raum PA:Nummer/Name bzw. TB:Zone · Kreis AH:Kreisname · Leistung AH:Leistung · Spreizung AH:Spreizung · VL/RL AH:TemperaturVorlauf/-Ruecklauf · V̇ AH:Erg_Volumenstrom · Δp AH:DruckverlustBauteil · Anschluss AH:AnschlussDN / AH:Erg_Nennweite | Raum nur mit Räumen (PA); sonst Zone aus TB |
| T7 | **Erzeugerliste** | AutoCAD | Erzeuger (AH:Rolle) | Kennzeichen · Art · Nennleistung AH:Nennleistung · Leistung AH:Erg_Leistung · VL/RL · V̇ · Δp · Pumpe im Erzeuger AH:PumpeImErzeuger | vorhanden |
| T8 | **Systemtrennung / Wärmetauscher** | AutoCAD | Wärmetauscher, hydraulische Weichen | Kennzeichen · Leistung AH:TrennungLeistung · primär VL/RL/V̇/Δp/Medium (AH:TrennungTemperaturPrimaer…, Erg_TrennungVolumenstromPrimaer, TrennungDruckverlustPrimaer, Erg_TrennungMediumPrimaer) · dasselbe sekundär · Abweichung AH:Erg_TrennungAbweichung | vorhanden |
| T9 | **Leistungsbilanz** | AutoCAD | je Netz/Kreis, mit Summe | Kreis · Summe Verbraucher AH:Erg_LeistungGesamt · Gleichzeitigkeit AH:Gleichzeitigkeit · Reserve AH:Leistungsreserve · mit Reserve AH:Erg_LeistungMitReserve · Erzeuger · Bilanz AH:Erg_Leistungsbilanz (Über-/Unterdeckung) | vorhanden; Summen bildet ANA oder die Liste? (siehe Fragen) |
| T10 | **Verteiler** | AutoCAD | je Verteiler, Abgänge darunter | Kennzeichen · DN AH:Erg_VerteilerDN · Ø gewählt/erf. · v AH:Erg_VerteilerGeschwindigkeit · Abgänge mit Kreis, V̇, DN | vorhanden |
| T11 | **Wasserinhalt / Ausdehnung** | AutoCAD | je Netz | Rohre AH:Erg_InhaltRohre · Verbraucher · Erzeuger · Systemtrennung · Speicher · Übrige · Gesamt AH:Erg_InhaltGesamt · Hinweis AH:Erg_InhaltHinweis · Puffer AH:PufferVolumen | vorhanden |
| T12 | **Teilstrecken** | AutoCAD | je Teilstrecke (Schemalinien) | Teilstrecke AH:Erg_Teilstrecke · DN AH:Erg_DNGewaehlt · Länge AH:Erg_Laenge · V̇ · v AH:Erg_Geschwindigkeit · R AH:Erg_Rohrreibung · Δp AH:Erg_Druckverlust · Abmessung AH:Erg_Rohrabmessung | vorhanden; lang → eher nur Excel über ADM |
| T13 | **Raumbuch** | **AEC-Bauteiltabelle** | je Raum | wie bisher `HVACRaumBuch` (HVACRaum: Geschoss, Zone, Nummer, Name, Fläche, Höhe, Volumen, Zu-/Ab-/Umluft …), neu gestaltet | nur, wenn Räume im Hausstandard bleiben (Bericht, Entscheidung 6) |
| T14 | **Stückliste allgemein** (optional) | **AEC-Bauteiltabelle** | je Schemasymbol, gleiche zusammengefasst | Menge · Kennzeichen TB:PosNr · Kürzel TB:KurzZeichenSymbol · Benennung (Symbolstil) | live, ohne Rechnung |
| T15 | **RLT-Listen** (Filter, Messstutzen, Luftdurchlässe) | offen | – | heute aus `TAGRLTFilter` und `PositionsAnker`; ANA rechnet Luft nicht | **offen**: Vorgaben für Bauteile, die ANA nicht rechnet, haben noch keinen Satz (Konzept 2 „später“). Nach Konzept-Regel keine Bindung an Altsätze → erst Satzfrage klären |
| T16 | **MSR/BMK-Liste** und **Elektrodaten** | offen | – | heute `TAGBMK…:ZaehlNr/Funktion`, `EDaten` | **offen**: Altsätze; ATT-Zuständigkeit (Kennzeichnung) klären |

Die alten Stile `StücklisteArmaturen`, `StücklistePumpen`, `StücklisteKühlerErhitzer`, `StücklisteRegelVentile`,
`Stückliste hydraulische Volumenstromregler`, `StücklisteULK`, `LeistungsBilanz` und `Legende` gehen in T2 bis T9 bzw. T1
auf. `MessStutzen`, `RLTMessStutzen` und `RLTFilterliste` gehen in T15 auf, `StücklisteMSRBMK` in T16, `HVACRaumBuch`
in T13.

## 4 Was ADM dafür bauen würde (später, erst auf Ansage)

1. **Listendefinition** je Tabelle (Datei in den EHS-Stammdaten): Titel, Auswahlregel, Gruppierung, Spalten mit
   Feldkatalog-Namen, Einheit, Rundung, Summenzeilen.
2. **Befehl `ADMLISTE`** (und `-ADMLISTE` für Skripte): Liste einfügen bzw. alle Listen der Zeichnung aktualisieren.
   Eigenschaften zum Wiederfinden: XData `ADM_LISTE` mit dem Listennamen an der Tabelle. Ein Rückgängig-Schritt, Layer
   `Z_Tabellenobjekte`, Tabellenstil `EHS_Liste`.
3. **Gleiche Definition für Excel:** „Export ▾ → Liste …“ schreibt dieselben Spalten. Ein Import zurück geht wie heute
   nur über die Felder, nicht über die Tabelle.
4. In der ADM-Palette eine Ansicht je Liste (gespeicherter Filter mit Spalten), damit man vor dem Einfügen prüfen kann.

## 5 Offene Fragen

- **An den Nutzer:** Wer füllt die Listen, ADM (Vorschlag) oder ANA (nur die hydraulischen)? · Raumbuch und Räume ja/nein?
  · T14 „Stückliste allgemein“ gewünscht? · Welche Listen zuerst? (Vorschlag: T2 Ventil, T3 Einstell, T5 Pumpen, T1
  Legende.)
- **An ANA:**
  - Woran erkennt man „Schema seit der Rechnung geändert“?
  - Liefert ANA je Kreis ein Feld für den ungünstigsten Fließweg und die Summen (T4, T9), oder rechnet die Liste das selbst?
  - Ist `AH:Rolle` der verlässliche Unterscheider (Pumpe, Verbraucher, Erzeuger, Trennung, Verteiler)?
  - Welche Spalten hat die vorhandene Inbetriebnahmeliste (T3)?
- **An ASG:** Benennung und Symbolblock je Stil für die Legende (T1) aus den Stammdaten?
- **An ATT:** Welche Kennzeichenfelder bleiben in `TAGBauteil` in Gebrauch (PosNr, Zone, Modul, BezeichnungFreitext)? Gibt
  es einen Satz für RLT-, MSR- und Elektroangaben (T15, T16)?
- **An AMK:** Feldkatalog-Namen für alle oben genannten Felder (Einheit, Rundung). Die Listen beziehen sich nur auf ihn.
