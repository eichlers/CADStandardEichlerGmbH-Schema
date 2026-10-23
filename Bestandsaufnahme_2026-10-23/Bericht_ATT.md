# Bestandsaufnahme ATT – Eichler-Hausstandard auf Basis RI 9.1

Stand 23.10.2026. Nur gelesen, nichts geändert.

- **Gelesen aus:** einer Kopie von `C:\Temp\AMK_Vorlage\Basis_ANA_Test_2_RI_9.1_20261023.dwg` (`C:\Temp\AMK_Vorlage\ATT_Lauf\v.dwg`). Lauf headless in accoreconsole, `_QUIT _Y`, die Kopie wurde nicht gespeichert.
- **Werkzeuge:**
    - Lesebefehl `ATTBESTAND` (`C:\Temp\ATTHeadless\Konsole\Bestand.cs`), Rohdaten in `ATT_Lauf\bestand.tsv`.
    - `ATTSTAMM` von ATT 0.15.9: Systeme und Symbolstile, Datei `Documents\ATT\Stammdaten\v_ATT_Stamm.json`.
- **Abgeglichen mit:**
    - AKS-Konfigurator v3.1, Tabs Medien, Layer und Symbolübersicht.
    - ATT-Listen (eingebettet, Stand 19.10.).
    - ASG-Auslesung der Themenfarben `C:\Temp\ASG_Systemfarben_Vorlage_RI_9.1.csv`.

## 1. Was ATT in der Vorlage nutzt oder erzeugt

### Beschriftungsstempel (Mehransichtsblöcke, AEC)

- Die Vorlage hat **48 Mehransichtsblöcke `TAG*`**.
- In dieser Zeichnung gesetzt sind nur zwei:
    - `TAGBauteilPosNr_01_01`, 618-mal. Das ist der TAG-Stempel.
    - `TAGDaemmung_01_02`, einmal.
- Alle anderen sind vorbereitet und haben 0 Einsätze.
- Jeder Stempel zeigt Attribute mit der Kennung `SATZ:FELD`, zum Beispiel `TAGBAUTEIL:POSNR`. Darüber liest ATT, welcher Stempel welches Feld zeigt.

| Gruppe | Mehransichtsblöcke | Felder (Attributkennungen) | ATT |
|---|---|---|---|
| Bauteil | `TAGBauteilPosNr_01_01/_01_02`, `…Groesse_01_01/_02`, `…DurchFluss`, `…Druck`, `…EinStellWert`, `…Fabrikat`, `…Typ`, `…Bemerkung`, `…Leistung`, `…Modul`, `…Zone`, `…RegelVentil_01_01/_02_01`, `…RegelAbgleichVentil`, `TAGBauteil_01_01`, `TAGBauteil3Zeilig`, `TAGBauteil4Zeilig` | `TAGBAUTEIL:*` | setzt, prüft und richtet aus. TAG-Stempel = `TAGBauteilPosNr_01_01`; „verwaltet“ laut Projektprofil: Durchfluss, FilterRLTDurchFluss, FilterRLT_01_05, Zone |
| RLT-Filter | `TAGFilterRLT_01_01 … _01_11` (ohne _07), `TAGFilterRLTDurchFluss_01_01` | `TAGRLTFILTER:XTAGZEILE01…10`, `:DURCHFLUSS` | setzt und prüft |
| BMK | `TAGBMKFremd`, `TAGBMKGebauede`, `TAGBMKMonitoring`, `TAGBMKProzess_01_01…03` | `TAGBMK*:ZAEHLNR`, `:FUNKTION` | prüft nur auf Doppelungen (MSR-Kennzeichen kommen als Zuarbeit) |
| Raum | `TAGHVACRaum_01_01…03`, `_05_01`, `_06_01`, `_07_01` | `HVACRAUM:*` | liest den Raum (Nummer) |
| Probe/Entnahme | `TAGProbeNahme`, `TAGEntNahme`, `TAGBeprobungspunktTrinkwasser` | `…:POSNR` | wie TAG (eigene Sätze) |
| Leitung/Dämmung | `TAGRohrleitung_02_01`, `TAGDaemmung_01_01/_02` | `TAGSTRÖMUNG:*`, `TAGDAEMMUNG:*`, `StilSchemaRohrKanal:*` | nicht genutzt |

