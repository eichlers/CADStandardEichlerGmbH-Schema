# Felder für ATT – Vorschlag für `EHS_Bauteil` (Eichler-Hausstandard)

Stand 23.10.2026. Nur Text, nichts gebaut. Feldnamen sind Vorschläge.

## Was ATT heute an einem Bauteil liest und schreibt

Ermittelt aus dem Code von ATT 0.15.9 und dem Projektprofil Roche BF18:

- **ATT schreibt:**
    - `TAGBauteil:PosNr`, das ist das Kennzeichen (Standardziel).
    - Je Projektprofil weitere Ziele, z. B. `TAGRLTFilter:FilterNummer`.
- **ATT liest, um das Kennzeichen zu bilden:**
    - System: `SystemAbkz` am Symbol = LabelName der Systemdefinition (automatisch).
    - Stilname und Stilbeschreibung (Kürzel).
    - `PositionsAnker:Nummer` (Raum), Werte aus Listen und das Register (Anlage).
- **ATT prüft:**
    - `TAGBMK*:ZaehlNr` auf Doppelungen.
    - Stempel ↔ Satzfeld über Attributkennungen `SATZ:FELD`.
- **ATT zeigt in Stempeln** (nur lesen): Groesse, DurchFluss, Druck, EinStellWert, Leistung, Fabrikat, Typ, Bemerkung, Zone, Modul, Beschriftung01–04.

Nicht genutzt werden die 20 Felder `CustomUserFied01…20` (Schreibfehler „Fied“ im Original) und die Dichtungsfelder.

## A. Felder für `EHS_Bauteil` aus Sicht von ATT

Abkürzungen in der Tabelle: auto = automatische Eigenschaft (MEP), Stil = stilbasiert, P = Pflicht.

| Feld (Vorschlag) | Bedeutung | Typ / Einheit | wer schreibt | wer liest | P | ersetzt heute |
|---|---|---|---|---|---|---|
| **Kennzeichen** | das vollständige Kennzeichen (TAG) des Bauteils, z. B. `01VDV01` | Text | ATT (Nummerieren, nach Vorschau und Rückfrage); von Hand nur über die ATT-Palette (wird als „von Hand“ markiert) | Stempel, ADM/Datenbank, ANA (Anzeige), Listen | ja, wenn das Bauteil getaggt wird | `TAGBauteil.PosNr` |
| **Kennzeichen_Anlage** | Teil 1: Anlagen- bzw. Systemnummer, z. B. `01` (AKS-Medien-Nr. zu PWW-VL) oder die RLT-Anlage `03` | Text (2 Stellen, führende Null) | ATT beim Nummerieren. Quelle: System → Liste medien, bei Lüftung die zugeordnete Anlage | ADM/Datenbank (filtern je Anlage), ATT | ja (mit Kennzeichen) | heute nur im Kennzeichen enthalten bzw. die Anlage im ATT-Register |
| **Kennzeichen_Kuerzel** | Teil 2: Bauteilkürzel, z. B. `VDV` | Text (2–4 Buchstaben) | ATT beim Nummerieren. Quelle: Stil → Liste bauteile, sonst Stilbeschreibung | ADM/Datenbank, ATT | ja (mit Kennzeichen) | im Kennzeichen enthalten |
| **Kennzeichen_Nummer** | Teil 3: laufender Zähler je Anlage + Kürzel | Ganzzahl (1–99 999), Anzeige zweistellig | ATT | ATT (Lücken, Fortsetzen), ADM/Datenbank (sortieren) | ja (mit Kennzeichen) | im Kennzeichen enthalten |
| **Kennzeichen_Gesperrt** | Kennzeichen ist freigegeben/eingefroren: ATT ändert es nicht mehr | Ja/Nein | ATT (Sperren/Freigeben) | ADM/Datenbank, alle Module (Warnung vor Änderungen) | nein | heute nur im ATT-Register (Freigaben) |
| **Taggen** | soll das Bauteil ein Kennzeichen bekommen: ja / optional / nie / ausgeschlossen | Text (Auswahl) | Vorgabe automatisch aus dem Stil; „ausgeschlossen“ setzt ATT | ATT, ADM | nein | heute AKS-Liste taggen (je Stil) + ATT-Register (Ausschluss je Bauteil) |
| **System** | Systemname der Leitung, z. B. „Pumpen-Warm-Wasser-Vorlauf“ | Text, auto | automatisch (Systemdefinition) | ATT, ADM, ANA, Stempel | – | `TAGBauteil.System` |
| **System_Kuerzel** | LabelName des Systems, z. B. `PWW-VL` | Text, auto | automatisch | ATT (Kennzeichen), ADM | – | `TAGBauteil.SystemAbkz.` |
| **Bauteil_Kuerzel** | Kürzel aus dem Symbolstil | Text, auto/Stil | automatisch aus der Stilbeschreibung | ATT, ADM, Stempel | – | `TAGBauteil.KurzZeichenSymbol` / `StilSchemaSymbol.KurzZeichenSymbol` |
| **Bauteilart** | Name des Symbolstils | Text, auto | automatisch | ATT, ADM | – | (heute nur Stilname) |
| **Raum** | Raumnummer am Positionsanker | Text, auto | automatisch (Positionsanker) | ATT (Profile „nach Raum“), ADM | – | `PositionsAnker.Nummer` |

