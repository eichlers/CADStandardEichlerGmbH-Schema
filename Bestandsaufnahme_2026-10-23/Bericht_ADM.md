# Bestandsaufnahme ADM – gemeinsame Zeichnungsvorlage (Eichler-Hausstandard auf Basis RI 9.1)

Stand 23.10.2026 · ADM 0.9.24 · nur gelesen, nichts geändert.

**Grundlage:** Kopie `C:\Temp\AMK_Vorlage\adm_lauf\ADMTest_Vorlage_Inventur.dwg` der Basis `Basis_ANA_Test_2_RI_9.1_20261023.dwg`.
Gelesen mit accoreconsole 2026 (`/isolate`, eigenes Lese-Plugin, `_QUIT _Y`). Es wurde nichts gespeichert, die Basis ist weiter
schreibgeschützt.
**Rohdaten:** `adm_lauf\adm_inventur.txt` und `adm_lauf\adm_inventur2.txt`. Plugin und Lauf liegen in `adm_inventur\`.

## Kurzfassung

- ADM bringt **keine eigenen Eigenschaftssätze, Tabellenstile oder Bauteiltabellen** mit. ADM zeigt, was die Vorlage
  hat: jedes Objekt mit mindestens einem Eigenschaftssatz wird eine Zeile, jedes Feld eine Spalte.
- ADM legt bei Bedarf selbst an: die Layer `ADM_Marke`, `ADM_Import` und `ADM_Aenderung`, die RegApp `ADM_MARKE` und den
  Wörterbucheintrag `ADM_EICHLER/Revision`. Die Vorlage muss dafür nichts vorbereiten.
- **In der Basis liegen noch 3 ADM-Marken** auf dem Layer `ADM_Marke`. Das sind Testreste und gehören nicht in eine Vorlage.
- **Plankopf:** `Aspire_TB_A2` und `Rocherahmen` im Layout „Vorlage“ haben weder Attribute noch Eigenschaftssätze.
  ADM sieht den Plankopf also nicht, ein Konflikt „Plankopf zählt als Bauteil“ besteht hier nicht.

## 1 Tabellenstile

### 1a AutoCAD-Tabellenstile (TABLESTYLE)

| Name | Aufbau | verwendet |
|---|---|---|
| Standard | Titel Textstil Standard 6, Kopf und Daten 4,5; Zellränder 1,5; ohne Füllung | nein (0 AutoCAD-Tabellen in der Zeichnung) |

### 1b AEC-Bauteiltabellenstile (Stücklisten)

Vier Bauteiltabellen stehen im Modell, alle auf dem Layer `Z_Tabellenobjekte`.

| Stil | gilt für | Spalten (Satz:Feld) | verwendet |
|---|---|---|---|
| HVACRaumBuch | Raum (AecDbSpace) | HVACRaum: Geschoss, Zone, Nummer, Name, RRKlasse (verborgen), DruckSoll, Feuchte, Temperatur, Fläche, Höhe, Volumen, LWGewählt (verborgen), LWBerech, Formel m³/m², Zuluft, Abluft, ProzessAbluft, Umluft, Zuströmung, Abströmung | ja (1) – es gibt aber **keine Räume** in der Zeichnung, die Tabelle bleibt leer |
| StücklisteArmaturen | Schemasymbol | Menge, TAGBauteil:Zone, TAGBauteil:PosNr, **danach eine Spalte mit Fehler `eKeyNotFound`** (verweist auf ein Feld, das es nicht gibt) | ja (1) |
| StücklisteKühlerErhitzer | Schemasymbol | Menge, TAGBauteil: PosNr, Zone, Fabrikat, Typ, Groesse, DurchFluss, Leistung, Druck, Bemerkung; StilSchemaSymbol:Stil | ja (1) |
| StücklistePumpen | Schemasymbol | Menge, TAGBMKGebauede:ZaehlNr, TAGBauteil: PosNr, Modul, SystemAbkz., Fabrikat, Typ, Groesse, DurchFluss, Druck, Bemerkung; StilSchemaSymbol:Stil; EDaten: Leistung, Spannung, Strom | ja (1) |
| Legende | Schemasymbol | Menge (verborgen), **danach eine Spalte mit Fehler `eKeyNotFound`** | nein |
| LeistungsBilanz | Schemasymbol | Menge, TAGBauteil: Modul, Zone, PosNr, BezeichnungFreitext, DurchFluss, Leistung, Druck, Bemerkung | nein |
| MessStutzen | Schemasymbol | PositionsAnker: Nummer, Name; TAGBauteil: BezeichnungFreitext, SystemAbkz. (verborgen), PosNr, Bemerkung (verborgen); drei Formelspalten (AeroSol, DiffDruck) | nein |
| RLTFilterliste | Schemasymbol | Menge, PositionsAnker: Nummer, Name; TAGBauteil: SystemAbkz., PosNr, Bemerkung; StilSchemaSymbol:Stil; TAGRLTFilter: FilterKlasse, Laenge | nein |
| RLTMessStutzen | Schemasymbol | wie RLTFilterliste, dazu TAGRLTFilter: AeroSolAufg, AeroSolMess | nein |
| Standard | alle | keine Spalten | nein |
| Stückliste hydraulische Volumenstromregler | Schemasymbol | Menge, TAGBauteil: PosNr, Modul, SystemAbkz., Fabrikat, Typ, Groesse, DurchFluss, Druck, EinStellWert, Bemerkung; StilSchemaSymbol:Stil | nein |
| StücklisteMSRBMK | Schemasymbol | Menge, TAGBMKGebauede: Auswertung, ZaehlNr, Funktion | nein |
| StücklisteRegelVentile | Schemasymbol | Menge, TAGBMKGebauede:ZaehlNr, TAGBauteil: PosNr, Zone, SystemAbkz., Fabrikat, Typ, Groesse, DurchFluss, Druck, EinStellWert, Bemerkung; StilSchemaSymbol:Stil | nein |
| StücklisteULK | Schemasymbol | Menge, TAGBauteil: PosNr, Zone, Fabrikat, Typ, Groesse, Leistung, DurchFluss, Druck, EinStellWert, Bemerkung; StilSchemaSymbol:Stil | nein |

ADM liest und schreibt **keine** Bauteiltabellen. Was ADM in die Sätze schreibt, erscheint nach dem Aktualisieren der
Tabelle auch in der Stückliste. Fast alle Stücklisten hängen an `TAGBauteil`. Das ist der gemeinsame Kern zwischen ADM und
ATT.

## 2 Eigenschaftssätze und ihre Verwendung

ADM hat **keine eigenen Sätze** und keine Datentabellen-Bezüge. Die Tabelle unten zeigt, was ADM in dieser Vorlage
anzeigt. Gezählt sind Objekte im Modell; Sätze an Objekten in Blockdefinitionen zeigt ADM nicht an.

| Satz | Felder | gilt für | an Objekten im Modell | in Blockdefinitionen |
|---|---|---|---|---|
| ANA_Hydraulik | 127 (Eingaben und viele `Erg_…`) | Schema, Schemasymbol, Block | 1211 Schemalinien, 663 Schemasymbole, 607 MV-Blöcke, 119 Beschriftungskurven | – |
| ANA_Armatur | 43 | Schema, Schemasymbol, Block | 372 Schemasymbole | – |
| TAGBauteil | 49 (PosNr, System/RohrKanalKlasse/SystemAbkz. automatisch, Beschriftung01–04 als Formel, CustomUserFied01–20) | Schemasymbol | 627 Schemasymbole | 17 (Legendenblöcke `eaklLeg-…`) |
| TAGBMKGebauede | ZaehlNr, Funktion, Auswertung | Schemasymbol | 1 | 6 (Legende) |
| TAGBMKMonitoring | ZaehlNr, Funktion, Auswertung | Schemasymbol | 1 | – |
| TAGDaemmung | Klasse, Abschluss, Staerke, 2 Formelzeilen, Bezeichnung (automatisch) | Schema | 2 Schemalinien | – |
| PositionsAnker | Name, Nummer, Geschoss, RRKlasse (alle automatisch aus dem Raum) | Schemasymbol | – | 5 (Legende) |
| TAGRLTFilter | 36 (Maße, Klassen, 10 Formelzeilen …) | Schemasymbol | – | 3 (Legende) |
| EDaten | Strom, Spannung, Leistung, StörMeldung, Bemerkung | Schemasymbol | – | 1 (Legende Pumpe) |
| HVACRaum | 29 (4 Formeln) | Raum | – (keine Räume) | – |
| BeprobungspunktTrinkwasser, TAGBMKFremd, TAGBMKProzess, TAGEntNahme, TAGMedium, TAGMessStutzen, TAGProbeNahme, TAGStrömung | 2–8 | Schemasymbol oder Schema | nirgends | – |
| AecPolygonStil, SpaceEngineeringClassifications, StilSchemaRohrKanal, StilSchemaSymbol, ThermalProperties | stilbasiert | Stile | an Stilen (ADM zeigt sie nicht als eigene Zeilen) | – |
| SpaceEngineeringObjects, ZoneEngineeringObjects | Autodesk-Standard | Raum, Zone | nirgends | – |

**Plankopf und Layouts:** Es gibt ein Layout „Vorlage“ mit 6 Objekten, darunter die Blöcke `Rocherahmen` (Layer `Z_Rahmen`)
und `Aspire_TB_A2` (Layer `Z_Plankopf`), beide **ohne Attribute und ohne Sätze**. Im Modell liegen dazu Beschriftungs- und
Verweisblöcke mit Attributen (`Beschrifter_01/02`, `ZeichnungsVerweis_01–03`, `Z_Hoehenkote`) und 20 lose
Attributdefinitionen auf `Z_Legende`. ADM zeigt Attribute nur, wenn „Einlesen → Block-Attribute“ an ist (Vorgabe: aus).

**Was ADM in der Zeichnung schon vorfindet:** Layer `ADM_Marke` (rot, plottet) mit **3 ADM-Marken** und die RegApp
`ADM_MARKE`. Kein `ADM_EICHLER` im Wörterbuch, keine Layer `ADM_Import` und `ADM_Aenderung`.

## 3 Was ADM in einer gemeinsamen Vorlage braucht oder voraussetzt

1. **Nichts Pflicht.** ADM arbeitet mit jeder Zeichnung, die Eigenschaftssätze hat. Spalten entstehen aus den
   Satzdefinitionen, ohne Sonderfälle im Code.
2. **Stabile Satz- und Feldnamen.** Gespeicherte ADM-Filter, Spaltenreihenfolge, Redundanzkriterien („eindeutig“), Excel- und
   XML-Austausch sowie das Änderungsprotokoll benutzen `Satz:Feld` als Schlüssel. Ein Umbenennen in der Vorlage macht alte
   Filter und Exporte unbrauchbar.
3. **Ein eindeutiges Feld je Bauteilart** für die Redundanzprüfung. Heute stehen in den ADM-Einstellungen
   `RLTLuftdurchlass:FilterNummer` und `…:FilternummerKurzStempel`. Beide stammen aus einer Roche-Projektzeichnung und
   **gibt es in dieser Vorlage nicht**. Naheliegend wäre `TAGBauteil:PosNr`.
4. **Raum am Bauteil als Feld**, nicht über die Lage im Raum. ADM ordnet bewusst nicht geometrisch zu. In der Vorlage
   übernimmt das `PositionsAnker` (automatisch aus dem Raum). Das funktioniert nur, wenn Räume vorhanden sind.
5. **Layer frei.** Die Namen `ADM_Marke`, `ADM_Import` und `ADM_Aenderung` sollten in der Vorlage nicht anders belegt
   sein. Ob `ADM_Marke` schon in der Vorlage stehen soll (mit Farbe und „nicht plotten“), entscheidet der Nutzer, siehe
   unten.
6. **Plankopf:** Soll ADM Plankopfdaten (Projekt, Plan-Nr., Index) anzeigen oder exportieren, braucht der Plankopf Attribute
   oder einen eigenen Satz. ADM liest Layouts und Attribute auf Wunsch schon heute.

## 4 Konflikte und Auffälligkeiten mit anderen Modulen

| # | Befund | betrifft |
|---|---|---|
| K1 | **ANA-Sätze an sehr vielen Objekten:** `ANA_Hydraulik` hängt an 1211 Schemalinien, 663 Symbolen, 607 MV-Blöcken und 119 Beschriftungskurven, `ANA_Armatur` an 372 Symbolen. In ADM wird **jede Rohrleitung eine Zeile**, dazu kommen 170 Spalten aus ANA. Die Tabelle wird groß und unübersichtlich, die Bauteile von ATT gehen darin unter. | ADM, ANA |
| K2 | `ANA_Hydraulik` an **Beschriftungskurven** (AecbDbLabelCurve, 119×). Das sind Beschriftungen, keine Bauteile. In ADM erscheinen sie als Zeilen, in Zählungen von ATT oder ANA vielleicht als Bauteile. | ANA, ATT, ADM |
| K3 | Die Legendenblöcke `eaklLeg-…` enthalten **echte Schemasymbole mit Sätzen** (TAGBauteil 17, TAGBMKGebauede 6, PositionsAnker 5, TAGRLTFilter 3, EDaten 1). ADM zeigt sie nicht an (nur Modell und Layouts). Ein Modul, das auch in Blockdefinitionen sucht, oder die Stücklisten könnten sie mitzählen. | ATT, Stücklisten |
| K4 | **ADM-Testreste in der Basis:** 3 Marken auf `ADM_Marke` und die RegApp `ADM_MARKE`. | ADM |
| K5 | **Defekte Stücklistenspalten:** „Legende“ und „StücklisteArmaturen“ verweisen auf ein Feld, das es nicht gibt (`eKeyNotFound`). | Vorlage |
| K6 | **Roche-Reste:** Rahmenblock `Rocherahmen`; die ADM-Einstellungen nennen Roche-Sätze (`RLTLuftdurchlass`, `Roche.MesspunktNummer`), die in der Vorlage fehlen. | Vorlage, ADM-Einstellungen |
| K7 | **Raumdaten ohne Räume:** `HVACRaum` und die Stückliste `HVACRaumBuch` sind vorhanden, aber es gibt keinen Raum. `PositionsAnker` liefert ohne Räume leere Werte. | Vorlage |
| K8 | Feldnamen `TAGBauteil:CustomUserFied01–20` (Tippfehler „Fied“). Werden sie umbenannt, betrifft das ATT, ADM-Filter und Exporte. | ATT, ADM |
| K9 | Gleiche Feldnamen in mehreren Sätzen, zum Beispiel `Leistung` (TAGBauteil, EDaten, ANA_Hydraulik) und `DurchFluss` (TAGBauteil, TAGRLTFilter). In ADM ist das eindeutig (`Satz:Feld`), fachlich aber doppelt gepflegt: Welcher Wert gilt? | ATT, ANA |

Der von AMK genannte Fall „Plankopf mit ADM-Satz zählte in ATT als Bauteil“ kommt in dieser Basis nicht vor. ADM hat keinen
eigenen Satz, und der Plankopf trägt keinen Satz.

## Entscheidungen für den Nutzer

1. **Testreste entfernen:** Sollen die 3 ADM-Marken, der Layer `ADM_Marke` und die RegApp `ADM_MARKE` aus der
   Hausstandard-Vorlage? Empfehlung: ja.
2. **ADM-Layer vorbelegen?** `ADM_Marke`, `ADM_Import` und `ADM_Aenderung` gleich mit Hausfarbe und „nicht plotten“ in die
   Vorlage legen oder wie bisher bei Bedarf entstehen lassen? Empfehlung: bei Bedarf, dafür „nicht plotten“ als
   ADM-Vorgabe.
3. **ANA-Sätze an Leitungen und Beschriftungen (K1/K2):** Sollen `ANA_Hydraulik` und `ANA_Armatur` in der Vorlage schon an
   allen Objekten hängen oder erst, wenn ANA rechnet? Sollen Beschriftungskurven überhaupt einen Satz tragen? Für ADM
   denkbar: eine vorgegebene Ansicht „nur Bauteile (ohne ANA)“.
4. **Eindeutiges Feld des Hausstandards** für die Redundanzprüfung: `TAGBauteil:PosNr`? Getrennt für BMK
   (`TAGBMK…:ZaehlNr`) und Filter (`TAGRLTFilter:FilterNummer`)?
5. **Plankopf:** Eichler-Rahmen statt `Rocherahmen`/`Aspire_TB_A2`. Soll er Attribute oder einen Satz (Projekt, Plan-Nr.,
   Index, Datum) bekommen, die ADM, ATT und ANA lesen? Dabei gemeinsam festlegen, dass der Plankopf **nicht als Bauteil
   zählt**.
6. **Räume:** Kommen Räume (HVACRaum, PositionsAnker) in die Vorlage, oder fallen `HVACRaum`, `HVACRaumBuch` und
   `PositionsAnker` weg, solange niemand Räume zeichnet?
7. **Aufräumen:** die beiden defekten Stücklistenspalten (K5), ungenutzte Sätze (BeprobungspunktTrinkwasser, TAGBMKFremd,
   TAGBMKProzess, TAGEntNahme, TAGMedium, TAGMessStutzen, TAGProbeNahme, TAGStrömung) und Stücklistenstile behalten oder
   streichen?
8. **Feldnamen festschreiben**, bevor die Vorlage gilt, zum Beispiel `CustomUserFied` → `CustomUserField` (K8).
   Umbenennungen später brechen gespeicherte Filter und Exporte.
9. **Doppelte Fachfelder (K9):** Welcher Satz ist führend für Leistung und Durchfluss, TAGBauteil oder ANA?
