# Entscheidungsliste EHS 0.1 – Eichler-Hausstandard (Schema)

**Zweck:** Aus den vier Bestandsaufnahmen (ATT, ADM, ANA, ASG vom 23.10.2026) ist hier **eine** Liste geworden. Erst wenn
diese Punkte entschieden sind, wird die Fassung EHS 0.1 bereinigt.
**Stand:** 23.10.2026, zusammengestellt von AMK. Quellen: `Bestandsaufnahme_2026-10-23\Bericht_ATT/ADM/ANA/ASG.md`,
`Vorschlag_Tabellen_ADM.md`, `Vorschlag_Anschlussnamen_ASG.txt`, `Stammdaten_ATT.csv`, `Kuerzel_Symbole_ATT.csv`, `README.md`.
Alle Zahlen stammen aus diesen Berichten. Wo sich die Berichte widersprechen, steht **⚠ Widerspruch** dabei.

**So antworten Sie:** je Punkt kurz die Nummer und
- **„ja“** – der Vorschlag wird übernommen, oder
- **eine eigene Angabe** (z. B. „A2: nur neue Stile“), oder
- **„später“** – der Punkt bleibt offen und hält EHS 0.1 nicht auf.

Beispiel: `A1a ja · A1b ja · B1 ja, aber TOEVL lassen · F1 später`.
Die ★-Punkte sind die fünf wichtigsten. Sie bestimmen, wie die Module zusammenarbeiten. Bitte diese zuerst.

---

## Bereits entschieden (nicht mehr fragen)

- Hausstandard der Eichler GmbH auf Basis **RI 9.1**.
- **Master** = Zeichnung `ANA_Test_2_CAD-Zeichnungsvorlage_RI_9.1.dwg` + Ihre DXF-Symbole (`SymboleVorlage_DXF`, 20 Dateien).
- **Nur Ihre eigenen Symbole** (393 Stile), keine MEP-eigenen.
- Anzeigethema **„Medien“ ist führend für die Systemfarben**. Der AKS-Konfigurator wird daran angeglichen.
- **Beschriftungsstempel und Tabellen werden komplett neu erstellt.** Alte TAG*-Stempel und Bauteiltabellenstile werden
  nicht repariert. Darum entfallen alle Fragen zu deren Fehlern (Namen der Ansichtsblöcke, Beschriftung05–09, defekte
  Spalten `eKeyNotFound`).
- **`TAGBauteil` bleibt unverändert**, auch der Tippfehler `CustomUserFied`. (Der ADM-Vorschlag, ihn umzubenennen, ist damit erledigt.)
- **Anschlüsse:** Start **links bei 9 Uhr**, dann **im Uhrzeigersinn** herum, und die Anschlüsse **bekommen Namen**
  (Nutzer 23.10.). Das gilt auch für parametrische ASG-Bauteile. Offen sind nur noch Namensschema und Einzelheiten (A1).
- **Materialwechsel** behält 1 Anschluss.
- **Kürzel steht in der Stilbeschreibung** (Description). ATT nimmt das Kürzel aus der Liste, sonst aus der Beschreibung.
  Für ASG-Stile ist das kein Problem.
- Aus früheren Runden: **ein Plankopf zählt nicht als Bauteil** (20.10.); es wird nur noch mit **Schemasymbolen** gearbeitet,
  nicht mit Blöcken (20.10.).
- Regel-Entwurf aus `README.md`: ab EHS 0.1 sind die **Stammdaten führend**; Grafik VonBlock auf Layer 0; Einfügepunkt
  Mitte des Symbols auf der Leitungsachse (Umsetzung siehe A3, A5).

---

## Offene Entscheidungen

### A Symbole und Stile

**A1 ★ Anschlussnamen** (ASG, ANA, ATT)
Befund: 1205 von 1206 Anschlüssen Ihrer Symbole haben keinen Namen. ANA und ATT können sie deshalb nicht unterscheiden.
Nur die ASG-Bauteile haben sprechende Namen („oben 1…n“, „Erzeuger VL/RL, Verbraucher VL/RL“ an der Weiche, „links
oben/unten“ am Wärmetauscher). Start 9 Uhr und Uhrzeigersinn sind entschieden. Bezug ist immer der ungedrehte,
ungespiegelte Stil, Drehen/Spiegeln ändert keine Namen (ASG-Vorschlag a).
- **A1a – Namensschema:** Wie heißen die Anschlüsse?
  **Vorschlag: neutrale Nummern `A1…An`** (Start 9 Uhr, im Uhrzeigersinn), **ohne VL/RL im Namen**. Ein Name „Vorlauf“
  führt in die Irre, wenn dort der Rücklauf angeschlossen wird. Man müsste das Symbol dann spiegeln. Ob Vorlauf oder
  Rücklauf, ergibt sich aus der angeschlossenen Leitung (System).
  Nur wo die Seite physikalisch festliegt, kommt eine **Seitenrolle als Zusatz** dazu:
  - Weiche: „Erzeuger“/„Verbraucher“,
  - Wärmetauscher: „Primär“/„Sekundär“, z. B. `A1 Primär`.

  (Der ASG-Vorschlag „A1 Erzeuger VL“ wird damit zu `A1 Erzeuger`.)