Fachwerte, die ATT nur im Stempel ANZEIGT: Die gehören in den Katalog, aber nicht wegen ATT. ATT braucht nur feste Namen, damit die neuen Stempel sie zeigen können:

- `Nennweite` (DN, Ganzzahl). Ersetzt `TAGBauteil.Groesse`.
- `Volumenstrom` (m³/h, Zahl). Ersetzt `TAGBauteil.DurchFluss`. Bei ANA: Ergebnis oder Vorgabe?
- `Druck` (bar), `Einstellwert` (Text), `Leistung` (kW).
- `Fabrikat`, `Typ`, `Bemerkung` (Text).
- Schreiben je nach Feld: von Hand, ANA oder ADM.

## B. Kennzeichen-Bildung als Felder – Regeln

- **Kennzeichen** bleibt die führende Angabe. Die drei Teilfelder sind ein von ATT geschriebener Spiegel für Datenbank und Filter.
    - Weichen sie ab, zum Beispiel weil das Kennzeichen von Hand geändert wurde, meldet ATT das bei der Prüfung („Teile passen nicht zum Kennzeichen“).
    - ATT überschreibt nichts still.
- **Syntax:** Der Hausstandard nutzt die eingebaute Grundregel `{Anlage}{Kuerzel}{Nummer}`, z. B. `01VDV01`.
    - Projektprofile dürfen andere Syntaxen setzen, z. B. Roche `0218-ZU-02` aus Raum, Luftart und Zähler.
    - Die Teilfelder enthalten dann die Bausteine des Profils (Anlage = leer, Kürzel = Luftart, Nummer = Zähler).
    - Die Bausteine des Profils stehen zusätzlich in `EHS_Projekt`.
- **Nicht gefunden** wird als `xx` eingesetzt (wie heute). Das Teilfeld bleibt dann leer, damit die Datenbank Lücken erkennt.
- **Weitere Kennzeichen** je Bauteil, wie heute die Roche-FilterNummer `0218ZU02`, kommen nicht in `EHS_Bauteil`. Sie gehören als sprechendes Feld in `EHS_Projekt` (z. B. `FilterNummer`), das Profil nennt es als Ziel.

## C. `EHS_Projekt` – was ATT dort erwartet

