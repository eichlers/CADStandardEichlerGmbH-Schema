# Bestandsaufnahme ANA – Eichler-Hausstandard auf Basis RI 9.1

Stand 23.10.2026, ANA 0.9.29. Grundlage ist eine eigene Kopie von `Basis_ANA_Test_2_RI_9.1_20261023.dwg`, headless ausgewertet und nie gespeichert. Die Rohdaten liegen in `C:\Temp\ANA_Vorlage\`:
- `objekte.json`: alle 671 Symbole und 1226 Schemalinien mit Stil, System, Anschlüssen, Property Sets und ANA-Erkennung
- `stilart.tsv`: alle 416 Symbolstile durch die ANA-Stilerkennung
- `auswertung.txt` und `stile_auswertung.txt`

Am Code und an der Zeichnung ist nichts geändert.

## 1. ANA-Property-Sets

| Satz | Felder | an welchen Objekten in der Basis | Zweck |
|---|---|---|---|
| **ANA_Hydraulik** | 127 (61 Eingaben, 66 Ergebnisse `Erg_…`) | 663 von 671 Symbolen, 1211 von 1226 Linien | Rolle, Kennzeichen, Leistung/Spreizung/Temperaturen, Pumpe (Bauart, Regelung, η, P1), Systemtrennung, Weiche/Puffer, Auslegung/Sperre, Länge; Ergebnisse (V, Δp, DN, Teilstrecke, Bewertung, Strom …) |
| **ANA_Armatur** | 43 (12 Eingaben, 31 Ergebnisse) | 372 Symbole | Armaturart, Produktwahl (Hersteller/Reihe/Unterart/Merkmale), DN, kvs, Schließfeder, Einbaulage; Ergebnisse (Produkt, Voreinstellung, Regelgüte, Reduzierung, Rohrklasse …) |

Was ANA zusätzlich nur liest:
- **StilSchemaSymbol** (an allen 671 Symbolen), Feld `KurzZeichenSymbol`. Daraus nimmt ANA heute nur die Rolle für PUM, NER, HVB und HWT.
- **TAGBauteil** (627): die Leistung als Rückfall, mit Hinweis „bitte in ANA_Hydraulik eintragen“.
- Die Systemdefinition jeder Linie bzw. jedes Symbols bestimmt den Kreis.

Listendefinitionen (ANA_ArmaturArt, ANA_Auslegung, ANA_Betrieb …) legt ANA selbst an und ergänzt sie. Neue Felder in Altzeichnungen ergänzt ANA, ohne vorhandene Werte zu ändern.

Hinweis: 8 Symbole ohne ANA_Hydraulik liegen auf `Z_Legende` (Legende, Datenpunkte). Die 15 Linien ohne ANA_Hydraulik sind 12 Legendenlinien und 3 Linien fremder Systeme.

## 2. Erkennung der Bauteile: Stilwörter gegen die Stile der Zeichnung

ANA bestimmt die Art in dieser Reihenfolge:
1. Eintrag `ANA_Armatur/ArmaturArt` bzw. `ANA_Hydraulik/Rolle`.
2. Sonst ein Wortteil des Stilnamens (z. B. „Rückschlag“, „Reduzier“, „Pfeil“, „Messstutzen“).
3. Für die Rolle zusätzlich das Kurzzeichen (PUM/NER/HWT/HVB) und Stilwörter („Erhitzer“, „Pumpe“, „Wärmetauscher“ …).
4. ASG-Symbole (`ASG_…`) erkennt ANA über eine eigene Erkennung.

Ein Symbol ohne Funktion (Pfeil, Messstelle) oder ein Formstück bleibt das, auch wenn dort ein Ventil eingetragen ist.

### 2a. In der Zeichnung benutzte Stile (21) – alle werden richtig gerechnet

| Anzahl | Stil | KZ | Anschlüsse | ANA rechnet als | woher |
|---:|---|---|---:|---|---|
| 282 | Volumenstromregler Einstellbar Motor | VDV | 6 | PICV Regelventil | **nur durch Eintrag** (am Stil nicht erkannt) |
| 280 | Erhitzer Zone | NER | 5 | Verbraucher | Kurzzeichen/Stil |
| 28 | Volumenstromregler Einstellbar | VHF | 3 | PICV (27), PIBV (1) | **nur durch Eintrag** |
| 18 | Reduzierung | FRE | 3 | Formstück Reduzierung | Stil; **9 tragen fälschlich „PICV Regelventil“** (5543B, 5084D, 50845, 5083D, 50835, 5082D, 50825, 5081D, 50815) – ANA übergeht den Eintrag |
| 14 | Pfeil Richtung | PR | 3 | Kennzeichnung | Stil; **8 tragen fälschlich „PICV Regelventil“** (5848B, 5832A, 54D78, 54D70, 54D68, 54D60, 52D20, 52D10) |
| 8 | MSR Messstelle Temperatur | MMS | 1 | Messstelle | Stil; **4 tragen fälschlich „PICV Regelventil“** |
| 6 | Flansch-Verbindung | XFL | 3 | Formstück Flansch | Stil |
| 6 | Materialwechsel | FMW | **1** | Formstück Materialwechsel | Stil (ab 0.9.29) |
| 4 | Anzeige Temperatur | MTH | 1 | Messstelle | Stil |
| 4 | Pumpe | PUM | 5 | Pumpe | Kurzzeichen |
| 4 | Rückschlagklappe | VRK | 3 | Rückschlagklappe | Stil |
| 3 | Absperrklappe | VAK | 3 | Absperrklappe | Stil |
| 2 | Kugelhahn | VAH | 3 | Entleerung | Eintrag (am Stil: Kugelhahn) |
| 1 | KFE-Hahn | VEF | 3 | Entleerung | **nur durch Eintrag** |
| 3/1/1 | Datenpunkt Prozess / Gebäudeautomation / Monitoring | MPP/MPG/MPM | 5 | – (Wirklinien, nicht hydraulisch) | richtig: kein ANA-Text |
| 3 | Pfeil | – | 3 | Kennzeichnung, im System „Reinstdampf“, nicht gerechnet | – |
| 1/1/1 | ASG Startsymbol / Verteiler / Wärmetauscher | HNS/DVT/HWT | 2/8/4 | Teilnetzstart / Verteiler / Systemtrennung | ASG-Erkennung |

Die Basis rechnet also richtig. Das liegt aber bei 311 Volumenstromreglern und dem KFE-Hahn an Einträgen von Hand. In einer neuen Zeichnung aus der Vorlage wären sie ohne Eintrag zunächst „Rolle nicht erkannt“. Außerdem stehen 21 falsche Einträge „PICV“ an Reduzierungen, Pfeilen und Messstellen. ANA fängt sie ab, sie gehören aber nicht in eine Vorlage.

### 2b. Alle 416 Stile der Zeichnung – falsch oder gar nicht erkannt (wenn sie benutzt würden)

**Falsch erkannt:**
- „Druckreduzierung“ → Formstück Reduzierung. Fachlich ist das ein Druckminderer (Ventil mit Druckverlust). Grund: Das Stilwort „Reduzier“ trifft.
- „Reduzierung exentrisch“ → Formstück Reduzierung. Tippfehler, richtig wäre „exzentrisch“. Die breite Seite liegt anders herum als bei „Reduzierung“ (+x statt −x). Die Prüfung „verkehrt herum“ prüft diesen Stil deshalb bewusst nicht.
- „Meßstutzen mit Kugelhahn“ → Armatur Kugelhahn. Richtig wäre Messstelle. „Meß-“ mit ß trifft das Wort „Messstutzen“ nicht.
- „Differenzdruck Messung“, „Differenzdruck Messung Fluid“, „Messung Durchfluss Differenzdruck“ → Differenzdruckregler. Richtig wäre Messstelle bzw. Messblende.
- „Absperrventil Differenzdruck (mit Prüfanschluss)“ → Differenzdruckregler. Fachlich zu klären: Strang-Absperrventil oder Partnerventil?
- „Umluftkühler 2-/3-Regelventil (Pumpe)“ und „Umluftheitzer 2-/3-Regelventil“ → Regelventil 2-Wege. Das sind Geräte mit Ventil, also eher Verbraucher. „3-Regelventil“ wird zu 2-Wege, weil „3-Wege“ nicht drinsteht. Dazu der Tippfehler „Umluft**heitzer**“.
- „3-Wege Umschalthahn/-ventil (Hand/Pneumatik)“, „3-Wege-Hahn“, „3-Wege-Absperrorgan“, „3-Wege Kugelhahn Kolbenantrieb“ → Regelventil 3-Wege. Für Umschaltarmaturen vertretbar, fachlich aber keine Regelventile.

**Nicht erkannt** (würde „Rolle nicht erkannt“ und 0 kPa ergeben). Hydraulisch relevant:
- Volumenstromregler (alle 9 Varianten, darunter die zwei benutzten)
- KFE-Hahn, KFR-Ventil, Eckhahn, Kappenventil, Serviceventil, Vorabsperrung
- Regulierventil, Ventil allgemein, Absperrorgan Allgemein (4), Magnetventil, Membranventil (5), Nadelventil, Schrägsitzventil (2), Wechselventil Hand
- 4-Wege Umschalthahn/-ventil, 6-Wege Umschaltventil Motor (ANA kennt „6-Wege-Ventil“ nur als Eintrag)
- Filter, Feinfilter, Rückspülfilter, Festbettfilter, Lochblende, Verschneide-Armatur, Temperatur-Regler, Stellungsregler

Lüftungs- und Sanitärstile (Brandschutzklappe, Ventilator, Jalousieklappe, Tellerventil …) sind für ANA ohne Belang, weil die Systeme nicht gerechnet werden.

Weitere 197 Stile ohne Funktionswort (Geräte, Sanitär, Elektro, Lüftung) erkennt ANA ebenfalls nicht. Für die Hydraulik ist das nur relevant, wenn sie in PWW/PKW/KKW … eingesetzt werden.

**Richtig erkannt (Stichprobe der unbenutzten):** 2-/3-Wege Regelventile, Absperrklappe/-schieber/-ventil, Kugelhähne, Rückschlagventil/-klappe, Schmutzfänger, Sicherheits- und Überströmventil, Messblende, alle Messstutzen und MSR-Messstellen, Anzeige Druck, Entleerung/Entlüftung, alle Heizkörper/Erhitzer/Umluftkühler (ohne Ventil im Namen), Wärmetauscher, Kessel, Pufferspeicher, Pumpen, Pfeile, Flansch-Stutzen/Gegenflansch.

**Schreibweisen:** „exentrisch“, „Umluftheitzer“, „Entlüftungsgefäss“ (ss), „Meßstutzen“ (ß) neben „Messstutzen“, die ASG-Namen mit „Waerme…“. Die Kurzzeichen (`KurzZeichenSymbol`) sind dagegen an allen benutzten Stilen gesetzt und eindeutig, z. B. FRE, FMW, XFL, VAK, VRK, VAH, VEF, VDV, VHF, MMS, MTH, PR, PUM, NER, HWT, DVT, HNS.

## 3. Rohrklassen, Systeme und Kreise

- **Linienstile = Rohrklassen:** RK110 (1096), RK001 (116), RK009 (1), RK112 (1), Standard (12, nur Legende). Alle stehen in `config/Rohrklassen.json` (dort zusätzlich RK008/011/012/111/142/143/145/431/434). 29 Linienstile sind definiert. Alle Linien im Netz haben eine DN, außer 23434 (RK001, Dampf 2,5 bar, nicht gerechnet).
- **Systeme der Linien:** PWW-Vorlauf (643), PWW-Rücklauf (568). Dazu je 1–3 Linien Dampf, Luft und Wirklinien, die ANA nicht rechnet und als „nicht gerechnet“ meldet.
- **Kreise.json gegen Systemdefinitionen** (99 Systeme in der Zeichnung): Alle 8 Kreise mit Vorlauf/Rücklauf haben passende Systeme. Die Kürzel stimmen: PWW-VL/RL, WRG, SO, KKW, PKW, KW, EIS. Zwei Abweichungen:
  - **Thermo-Öl:** Abkürzungen „TOEVL/TOERL“ ohne Bindestrich, alle anderen haben „-VL/-RL“.
  - **Kühl-Wasser-sekundär (KW-S):** Kreis in Kreise.json, aber kein System in der Zeichnung.
  - Umgekehrt gibt es kein Vorlauf/Rücklauf-System ohne Kreis.
- Medium: Die Zeichnung trägt an 01HNS01 bzw. 23HWT01 „Antifrogen-N 25 %“ als Wahl. Kreise.json sagt für PWW „Wasser“. ANA meldet das, und seit 0.9.29 mit dem Hinweis, dass es nur bis zur Systemtrennung gilt.
- Symbole: 3 „Pfeil“ im System „Reinstdampf“, Legendensymbole im System „Standard“. Für ANA ist das ohne Wirkung.

## 4. Was ANA in einer gemeinsamen Vorlage braucht

**Stilnamen-Konvention (Vorschlag):**
1. Die Art steht vorn, als ganzes deutsches Wort mit Umlauten, ohne ß oder ae/oe/ue: „Reduzierung konzentrisch“, „Reduzierung exzentrisch“, „Druckminderer“ statt „Druckreduzierung“, „Messstutzen mit Kugelhahn“, „Volumenstromregler druckunabhängig (PICV) Motor“.
2. Funktion und Antrieb hinten: Hand, Motor, Pneumatik.
3. Geräte mit eingebautem Ventil als Gerät benennen: „Umluftkühler mit 2-Wege-Ventil“. Dann greift „Umluftkühler“ für den Verbraucher.

**Besser als Wörter, Empfehlung:** Jeder hydraulisch relevante Stil bekommt im Stil-Satz `StilSchemaSymbol` ein festes **Kurzzeichen**. In RI 9.1 ist das schon vollständig gepflegt. ANA ordnet dann nach einer **Kurzzeichen-Tabelle des Hausstandards** zu (FRE → Reduzierung, FMW → Materialwechsel, VDV/VHF → PICV …) und nutzt die Stilwörter nur als Rückfall. Das ist unabhängig von Schreibweisen und Umbenennungen. Für ANA ist das eine Erweiterung der vorhandenen Kurzzeichen-Zuordnung, gebaut nur auf Go.

**Pflicht-Anschlüsse je Bauteilart (Sicht ANA):**

| Art | Anschlüsse | Anforderung |
|---|---|---|
| Durchgangsarmatur (Ventil, Klappe, Schmutzfänger, PICV …), Formstück Reduzierung/Flansch | 2 durchgehende + 1 Mitte | Anschlüsse in Leitungsrichtung, symmetrisch zur Mitte; Linien enden am Anschluss oder in der Mitte |
| Reduzierung | 2 + 1 | **große Seite fest auf einer Seite** (heute: entgegen der Symbolrichtung) – sonst keine Prüfung „verkehrt herum“ |
| Materialwechsel | 1 (Einfügepunkt) genügt | Linie dort brechen, je Seite eigene Rohrklasse |
| 3-Wege-Ventil | 3 | Tor AB eindeutig (für Mischpunkt) |
| Messstelle, Entleerung, Manometerventil, Pfeil | 1 bzw. beliebig | sitzt am Abzweig/auf der Linie, nie im Durchfluss |
| Verbraucher | ≥ 2 (VL, RL) | Wasseranschlüsse als Anschlüsse; zusätzliche (Luft/Elektro) stören nicht |
| Pumpe, Rückschlagarmatur, Pfeil | 2 + 1 | **Fließrichtung = Symbolrichtung festlegen** (heute eingemessen: Pfeil/Rückschlag in X, Pumpe gegen X) |
| Erzeuger / Systemtrennung | 2 bzw. 4 (primär/sekundär) | Seiten eindeutig zuordenbar (ASG-Wärmetauscher erfüllt das) |
| Verteiler | n Stutzen | wie ASG-Verteiler |

**Vorlage sauber halten:** Ohne Grund gehört kein `ANA_Armatur/ArmaturArt` an Stilen ohne Funktion (Reduzierung, Pfeil, Messstelle). Ergebnisfelder (`Erg_…`) gehören in der Vorlage leer.

## Entscheidungen für den Nutzer

1. **Kurzzeichen statt Stilwörter:** Soll ANA Bauteile im Hausstandard primär über das Kurzzeichen (`KurzZeichenSymbol`) erkennen, mit einer festen Tabelle? Empfohlen. Wenn ja: Wer pflegt die Tabelle, AMK als gemeinsame Datei?
2. **Volumenstromregler (VDV/VHF):** Gelten sie im Hausstandard grundsätzlich als PICV (druckunabhängiges Regelventil) bzw. PIBV, oder als eigene Art „Volumenstromregler (konstant)“?
3. **Druckreduzierung:** Umbenennen in „Druckminderer“ und als Ventil mit Druckverlust führen? Heute rechnet ANA sie fälschlich als Formstück.
4. **Reduzierung exzentrisch:** Tippfehler im Stilnamen korrigieren. Die große Seite gleich legen wie bei „Reduzierung“, oder ANA kennt beide Lagen?
5. **Umluftkühler/-heizer mit Ventil:** Als Verbraucher führen (Gerät) und den Tippfehler „heitzer“ korrigieren?
6. **Differenzdruck-Stile:** Messung als Messstelle, „Absperrventil Differenzdruck“ als Strangabsperrventil oder Partnerventil?
7. **Nicht erkannte Armaturen** (KFE-Hahn, KFR-Ventil, Regulierventil, Ventil allgemein, Absperrorgan, Membran-/Schrägsitz-/Magnetventil, Filter, 4-/6-Wege): Welche Art soll jede bekommen?
8. **Falsche Einträge in der Basis** (21× „PICV“ an Reduzierungen, Pfeilen, Messstellen): In der Vorlage entfernen? ANA ändert in der Zeichnung des Nutzers nichts.
9. **Kreise.json:** Thermo-Öl-Kürzel auf „TOE-VL/TOE-RL“ angleichen? Kreis „Kühl-Wasser-sekundär“ behalten, obwohl die Vorlage kein System dafür hat?
10. **Medium PWW:** Im Hausstandard Wasser (Kreise.json) oder Antifrogen-N 25 % (wie an 01HNS01 gewählt)?
11. **Symbolrichtung:** Festlegen, dass bei Pumpe, Rückschlagarmatur, Pfeil und Reduzierung die Symbol-X-Richtung immer die Fließrichtung (bzw. „groß → klein“) ist, damit ANA die Prüfungen „verkehrt herum“ für alle Stile machen kann.