Dazu gibt es **gleichnamige einfache Blöcke** `TAG*_01_01` (48 Stück). Das sind die Ansichtsblöcke der Mehransichtsblöcke.

**Widersprüche bei den Stempeln:**

- **Namen** – der Ansichtsblock heißt anders als der Mehransichtsblock:
    - Block `TAGProzessBMK_01_01` ↔ Mehransichtsblock `TAGBMKProzess_01_01`.
    - Ebenso `TAGGebauedeBMK` ↔ `TAGBMKGebauede`, `TAGMonitoringBMK` ↔ `TAGBMKMonitoring`, `TAGFremdBMK` ↔ `TAGBMKFremd`.
    - Ebenso `TAGBeprobungTrinkwasser` ↔ `TAGBeprobungspunktTrinkwasser`.
- **Felder ohne Satzfeld:** `TAGBauteil_01_01` zeigt `TAGBAUTEIL:BESCHRIFTUNG05…09`, der Satz TAGBauteil hat aber nur `Beschriftung01…04`. Diese Zeilen bleiben immer leer.
- **Schreibweise:** Einige Kennungen sind gemischt geschrieben (`TAGBAUTEIL:Fabrikat`, `:Typ`, `:EinStellWert`, `HVACRAUM:Höhe`). Das funktioniert, weil Groß-/Kleinschreibung egal ist, ist aber uneinheitlich.

### Stempel-Layer, Text- und Führungsstile

- **Stempel-Layer:** ATT legt neue Stempel auf den Layer des Vorbilds bzw. des Stempelsatzes. In der Vorlage ist das **`Z_Symbol-Beschriftungen`** mit 631 Objekten. ATT legt **keine eigenen Layer** an.
- **Textstile (12):**
    - Standard, Arch-Dim, RomanS, Schedule-Header, Annotative, Arial, ISO, SIMPLEX.
    - Mit Roche-Namen: `Roche_SchemaLinie_085` (Arial 85), `Roche_SchemaLegende_1` (Arial 100), `Roche_Vector_c` (simplex, 0,7), `Roche` (ROCHL__.TTF).
    - ATT schreibt keinen Textstil. Die Stempel bringen ihren Stil im Block mit.
- **Multiführungsstile:** nur `Standard` (RomanS, Höhe 4). ATT nutzt keine Multiführungen.

### Was ATT sonst in die Zeichnung schreibt

- Werte in Eigenschaftssätzen, vor allem `TAGBauteil:PosNr`, nur nach Vorschau und Rückfrage.
- Das Register als Xrecord **`ATT_REGISTER`** im Wörterbuch der Zeichnung (Sperren, Ausschlüsse, Anlagen).
- Für Baugruppen den RegApp **`ATT_BAUGRUPPE_FREMD`** (XData) und Schemalinien auf vorhandenen Layern.
- Neue Layer, Blöcke oder Stile legt ATT nicht an.

## 2. Eigenschaftssatz-Definitionen der Zeichnung (25)

„Objekte“ und „Stile“ zählen, an wie vielen Objekten bzw. Stilen der Satz hängt. Gezählt ist über alle Objekte der Zeichnung.