- **A1b – Mittelanschluss** (Reduzierung, Materialwechsel, Anschluss im Einfügepunkt): `A0` oder die letzte Nummer?
  **Vorschlag: `A0`.** Dann verschiebt sich die Zählung der Außenanschlüsse nicht.
- **A1c – gilt auch für ASG-Bauteile?** Verteiler, Puffer, Weiche, Wärmetauscher, Netzstart bekommen das neue Schema,
  abgestimmt mit ANA (die Weiche ist die Rechen-Schnittstelle zu ANA).
  **Vorschlag: ja, mit Übergang.** Die sprechenden Namen („Erzeuger VL“, „oben 1“ …) werden zu `A1…An`, nur an Weiche
  und Wärmetauscher bleibt die Seitenrolle als Zusatz. ASG erzeugt je Bauteilart eine neue Formversion. `ASGAENDERN` kennt alte und neue
  Namen, damit vorhandene Zeichnungen weiter gehen. Bei geänderter Stutzenzahl ordnet ASG über Lage und Bedeutung zu,
  nicht nur über die Nummer.

**A2 ★ Schreibweise der Stilnamen und Umbenennen** (ASG, ANA, ATT, ADM)
Befund: Die Schreibweisen sind gemischt: Umlaute neben ae/oe/ue („Ruehrwerk“ neben „Rührer“, ASG-Namen mit
„Waerme…“), „Meßstutzen“ neben „Messstutzen“, Leerzeichen neben Bindestrich, Groß und klein uneinheitlich. Dazu kommen
Tippfehler (siehe Liste am Ende). Stilnamen sind eine Schnittstelle: Ein Umbenennen trifft die Erkennung in ANA, die
ATT-Listen und ADM-Auswertungen. In bestehenden Zeichnungen überschreibt ein Stilimport gleichnamige Stile.
Vorschlag:
- Regel nach ANA: die **Art steht vorn**, als ganzes deutsches Wort **mit Umlauten, ohne ß und ohne ae/oe/ue**.
  Zum Beispiel „Reduzierung exzentrisch“, „Messstutzen mit Kugelhahn“.
- Danach Funktion und Antrieb (Hand, Motor, Pneumatik).
- Geräte mit eingebautem Ventil werden als Gerät benannt („Umluftkühler mit 2-Wege-Ventil“).
- Die **vorhandenen Stile werden in EHS 0.1 umbenannt**, aber nur über **eine gemeinsame Umbenennungsliste** (alt → neu)
  in den Stammdaten. Diese Liste lesen alle Module (siehe H2).

**A3 Einfügepunkt bei Geräten und Behältern** (ASG)
Befund: Die Regel lautet „Mitte des Symbols auf der Leitungsachse“. Bei 47 Stilen liegt der Einfügepunkt auf keinem
Anschluss, z. B. Behälter, Pufferspeicher, Speicher, Pumpen-Varianten, Kolonne, Katalysator, Rückschlagventil, Messblende.
Bei Geräten läuft keine Leitung durch die Mitte.
Vorschlag:
- **Durchgangsbauteile:** Mitte auf der Leitungsachse, wie in der Regel.
- **Geräte und Behälter:** Mitte des Körpers, wie die ASG-Bauteile heute.
- **Fehler sind nur Durchgangsbauteile**, bei denen der Einfügepunkt nicht auf der Achse liegt (z. B. Rückschlagventil,
  Rückschlagklappe Flansch, Messblende). ASG meldet sie in der Prüfung.

**A4 Fehlende und überzählige Stile** (ASG)
Befund:
- 76 Ihrer DXF-Blöcke haben **keinen Schemasymbolstil**, u. a. Sammler/Verteiler 4- bis 8-fach, 9 Strang-Symbole,
  20 Elektro-Geräte, Brandschott R30/R90/R120 und 8 Konvektor-Heizkörper.
- 23 Stile stehen **nur in der Zeichnung**, nicht in den DXF. Darunter sind „Platten Wärmetauscher“, „Rohrbündel
  Wärmetauscher“, „Ventil allgemein“, „Eckhahn“, „Differenzdruck Messung“, „Standard“ und die 3 ASG-Stile.

Vorschlag:
- **a)** Hydraulik, Brandschott und Heizkörper werden Stile.
- **b)** Sammler/Verteiler 4–8-fach werden **durch den ASG-Verteiler ersetzt**.
- **c)** Elektro-Geräte und Strang-Symbole folgen später.
- **d)** Von den 23 Stilen nur in der Zeichnung kommen die fachlichen ins DXF-Set (Wärmetauscher, Eckhahn, Ventil allgemein …).
  Die 3 ASG-Stile bleiben ASG-Bauteile. Ungenutzte Reste wie „Standard“ entfallen.