- Felder mit sprechenden Namen aus dem Projektprofil. ATT schreibt nur in Felder, die das Profil als Ziel nennt. Beispiel: `FilterNummer`.
- Bausteine, die nur ein Projekt kennt: `Luftart`, `RaumKurz`, `Modul`, `Operation`.
- Heute stehen solche Werte als „Zeichnungswerte“ im ATT-Register. Am Bauteil nur dann, wenn sie je Bauteil verschieden sind.
- Freie Beschriftungszeilen (heute `Beschriftung01–04`, `XTagZeile01–10`) gehören hierher, NICHT in `EHS_Bauteil`.

## D. Nur ATT-intern, nicht in `EHS_Bauteil`

Das bleibt im **Register der Zeichnung**: Xrecord `ATT_REGISTER` im Wörterbuch der Zeichnung, kein Satz am Bauteil. Es führt Verlauf und Gründe, die an einem Feld schlecht aufgehoben wären:

- Freigaben (Kennzeichen, Datum, Bemerkung, Höchststand je Nummernkreis),
- Ausschlüsse mit Grund,
- Ausschluss von der Prüfung,
- Markierung „von Hand geändert“,
- Anlage je Bauteil (Lüftung),
- Zeichnungswerte (Modul, Operation),
- Profilwahl.

`Kennzeichen_Gesperrt` und `Taggen = ausgeschlossen` am Bauteil sind der für andere Module sichtbare **Spiegel** davon.

Weiter intern bleiben:

- **Baugruppen:** RegApp `ATT_BAUGRUPPE_FREMD` (XData). Ein Modulsatz ist nicht nötig.
- **Stempelzuordnung:** Stempel ↔ Bauteil über den Positionsanker (MEP), kein Feld.

## E. Begleitende Sätze, die ATT liest (nicht `EHS_Bauteil`)

- **MSR-Kennzeichen (BMK):**
    - Heute 4 gleich aufgebaute Sätze `TAGBMKFremd/Gebauede/Monitoring/Prozess` (ZaehlNr, Funktion, Auswertung).
    - Vorschlag: **ein** Satz `EHS_BMK` mit `BMK_Art` (Fremd/Gebäude/Monitoring/Prozess), `BMK_Nummer`, `BMK_Funktion`, `BMK_Auswertung`.
    - Schreiben: von Hand (Zuarbeit MSR). Lesen: ATT (Doppelungen), Stempel.
- **Probe/Entnahme:**
    - Heute 3 gleiche Sätze (`TAGProbeNahme`, `TAGEntNahme`, `BeprobungspunktTrinkwasser`).
    - Vorschlag: im Kennzeichen von `EHS_Bauteil` aufgehen, mit eigenem Kürzel und eigener Syntax im Profil.
    - `Auswertung` kommt in `EHS_Projekt`, oder in `EHS_Bauteil`, falls hausweit gültig.
- **RLT-Filter** (heute `TAGRLTFilter`, 36 Felder): Fachdaten eines Bauteiltyps.
    - Vorschlag: eigener Typsatz `EHS_Filter` (Filterklasse, Nennluftmenge, Abmessungen, Messstutzen).
    - Die Beschriftungszeilen gehen in die neuen Stempel bzw. in `EHS_Projekt`.

## Entscheidungen für den Nutzer

1. **Kennzeichen in drei Teilfelder spiegeln?** Gut für Datenbank und Filter, aber Pflege durch ATT nötig. Alternative: nur `Kennzeichen`, die Datenbank zerlegt selbst.
2. **Sperre und Ausschluss** als sichtbare Felder am Bauteil (Spiegel des Registers) oder nur im ATT-Register?
3. **Hausstandard-Syntax** `{Anlage}{Kuerzel}{Nummer}` = heute SSKKNN als Grundregel bestätigen?
4. **BMK:** vier Sätze zu einem `EHS_BMK` zusammenlegen?
5. **Probe/Entnahme/Beprobung** als eigene Sätze oder im Kennzeichen aufgehen lassen?
6. **Fachwerte** wie Volumenstrom und Nennweite: Wer ist Eigentümer, wenn ANA rechnet und der Planer von Hand vorgibt? Zwei Felder (Vorgabe/Ergebnis) oder eines?
