# Bericht EHS 0.2: Fremd-Add-on entfernt, ein DN-Thema

Stand 23.10.2026 · erstellt von ASG mit `tools/ehs/EHS_bereinigen.ps1` (headless)

- **Quelle:** Kopie von `Schema/Versionen/EHS_0.1_leer_20261023.dwg`. Die Quelle wurde nicht verändert.
- **Ergebnis:** `C:\Temp\AMK_Vorlage\EHS_0.2\EHS_0.2.dwg`
- **Aufträge (Nutzer über AMK):** Wörterbücher des Fremd-Add-ons raus. Weitere Spuren prüfen und unbenutzte entfernen. Thema „ANA Rohr DN“ entfernen, „DN Rohrleitung“ bleibt.
- **Rohdaten:**
  - Durchgang 1: `vorher.txt`, `plan.txt`, `nachher.txt`
  - Durchgang 2: `zweiter\plan.txt`, `zweiter\nachher.txt`, AUDIT in `zweiter\lauf2\konsole.txt`

## Gegenprobe (am Ergebnis)

| Prüfung | Ergebnis |
|---|---|
| Öffnet headless ohne Fehler | ja |
| AUDIT (nur melden) | 0 Fehler gefunden, 0 behoben |
| Anzeigethemen | 9 (vorher 10), alle Satz-Zeiger intakt (ANA_Hydraulik, StilSchemaRohrKanal, AecPolygonStil) |
| „ANA Rohr DN“ | entfernt. Kein bleibendes Objekt zeigte darauf: kein Schutz, kein offener Verweis im Verweisgraphen. |
| „DN Rohrleitung“ | vorhanden |
| Symbolstile | 416 (393 mit Kürzel, 415 mit Ansichtsblock, wie vorher) |
| Systemdefinitionen | 99 |
| Satzdefinitionen | 3 (unverändert) |
| Fremde Wörterbücher im NOD | 0 (vorher 18) |
| Fehler beim Entfernen | 0 |

## Vorher und nachher

| Kategorie | EHS 0.1 | EHS 0.2 |
|---|---:|---:|
| Objekte gesamt | 18915 | 18306 |
| Anzeigethemen | 10 | 9 |
| Fremde Wörterbücher im NOD | 18 | 0 |
| RegApps | 51 | 50 |
| Symbolstile | 416 | 416 |
| Systemdefinitionen | 99 | 99 |
| Satzdefinitionen | 3 | 3 |
| Blöcke | 545 | 545 |
| Layer | 22 | 22 |
| Linientypen | 16 | 16 |
| Textstile | 12 | 12 |
| Bemaßungsstile | 3 | 3 |
| Layouts (mit Modell) | 2 | 2 |

## Was entfernt wurde

- **18 Wörterbücher des Fremd-Add-ons im NOD:**
  - 16 mit der Vorsilbe `LIN_` (Anlagen, Disciplines, Gewerke, Medien, Komponenten, Geschosse, Planarten, Verbinder …)
  - das Hauptwörterbuch des Add-ons mit 456 Einträgen
  - das Sichtbarkeits-Wörterbuch `linVisibiltyDict`, ein Objekt einer Add-on-Klasse
  - Mit ihnen gingen alle Objekte der Add-on-Klassen (lin…Record), danach war keines mehr übrig.
- **Anzeigethema „ANA Rohr DN“**, die doppelte, veraltete Kopie von „DN Rohrleitung“ (Befund ANA).
- **RegApps ohne Benutzer**, darunter die letzte RegApp des Add-ons.

## Weitere Spuren des Add-ons geprüft

- **Layer, Blöcke, Linientypen, Text- und Bemaßungsstile:** keine Namen mit LIN*, LN_* o. Ä.
- **RegApps:** nur noch eine mit dem Produktnamen, ohne Benutzer, jetzt entfernt. Die übrigen gehörten schon in EHS 0.1 nicht mehr dazu.
- **Wörterbücher:** Gesucht wurde in allen Wörterbüchern, auch den Erweiterungswörterbüchern der Stile. Außerhalb des NOD gab es keine Treffer.

## Warum zwei Durchgänge

- Auf diesem Rechner ist das Add-on mit Object-Enablern registriert (Ladesteuerung „bei Objekten der Klasse“).
- **Durchgang 1:** Die Quelle enthielt noch Objekte der Add-on-Klassen. Deshalb lud MEP die Enabler, und beim Speichern legten sie ein neues, kleines Hauptwörterbuch (7 Einträge) und drei RegApps an.
- **Durchgang 2:** Er lief auf diesem Zwischenstand, der keine Objekte der Add-on-Klassen mehr enthält. Die Enabler luden nicht mehr, und das Ergebnis blieb sauber.
- **Wichtig für den Alltag:** Öffnet man EHS 0.2 in MEP, laden die Enabler nicht, weil keine Add-on-Objekte darin sind. Fügt man aber Inhalte aus alten Zeichnungen ein, kommen Add-on-Objekte mit, die Enabler laden wieder und schreiben ihre Wörterbücher in die Zeichnung. Das ist derselbe Weg wie bei den alten Sätzen (Befund ANA zu EHS 0.1). Die Ursache stellt man in MEP ab: Wird das Add-on nicht mehr gebraucht, sollte es deinstalliert werden. Das entscheidet der Nutzer.

## Was bleibt

- **2 RegApps ohne Benutzer** (ManulPointsAssociative, ROASYM): Sie entstehen bei jedem Lauf neu, gehören nicht zum Add-on und sind harmlos.
- Alles Übrige wie in EHS 0.1: 3 Satzdefinitionen wegen der Themen-Zeiger, Planlayout, Symbolstile, Systeme, Verbinderstile.

## Wiederholen

```
powershell -File tools\ehs\EHS_bereinigen.ps1 -Quelle <EHS_0.1_leer_…dwg> -Arbeit C:\Temp\AMK_Vorlage\EHS_0.2 -Ergebnis EHS_0.2.dwg -FremdeWoerterbuecher LIN_,liN,linV -Themen 'ANA Rohr DN'
powershell -File tools\ehs\EHS_bereinigen.ps1 -Quelle C:\Temp\AMK_Vorlage\EHS_0.2\EHS_0.2.dwg -Arbeit C:\Temp\AMK_Vorlage\EHS_0.2\zweiter -Ergebnis EHS_0.2.dwg -FremdeWoerterbuecher LIN_,liN,linV
```

Die Fremd-Vorsilben werden nur beim Aufruf übergeben. Dabei zählt Groß- und Kleinschreibung, damit AutoCAD-Schlüssel wie LINETYPE nicht getroffen werden.