**A5 Grafik und Verbinder einheitlich** (ASG)
Befund:
- Die Regel lautet: Farbe, Linientyp und Linienstärke VonBlock, Layer 0.
- Heute ist die Grafik fast überall **ByLayer auf Layer 0**. Feste Farben gibt es keine.
- **29 Stile** haben eine **feste Linienstärke**, u. a. Absperrklappen, Umschaltventile, Filter, Volumenstromregler.
- Zwei Verbinderstile sind im Einsatz: „Schaltbildverbinderstil“ (16 Stile) und „Schematic Connector Style“
  (5 Stile, Datenpunkte/Pfeile).

Vorschlag:
- Alle Stile auf VonBlock umstellen, auch die 29.
- ASG prüft vorher an einer Kopie in MEP, dass die Farbe aus dem Thema „Medien“ weiter wirkt.
- Es gibt nur noch **einen Verbinderstil**: „Schaltbildverbinderstil“.

**A6 Anzahl der Anschlüsse je Bauteilart** (ASG, ANA)
Befund: 127 Stile haben nur 1 Anschluss. Das sind meist Anbauteile (Antriebe, Entlüftung, Tanks, Leuchten,
Luftdurchlässe, Pfeile), aber auch „3-Wege Mischventil Hand“.
**⚠ Widerspruch** bei Durchgangsbauteilen:
- Der README-Entwurf sagt „2 Anschlüsse (`Ein`, `Aus`)“.
- ANA verlangt „2 durchgehende + 1 Mitte“.
- Ihre 2-Wege-Regelventile haben heute 3 (links, rechts, Mitte).

Vorschlag:
- Es gilt die **ANA-Tabelle** als Pflicht: Durchgangsarmatur 2 + Mitte `A0`, 3-Wege-Ventil 3, Verbraucher ≥ 2,
  Wärmetauscher 4 …
- Anbauteile (Antriebe, Plombierung …) bleiben bei 1 Anschluss.
- „3-Wege Mischventil Hand“ ist ein Fehler und bekommt 3 + Mitte.

**A7 Symbolrichtung = Fließrichtung** (ASG, ANA)
Befund: Heute ist die Richtung uneinheitlich eingemessen: Pfeil und Rückschlagarmatur zeigen in +X, die Pumpe gegen X.
Bei der Reduzierung liegt die große Seite auf −X, bei „Reduzierung exentrisch“ auf +X. Darum prüft ANA diesen Stil nicht
auf „verkehrt herum“.
Vorschlag:
- Bei Pumpe, Rückschlagarmatur, Pfeil und Reduzierung ist **+X immer die Fließrichtung**, bei der Reduzierung „groß → klein“.
- Die exzentrische Reduzierung wird gleich gelegt wie die konzentrische.
- Danach prüft ANA alle Stile auf „verkehrt herum“.

### B Kürzel, Systeme, AKS

**B1 ★ Schreibweise der System-Kürzel** (ATT, ANA, ASG, AKS)
Befund: Bei 5 Gruppen weichen Vorlage (LabelName) und AKS voneinander ab:

| Vorlage | AKS |
|---|---|
| KW-VL-S / KW-RL-S | KW-S-VL / KW-S-RL |
| D-8.0 / KD-8.0 | D-8 / KD-8 |
| TOEVL / TOERL | TOE-VL / TOE-RL |
| BEENTLUE | BEENTLÜ |
| WLFBMK, WLGBMK, WLMBMK, WLPBMK, WLTWB | WL-FREMD, WL-GEB, WL-MON, WL-PRO, WL-TWB |

Die ATT-Liste kennt bei den ersten vier Gruppen beide Schreibweisen. Ein geänderter LabelName wirkt in allen Zeichnungen
aus der Vorlage.
Vorschlag:
- Die **Vorlage ist führend**, passend zu „Medien führend“: KW-VL-S, D-8.0, BEENTLUE (Kürzel ohne Umlaut) und WL…BMK
  bleiben.
- **Einzige Ausnahme:** Thermo-Öl wird **TOE-VL / TOE-RL**, so wie alle anderen Kreise mit „-VL/-RL“. Das empfiehlt auch ANA.
- Das AKS und die ATT-Liste werden angeglichen. Die AKS-Schreibweisen fliegen aus der ATT-Liste.

**B2 AKS-Tab „Layer“ aus der Vorlage erzeugen** (ATT, AMK)
Befund: Der Tab ist keine Layerliste, sondern eine Liste der Systeme mit Darstellung (86 Einträge). 13 Systeme der
Vorlage fehlen darin: AG, AC, DEM, KOK, MADL, NOEW, PAGL, PR, SPN, SPT, STA, SYL, UDF. Kürzel, Name und Farbe lassen sich
aus dem Thema „Medien“ und den Systemdefinitionen erzeugen. Linientyp, Linienstärke und Schraffur stehen nicht im Thema.
Vorschlag: Der Tab wird künftig **automatisch aus der Vorlage erzeugt**, mit allen 99 Systemen, also auch den 13.
Linientyp und Linienstärke kommen aus den Systemdefinitionen bzw. Leitungsstilen. Von Hand pflegt diesen Tab niemand mehr.