| Satz | Felder | Objekte | Stile | gilt für | Herkunft | Befund |
|---|---|---|---|---|---|---|
| **TAGBauteil** | 49 | 644 | – | Schemasymbol | Vorlage (RI 9.1); **ATT schreibt PosNr** | bleibt unverändert (Regel). Beschriftung01–04, aber Stempel bis 09 (s. o.) |
| TAGRLTFilter | 36 | 3 | – | Schemasymbol | Vorlage; ATT setzt Stempel | – |
| TAGBMKGebauede | 3 | 7 | – | Schemasymbol | Vorlage; ATT prüft | **gleich aufgebaut** wie TAGBMKFremd/Monitoring/Prozess |
| TAGBMKMonitoring | 3 | 1 | – | Schemasymbol | Vorlage; ATT prüft | dto. |
| TAGBMKFremd | 3 | 0 | – | Schemasymbol | Vorlage | dto., **ungenutzt** |
| TAGBMKProzess | 3 | 0 | – | Schemasymbol | Vorlage | dto., **ungenutzt** |
| TAGProbeNahme | 2 | 0 | – | Schemasymbol | Vorlage | **gleich aufgebaut** wie TAGEntNahme und BeprobungspunktTrinkwasser (PosNr, Auswertung), ungenutzt |
| TAGEntNahme | 2 | 0 | – | Schemasymbol | Vorlage | dto., ungenutzt |
| BeprobungspunktTrinkwasser | 2 | 0 | – | Schemasymbol | Vorlage | dto., ungenutzt; Name passt nicht ins TAG*-Schema |
| TAGMessStutzen | 2 | 0 | – | Schemasymbol | Vorlage | ungenutzt |
| PositionsAnker | 4 | 5 | – | Schemasymbol | Vorlage; **ATT liest Raum** (`PositionsAnker:Nummer`) | Felder überschneiden sich mit HVACRaum (Name, Nummer, Geschoss) |
| HVACRaum | 29 | 0 | – | Raum (AecDbSpace) | Vorlage; ATT liest `HVACRaum:Nummer` | in dieser Zeichnung keine Räume |
| EDaten | 5 | 1 | – | Schemasymbol | Vorlage | – |
| TAGDaemmung | 6 | 2 | – | Schemaleitung | Vorlage | – |
| TAGMedium | 8 | 0 | – | Schemaleitung | Vorlage | ungenutzt |
| TAGStrömung | 8 | 0 | – | Schemaleitung | Vorlage | ungenutzt (nur im Stempel TAGRohrleitung) |
| StilSchemaSymbol | 4 | – | 403 | Symbolstil | Vorlage; **ATT liest KurzZeichenSymbol** | stilbasiert |
| StilSchemaRohrKanal | 4 | – | 29 | Schemaleitungsstil | Vorlage | stilbasiert |
| **ANA_Hydraulik** | 127 | 2 600 | – | Schema, Symbol, Block | **ANA** | – |
| **ANA_Armatur** | 43 | 372 | – | Schema, Symbol, Block | **ANA** | – |
| SpaceEngineeringClassifications | 8 | 245 | – | Klassifizierung | MEP-Standard | hängt an Klassifizierungen, nicht an Bauteilen |
| SpaceEngineeringObjects | 17 | 0 | – | Raum | MEP-Standard | ungenutzt; überschneidet sich mit HVACRaum |
| ZoneEngineeringObjects | 2 | 0 | – | Zone | MEP-Standard | ungenutzt |
| ThermalProperties | 2 | 0 | 0 | Wand-/Fenster-/Türstile | MEP-Standard | ungenutzt |
| AecPolygonStil | 6 | 0 | 0 | Polygonstil | MEP-Standard | ungenutzt |

- **ADM und ASG** haben in dieser Zeichnung keine eigenen Sätze. Von ADM stammt nur der Layer `ADM_Marke`.
- **Ungenutzt:** 12 Sätze hängen weder an Objekten noch an Stilen (oben markiert).
- **Echte Dubletten** (gleicher Aufbau):
    - die 4 TAGBMK*-Sätze;
    - die 3 Sätze mit PosNr/Auswertung (TAGProbeNahme, TAGEntNahme, BeprobungspunktTrinkwasser);
    - teilweise HVACRaum ↔ SpaceEngineeringObjects ↔ PositionsAnker.

## 3. Kürzel-Abgleich

Vier Quellen: AKS (Tab Medien, Spalte „Leitungssysteme“, und Tab Layer, „Name (Kürzel)“), die Systemdefinitionen der Vorlage (LabelName, 99), die ATT-Liste `medien` (109 Schlüssel) und die Symbolstil-Kürzel.

### Systeme, deren Kürzel sich unterscheidet (Name und Farbe gleich)