**B3 Farben Feuerlöschleitung ↔ Sprinkler** (ASG, ATT)
Befund: Nur 2 Systemfarben weichen zwischen AKS und Thema „Medien“ ab:

| System | AKS | Thema „Medien“ |
|---|---|---|
| FLN | ACI 102 | ACI 40 |
| FLT | ACI 142 | ACI 20 |

Sprinkler-Nass/-Trocken (SPN/SPT) tragen im Thema genau die alten AKS-Farben von FLN/FLT. Das sieht nach einem Tausch aus.
Frage: Sind die neuen Farben gewollt?
Vorschlag: **ja, das Thema gilt** (Medien ist führend). Bitte nur bestätigen, dass der Tausch kein Versehen ist.

**B4 Alte Lüftungskürzel streichen** (ATT)
Befund: In der ATT-Zusatzliste stehen noch AB, ZU, UM, AU, FO, MI. Das ist der Stand vor EN 16798. Die Vorlage nutzt
SUP, ETA, ODA, EHA, RCA, MIA …
Vorschlag: **streichen.**

**B5 Symbol-Kürzel vervollständigen** (ASG, ATT, AKS)
Befund:
- 22 Stile haben eine **leere Stilbeschreibung**, also kein Kürzel: Steckdosen, Leuchten, Melder, Dosen, Pfeile,
  Hosen-Bogen, T-Bogen, Verbindungspunkt, MedienPunkt, Serviceventil, Aufbau dreifach.
- Ein Teil der vergebenen Kürzel steht nicht in der AKS-Liste. **⚠ Widerspruch:** ASG zählt 24 solche Kürzel (AD, BA, H,
  LAE, LBS … ÖR), ATT zählt 14. Laut ASG ist die Vergleichsliste von ATT maßgeblich.
- ATT zählt 37 Stile ohne AKS-Kürzel (Elektro, Hilfsstile, 3 ASG-Stile).

Vorschlag:
- Alle Stile, die gezählt oder getaggt werden, bekommen ein Kürzel. Das betrifft auch Elektro und Serviceventil.
- Reine Hilfsstile (Pfeile, Verbindungspunkt, MedienPunkt) bleiben ohne Kürzel und werden in den Stammdaten als
  „Taggen: nie“ geführt.
- Die fehlenden Kürzel kommen **ins AKS**: zuerst AKS, dann die ATT-Liste, dann ASG.

**B6 ANA-Kreise und Medium** (ANA)
Befund:
- `Kreise.json` hat einen Kreis „Kühl-Wasser-sekundär (KW-S)“. ANA meldet dafür kein System in der Zeichnung.
  **⚠ Widerspruch:** ASG und ATT führen die Systeme KW-VL-S / KW-RL-S. Vermutlich sucht ANA die AKS-Schreibweise.
- Thermo-Öl steht in `Kreise.json` ohne Bindestrich (TOEVL).
- Medium PWW: `Kreise.json` sagt „Wasser“, die Zeichnung hat an 01HNS01 bzw. 23HWT01 „Antifrogen-N 25 %“ gewählt.

Vorschlag:
- `Kreise.json` wird an B1 angeglichen: KW-VL-S/KW-RL-S und TOE-VL/TOE-RL. Der Kreis KW-S bleibt.
- Für PWW gilt im Hausstandard **Wasser**. Antifrogen wird nur im Projekt gewählt.

### C Eigenschaftssätze (Property Sets)

**C1 Feldkatalog festschreiben, bevor die Vorlage gilt** (AMK, alle)
Befund: Gespeicherte ADM-Filter, Excel/XML-Austausch, ATT-Listen und die neuen Tabellen arbeiten mit `Satz:Feld` als
Schlüssel. Ein Umbenennen später bricht sie. Die neuen Listen sollen sich nur auf einen **Feldkatalog** beziehen (Name,
Einheit, Rundung). Für die Redundanzprüfung braucht ADM ein eindeutiges Feld je Bauteilart. In den ADM-Einstellungen
stehen heute Roche-Felder (`RLTLuftdurchlass:FilterNummer`), die es in der Vorlage nicht gibt.
Vorschlag:
- AMK legt den **Feldkatalog** als Stammdatei an, bevor EHS 0.1 gebaut wird.
- Eindeutiges Feld ist **`TAGBauteil:PosNr`**, bei BMK `TAGBMK…:ZaehlNr`.
- Für Filter ist es das von ADM vorgeschlagene Filter-Nummernfeld. Ob es dieses Feld in der Vorlage gibt, ist nicht
  geprüft.