| AKS (Medien/Layer) | Vorlage (LabelName) | ATT-Liste |
|---|---|---|
| KW-S-VL / KW-S-RL | **KW-VL-S / KW-RL-S** | beide Schreibweisen |
| D-8 / KD-8 | **D-8.0 / KD-8.0** | beide Schreibweisen |
| TOE-VL / TOE-RL | **TOEVL / TOERL** | beide Schreibweisen |
| BEENTLÜ (Medien) / BEENTLUE (Layer) | BEENTLUE | BEENTLÜ und BEENTLUE |
| WL-FREMD, WL-GEB, WL-MON, WL-PRO, WL-TWB (Layer) | **WLFBMK, WLGBMK, WLMBMK, WLPBMK, WLTWB** | nur die Vorlagen-Kürzel (Wert „-“) |

### Systeme, die nur in einer Quelle stehen

- **Nur in der Vorlage, nicht in der ATT-Liste:** DEM (Demontage), STA (Standard), UDF (Undefiniert). Das sind Hilfssysteme, ATT nummeriert sie mit dem Rückfall.
- **Nur in der Vorlage, nicht im AKS-Tab Medien:**
    - die Lüftungssysteme nach EN 16798: SUP, ETA, ODA, EHA, RCA, MIA, PEA, DID, ENT, UEST, DA;
    - AEA, AEM, die Wirklinien und DEM/STA/UDF.
    - Bei ATT sind sie über `config/quellen/ATT_zusatz_medien.csv` abgedeckt (RLT bzw. „-“).
- **Nur in der Vorlage, nicht im AKS-Tab Layer:**
    - Ohne Zeile: AG, AC, DEM, KOK, MADL, NOEW, PAGL, PR, SPN, SPT, STA, SYL, UDF.
    - Die übrigen Fehlenden (D-8.0, KD-8.0, KW-*-S, TOEVL/TOERL, WL*) stehen dort unter anderem Kürzel (siehe Tabelle oben).
- **Nur in der ATT-Liste, nicht in der Vorlage:**
    - die alten Lüftungskürzel **AB, ZU, UM, AU, FO, MI** (Zusatzliste, Stand vor EN 16798);
    - die AKS-Schreibweisen D-8, KD-8, KW-S-*, TOE-*, BEENTLÜ.
    - Das stört nicht, ist aber Altbestand.

### Symbolstil-Kürzel

- **Übereinstimmung:** Alle 379 Symbolstile mit AKS-Kürzel tragen in der Vorlage dasselbe Kurzzeichen (Stilbeschreibung = AKS-Symbolübersicht). Hier gibt es **keinen Widerspruch**.
- **37 Stile der Vorlage haben kein AKS-Kürzel:**
    - Elektro-Symbole: Steckdosen, Schalter, Leuchten, Melder, Dosen.
    - Hilfsstile: Pfeile, Verbindungspunkt, Schnittstelle, Standard, MedienPunkt, Bauteil Allgemein.
    - 3 ASG-Symbole: `ASG_Startsymbol…`, `ASG_Verteiler…`, `ASG_Waermetauscher…`.
    - Sonstige: Heizung, Hosen-Bogen, T-Bogen, Serviceventil, Ölspiegelregulator.
    - Für ATT ist das unkritisch: Diese Stile bekommen das Kürzel aus der Stilbeschreibung bzw. „xx“.

## 4. Layerliste

- **In der Zeichnung gibt es 29 Layer, keiner davon gehört zu einem System:**
    - `Z_*`: Schema 1 214 Objekte, Schema_Symbol 666, Symbol-Beschriftungen 631, Legende, Beschriftungen, Plankopf, Rahmen …
    - `G-*` / `A-*`: Grundriss-Hintergrund.
    - `NA_*`: 6 Layer von ANA (Teilstrecken, Verzweigungen …).
    - `ADM_Marke`, `0`, `Defpoints`.
- **Die Farbe kommt nicht vom Layer:** Alle Schemaleitungen liegen auf `Z_Schema`. Ihre Farbe gibt das **Anzeigethema** vor, das nach **System** färbt (Thema „Medien“, 99 Regeln „Systemname (Kürzel)“, 7 Anzeigethemen in der Zeichnung).
- **Der AKS-Tab „Layer“ beschreibt keine Zeichnungslayer.** Er ist eine Liste der Leitungssysteme mit Darstellung:
    - je System Name (Kürzel), Gewerk, Farbe, Linientyp, Linienstärke, Schraffur;
    - 86 Einträge;
    - der Form nach ein Export des Layer-Managers, inhaltlich deckt er sich mit den Systemdefinitionen der Vorlage.