**C2 Welcher Satz ist führend für Leistung, Durchfluss, Einstellwerte?** (ANA, ATT, ADM)
Befund: Gleiche Fachfelder stehen in mehreren Sätzen, z. B. `Leistung` in TAGBauteil, EDaten und ANA_Hydraulik,
`DurchFluss` in TAGBauteil und TAGRLTFilter. ANA nimmt die Leistung aus TAGBauteil nur als Rückfall, mit Hinweis.
Vorschlag: **ANA-Sätze sind führend.** TAGBauteil bleibt Transportkopie, unverändert. Die neuen Listen lesen nur aus den
ANA-Sätzen.

**C3 An welchen Objekten hängen ANA-Sätze in der Vorlage?** (ANA, ADM, ATT)
Befund:
- `ANA_Hydraulik` hängt an 2 600 Objekten: 1 211 Schemalinien, 663 Symbole, 607 MV-Blöcke und **119 Beschriftungskurven**.
- `ANA_Armatur` hängt an 372 Symbolen.
- In ADM wird jede Rohrleitung eine Zeile, mit rund 170 ANA-Spalten. Die Bauteile gehen darin unter.

Vorschlag:
- In der Vorlage hängen ANA-Sätze **nur dort, wo ANA sie beim Erfassen anhängt**. Das passt zur AMK-Regel „Sätze beim
  Erfassen des Netzes“.
- **Beschriftungskurven tragen keinen Satz.**
- Ergebnisfelder `Erg_…` sind leer.
- ADM bekommt eine vorgegebene Ansicht „nur Bauteile (ohne ANA)“.

**C4 Ungenutzte und doppelte Sätze** (ATT, ADM)
Befund:
- **12 Sätze hängen an nichts**: TAGBMKFremd, TAGBMKProzess, TAGProbeNahme, TAGEntNahme, BeprobungspunktTrinkwasser,
  TAGMessStutzen, TAGMedium, TAGStrömung, SpaceEngineeringObjects, ZoneEngineeringObjects, ThermalProperties,
  AecPolygonStil. HVACRaum hat 0 Objekte, weil die Zeichnung keine Räume hat (siehe C5).
- Echte Dubletten: die 4 TAGBMK*-Sätze und die 3 Sätze mit PosNr/Auswertung.

Vorschlag:
- In EHS 0.1 werden die ungenutzten **MEP-Standardsätze entfernt**: SpaceEngineeringObjects, ZoneEngineeringObjects,
  ThermalProperties, AecPolygonStil. SpaceEngineeringClassifications bleibt, weil es an 245 Klassifizierungen hängt.
- Die **TAG*-Sätze bleiben vorerst**. Zusammenlegen oder Streichen erst mit dem Feldkatalog (C1) und den neuen Stempeln,
  weil sich dabei Feldnamen ändern.

**C5 Räume im Hausstandard?** (ADM, ATT)
Befund: `HVACRaum` (29 Felder), `PositionsAnker` und die Tabelle `HVACRaumBuch` sind da, aber es gibt keinen Raum. Ohne
Räume liefert PositionsAnker leere Werte. ATT liest die Raumnummer daraus. Die Verbraucherliste braucht den Raum, sonst
nimmt sie die Zone aus TAGBauteil.
Vorschlag: **Räume bleiben möglich.** HVACRaum und PositionsAnker bleiben, das Raumbuch wird neu als AEC-Tabelle (T13)
angelegt. Solange kein Raum gezeichnet ist, nehmen die Listen `TAGBauteil:Zone`.

### D Anzeigethemen, Layer, Plankopf

**D1 Welche Anzeigethemen kommen in die Vorlage?** (ASG, ANA)
Befund: ASG zählt 10 Themen:
- 5 ANA-Themen (Bewertung, Geschwindigkeit, Leistung, Rohr DN, Rohrreibung),
- „DN Rohrleitung“ (eine Kopie eines ANA-Themas, trägt intern noch den Titel „ANA Rohrreibung“),
- Medien, Stoffgruppen, RohrKanalKlassen,
- „Standard“ (leer).

**⚠ Widerspruch:** ATT nennt 7 Anzeigethemen.
Vorschlag:
- In der Vorlage bleiben **Medien, Stoffgruppen und RohrKanalKlassen**.
- Die **ANA-Themen legt ANA bei Bedarf selbst an**.
- „DN Rohrleitung“ und „Standard“ entfallen.

**D2 Roche-Namen ablösen** (ATT, ADM, AMK)
Befund:
- Textstile `Roche_SchemaLinie_085`, `Roche_SchemaLegende_1`, `Roche_Vector_c`, `Roche` (Schrift `ROCHL__.TTF`).
- Rahmenblock `Rocherahmen`, Plankopf `Aspire_TB_A2`.
- In den ADM-Einstellungen Roche-Sätze (`RLTLuftdurchlass`, `Roche.MesspunktNummer`).