- **Lässt er sich aus dem Thema erzeugen? Teilweise:**
    - **Kürzel, Name und Farbe:** ja, aus Thema „Medien“ (ASG liest es schon aus) und den Systemdefinitionen (Name, LabelName, Gruppe).
    - **Linientyp, Linienstärke und Schraffur:** nicht aus dem Thema. Sie stehen in den Systemdefinitionen bzw. Leitungsstilen der Vorlage und wären von dort zu lesen (nicht geprüft).
    - Eine Rückrichtung AKS → Vorlage ist nicht nötig, wenn die Vorlage führend ist.
- **Farbabgleich mit Thema „Medien“** (Rohwerte verglichen): Nur **2** Systeme weichen ab.

| System | AKS heute | Vorlage (Thema) |
|---|---|---|
| Feuerlöschleitung Nass (FLN) | ACI 102 | ACI 40 |
| Feuerlöschleitung Trocken (FLT) | ACI 142 | ACI 20 |

- Im Thema tragen **Sprinkler-Nass/-Trocken (SPN/SPT)** genau die bisherigen AKS-Farben von FLN/FLT.
- Die Änderung E80/E81 ruht, sie geht in diesem Vorhaben auf.

## Entscheidungen für den Nutzer

1. **Führende Quelle:**
    - Vorschlag: Die Hausstandard-Vorlage ist führend für Systeme (Kürzel, Name, Farbe).
    - Der AKS-Tab Layer wird daraus erzeugt, statt von Hand gepflegt.
    - Linientyp und Linienstärke aus den Systemdefinitionen.
2. **Kürzel vereinheitlichen** – welche Schreibweise gilt?
    - KW-VL-S oder KW-S-VL, D-8.0 oder D-8, TOEVL oder TOE-VL, BEENTLUE oder BEENTLÜ, WLFBMK oder WL-FREMD …
    - Die Vorlage (LabelName) wirkt in allen Zeichnungen. Eine Änderung dort ändert die Systemdefinition.
3. **13 Systeme ohne AKS-Zeile ergänzen?** AG, AC, DEM, KOK, MADL, NOEW, PAGL, PR, SPN, SPT, STA, SYL, UDF.
4. **Feuerlöschleitung ↔ Sprinkler:** Sind die neuen Farben von FLN/FLT im Thema gewollt? Sprinkler haben die alten.
5. **Alte Lüftungskürzel** AB/ZU/UM/AU/FO/MI aus der ATT-Zusatzliste streichen? Die Vorlage nutzt SUP/ETA/ODA/EHA/RCA …
6. **Eigenschaftssätze aufräumen?**
    - 12 ungenutzte Sätze.
    - Dubletten zusammenlegen: TAGBMK* (4 → 1 mit Feld „Art“?), TAGProbeNahme/TAGEntNahme/BeprobungspunktTrinkwasser.
    - Hinweis: Zusammenlegen ändert Feldnamen, die Stempel und DataManager-Formeln benutzen. Deshalb nur mit Plan.
    - TAGBauteil bleibt unverändert (Regel).
7. **Stempel:**
    - Den Ansichtsblöcken `TAG…BMK_*` die gleichen Namen geben wie den Mehransichtsblöcken.
    - `TAGBauteil_01_01` zeigt Beschriftung05–09, die es im Satz nicht gibt: Felder ergänzen oder Stempel kürzen?
8. **Roche-Namen im Eichler-Hausstandard umbenennen?**
    - Textstile `Roche*`, Schriftdatei `ROCHL__.TTF`, auch an Rechnern ohne Roche-Schrift prüfen.
    - Layer und Sätze mit Projektbezug.
9. **Elektro- und Hilfsstile** (37 ohne AKS-Kürzel): im Hausstandard behalten, und mit welchem Kürzel?