Vorschlag:
- Die Textstile werden umbenannt auf `EHS_…`. Ein Ersatz für die Roche-Schrift wird an einem Rechner ohne Roche-Schrift
  geprüft.
- Die Roche-Einträge in den ADM-Einstellungen werden entfernt.

**D3 Eichler-Plankopf** (ADM, ATT, ANA)
Befund: `Rocherahmen` und `Aspire_TB_A2` haben weder Attribute noch Sätze. ADM sieht den Plankopf heute also nicht.
Vorschlag: Ein **Eichler-Rahmen mit Attributen** (Projekt, Plan-Nr., Index, Datum) wird neu erstellt, zusammen mit den
neuen Stempeln. Die Module lesen ihn. Er zählt nicht als Bauteil (entschieden).

**D4 ADM-Layer vorbelegen?** (ADM)
Befund: ADM legt `ADM_Marke`, `ADM_Import` und `ADM_Aenderung` bei Bedarf selbst an.
Vorschlag (ADM): Die Layer werden **nicht** in die Vorlage gelegt. Sie entstehen bei Bedarf, und ADM setzt sie dann auf
„nicht plotten“.

### E ANA-Erkennung der Bauteile

**E1 ★ Erkennung über eine Kürzel-Tabelle statt über Wörter im Stilnamen** (ANA, AMK, ASG)
Befund:
- ANA erkennt die Bauteilart heute zuerst am Eintrag in ANA_Armatur/ANA_Hydraulik, sonst an Wortteilen im Stilnamen.
  Das Kürzel nutzt es nur für PUM, NER, HVB und HWT.
- Die Basis rechnet richtig. Aber **311 Volumenstromregler und der KFE-Hahn** gehen nur durch Einträge von Hand. In einer
  neuen Zeichnung wären sie „Rolle nicht erkannt“.
- **⚠ Widerspruch:** Ein Kürzel steht oft an mehreren Stilen, insgesamt 71 Kürzel. **VDV** steht laut ANA am
  „Volumenstromregler Einstellbar Motor“, laut ASG aber auch an 2-/3-Wege-Regelventilen und am „3-Wege Mischventil Hand“.
  Eine Tabelle „VDV → PICV“ wäre damit falsch.

Vorschlag:
- ANA erkennt im Hausstandard **zuerst über das Kürzel**. Die Tabelle **pflegt AMK** als gemeinsame Stammdatei.
- Stilwörter sind nur noch Rückfall.
- **Vorher** wird jedes Kürzel, das mehrere Bauteilarten deckt, aufgetrennt (VDV/VHF, siehe E2).

**E2 Volumenstromregler** (ANA, ASG, AKS)
Befund: „Volumenstromregler Einstellbar Motor“ (VDV, 282×) und „Einstellbar“ (VHF, 28×) rechnet ANA nur durch Eintrag als
PICV bzw. 1× als PIBV. Alle 9 Varianten erkennt ANA am Stil nicht.
Vorschlag: Sie gelten im Hausstandard als **PICV (druckunabhängiges Regelventil)** und bekommen ein **eigenes Kürzel**,
das nicht VDV heißt. Den Namen des Kürzels legt AKS/ATT fest. Volumenstromregler ohne Druckunabhängigkeit sind PIBV.

**E3 Stile, die ANA heute falsch einordnet** (ANA, ASG)
- **a)** „Druckreduzierung“ wird als Formstück gerechnet. Vorschlag: Sie heißt künftig **„Druckminderer“** und wird als
  Ventil mit Druckverlust gerechnet.
- **b)** „Umluftkühler/Umluftheitzer 2-/3-Regelventil“ wird als Regelventil gerechnet, „3-Regelventil“ sogar als 2-Wege.
  Vorschlag: Sie werden **als Verbraucher** geführt und „Umluftkühler/Umluftheizer mit 2-/3-Wege-Ventil“ genannt.
- **c)** „Differenzdruck Messung (Fluid)“ und „Messung Durchfluss Differenzdruck“ werden als Differenzdruckregler gerechnet.
  Vorschlag: Sie sind **Messstellen** bzw. Messblende. Bei „Absperrventil Differenzdruck (mit Prüfanschluss)“ entscheiden Sie
  bitte: Strangabsperrventil oder Partnerventil?
- **d)** 3-Wege-Umschalthahn/-ventil, 3-Wege-Hahn und 3-Wege-Absperrorgan werden als 3-Wege-Regelventil gerechnet.
  Vorschlag: Sie bekommen eine eigene Art **„Umschaltarmatur“** (kein Regelventil).

**E4 Nicht erkannte Armaturen** (ANA)
Befund: Diese Armaturen ergeben heute „Rolle nicht erkannt“ und 0 kPa: KFE-Hahn, KFR-Ventil, Eckhahn, Kappenventil,
Serviceventil, Vorabsperrung, Regulierventil, Ventil allgemein, Absperrorgan Allgemein (4), Magnetventil, Membranventil (5),
Nadelventil, Schrägsitzventil (2), Wechselventil Hand, 4-/6-Wege-Umschaltventil, Filter, Feinfilter, Rückspülfilter,
Festbettfilter, Lochblende, Verschneide-Armatur, Temperatur-Regler, Stellungsregler.
Vorschlag:
- KFE/KFR/Eck/Kappen/Service: Entleerung bzw. Absperrarmatur.
- Regulier, Ventil allgemein, Absperrorgan, Membran, Nadel, Schrägsitz, Magnet: Absperrarmatur mit kvs.
- Filter: wie Schmutzfänger.
- Lochblende: Messblende.
- 4-/6-Wege: Umschaltarmatur (E3d).
- Stellungsregler und Temperatur-Regler: kein hydraulisches Bauteil.

ANA legt dazu eine Tabelle zum Abhaken vor.

### F Tabellen und Listen (ADM)

**F1 ★ Wer füllt die neuen Listen?** (ADM, ANA)
Befund: ADM liest schon alle Sätze, kennt Filter und Gruppen und hat den Excel-Export. Laut Konzept läuft der Export nur
über ADM. Die Alternative wäre: ANA füllt die hydraulischen Listen selbst. Dann gäbe es zwei Tabellenbauer.
Vorschlag: **ADM füllt alle Listen** (Befehl `ADMLISTE`) aus einer Listendefinition, und Excel kommt aus derselben
Definition. ANA löst nach der Rechnung nur „Listen aktualisieren“ aus.

**F2 Art der Tabellen** (ADM)
Befund: Die AEC-Bauteiltabelle kann nicht nach Feldwert filtern, keine Summen bilden und keine Symbole zeigen. Mit „hat
Satz ANA_Hydraulik“ trennt sie keine Bauteilarten.
Vorschlag:
- **AutoCAD-Tabellen**, von ADM gefüllt, für alle Fachlisten und die Legende. Der Stil heißt `EHS_Liste`, der Layer
  `Z_Tabellenobjekte`.
- Die AEC-Tabelle bleibt nur für das Raumbuch.
- Die **live mitlaufende „Stückliste allgemein“ (T14)**: ja, als einfache Mengenliste.

**F3 Welche Listen zuerst?** (ADM, ANA)
Befund: ADM schlägt 16 Tabellen vor (T1–T16). T15 (RLT) und T16 (MSR/BMK/Elektro) haben noch keinen passenden Satz.
Vorschlag:
- Zuerst **T2 Ventilliste, T3 Einstellliste, T5 Pumpenliste, T1 Legende**.
- Danach T4, T6–T11.
- T15/T16 erst, wenn die Satzfrage (C1/C4) geklärt ist.

**F4 Legende als Tabelle** (ADM, ASG)
Befund: Die heutigen Legendenblöcke `eaklLeg-…` enthalten echte Schemasymbole mit Sätzen (TAGBauteil 17, TAGBMKGebauede 6,
PositionsAnker 5, TAGRLTFilter 3, EDaten 1). Ein Modul, das auch in Blockdefinitionen sucht, oder eine Stückliste könnte
sie mitzählen.
Vorschlag: Die Legende wird **eine von ADM gefüllte Tabelle** (Symbol, Kürzel, Benennung aus den Stammdaten). Die
Legendenblöcke entfallen. So zählt nichts doppelt.

### G Aufräumen und Reste

**G1 Inhalt der Vorlage: leeres Blatt oder mit Beispielnetz?** (alle)
Befund: Die Basis ist eine Test-/Projektzeichnung. Sie enthält:
- 671 Symbole und 1 226 Schemalinien,
- 618 TAG-Stempel und 4 Bauteiltabellen,
- ANA-Ergebnisse, Medium-Einträge (Antifrogen) und 21 falsche „PICV“-Einträge.

Vorschlag:
- Die **Vorlage enthält keine Zeichnungsobjekte**, nur Definitionen: Stile, Systeme, Themen, Sätze, Layer, Textstile,
  Rahmen.
- Das Beispielnetz bleibt als eigene **Testzeichnung** im EHS-Ordner, für die Prüfung der Module.

**G2 Übergang alte Stempel und Tabellenstile** (ATT, ADM)
Befund: Es gibt 48 alte TAG*-Mehransichtsblöcke (davon 2 genutzt, `TAGBauteilPosNr_01_01` 618×) und 13
Bauteiltabellenstile. Die neuen kommen erst noch.
Vorschlag:
- In EHS 0.1 bleiben die alten noch drin.
- Sie werden in der Fassung entfernt, in der die neuen Stempel und Tabellen fertig sind.
- Alte Zeichnungen stellt der Umstellbefehl um (H2).

### H Ablauf und Werkzeuge

**H1 Rolle von ASG bei den Symbolen** (ASG)
Befund: ASG kann Stile samt Anschlüssen per Programm anlegen, das ist in MEP belegt. Der Umfang ist groß: 393 vorhandene
und 76 fehlende Symbole.
Vorschlag:
- In Stufen: **erst Definitionsliste + Prüfbefehl** (nur lesend).
- Dann **Erzeugen der fehlenden Stile**.
- Zuletzt **Angleichen der vorhandenen**: Namen, Anschlüsse, Grafik.
- Jede schreibende Stufe nur nach Ihrem Go und mit MEP-Nachweis.

**H2 Umbenennungsliste und Umstellbefehl für alte Zeichnungen** (AMK, alle)
Befund: Ein Stilimport überschreibt gleichnamige Stile. Dabei können sich Anschlüsse eingesetzter Symbole verschieben,
sodass sich Leitungen lösen. Umbenannte Stile und Kürzel müssen alle Module gleichzeitig kennen.
Vorschlag:
- AMK führt **eine Umbenennungsliste** (Stile, System-Kürzel, Anschlussnamen alt → neu) in den Stammdaten.
- Jedes Modul liest sie.
- Der Umstellbefehl für alte Zeichnungen kommt später. Bis dahin bleiben alte Zeichnungen auf RI 9.1.

**H3 Reihenfolge bis EHS 0.1** (AMK)
Vorschlag:
1. Ihre Antworten auf diese Liste.
2. Feldkatalog + Umbenennungsliste + Kürzel-Tabelle (AMK).
3. Prüfbefehl ASG gegen EHS 0.0.
4. Bereinigung an der Kopie, je Modul nacheinander, jeweils mit Prüfbericht `Pruefung\EHS_0.1.md`.
5. Ein gemeinsamer Testplan für Sie.

---

## Kann AMK bzw. das Modul ohne Rückfrage erledigen (bitte nur abhaken)

Reine Fehlerkorrekturen. Umbenennungen laufen trotzdem über die Umbenennungsliste (H2).

- [ ] **Tippfehler in Stilnamen** (ASG):
  - „Reduzierung exentrisch“ → exzentrisch
  - „Umluftheitzer“ → Umluftheizer
  - „Dehungsantrieb“ → Dehnstoffantrieb (so steht es schon in der Beschreibung)
  - „Bewegunsgmelder“ → Bewegungsmelder
  - „Kolone“ → Kolonne
  - „Meßstutzen mit Kugelhahn“ → Messstutzen …
- [ ] **Tippfehler in DXF-Blocknamen:** „Luftdurchlass Übertsrömung“, „Verdichter Sroll“ (ASG, nur in der EHS-Kopie
  `Symbole_DXF\`).
- [ ] **Dublette** „Aufbau dreifach“ / „Aufbau_dreifach“ zu einem Stil zusammenführen (ASG).
- [ ] **Beschreibungen der Systemdefinitionen** korrigieren (ASG):
  - „Dofferenzdruck“ (DID)
  - „Test-Pumpen-Warm-Wasser-Vorlauf“ (PWW-VL)
  - „S-Trinkwasser-Warm“ (TWW)
  - „allne nicht zugeordneten Syteme“ (STA)
  - WLTWB heißt „Wirklinie Gebäude BMK“
  - KW-VL-S/KW-RL-S ohne „sekundär“ in der Beschreibung
- [ ] **ADM-Testreste entfernen:** 3 ADM-Marken, Layer `ADM_Marke`, RegApp `ADM_MARKE` (ADM empfiehlt ja).
- [ ] **21 falsche Einträge „PICV Regelventil“** an Reduzierungen (9), Pfeilen (8) und Messstellen (4) entfernen (ANA,
  entfällt bei G1 = leere Vorlage).
- [ ] **Ergebnisfelder `Erg_…` leeren**, falls Objekte in der Vorlage bleiben (ANA).
- [ ] **Roche-Redundanzfelder** aus den ADM-Einstellungen entfernen (`RLTLuftdurchlass:FilterNummer`,
  `…:FilternummerKurzStempel`) (ADM).
- [ ] **Klären (AMK):** In welchem Satz liest man das Kürzel als Feld?
  - README und ADM-Tabellenvorschlag nennen `TAGBauteil:KurzZeichenSymbol`.
  - ASG und ANA lesen `StilSchemaSymbol:KurzZeichenSymbol` (automatisch aus der Stilbeschreibung).
  - Die Annahme von ANA „vermutlich Formel“ ist durch ASG überholt.
  - Danach Regeltext und Tabellenvorschlag angleichen.
- [ ] **Klären (AMK):** Zahl der Anzeigethemen (ATT 7, ASG 10). Vermutlich zählt ATT ohne die von ANA angelegten.
- [ ] **Entfällt** (Stempel und Tabellen neu): Namen der Ansichtsblöcke `TAG…BMK`, `TAGBauteil_01_01` mit Beschriftung05–09,
  gemischte Schreibweise der Attributkennungen, defekte Spalten `eKeyNotFound` in „Legende“ und „StücklisteArmaturen“.
