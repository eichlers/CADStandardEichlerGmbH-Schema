# Bestandsaufnahme ASG – Eichler-Hausstandard auf Basis RI 9.1

Stand 23.10.2026. Nur gelesen: eigene Kopie der Basis `C:\Temp\AMK_Vorlage\Basis_ANA_Test_2_RI_9.1_20261023.dwg` (headless, nicht gespeichert; Rohdaten `C:\Temp\AMK_Vorlage\ASG_Lauf\inv.txt`, `themen.txt`) und die DXF-Exporte des Nutzers (`…\CAD-Vorlage fuer R+I_V9.1\SymboleVorlage_DXF`, 20 Dateien). Nichts geändert.

## Kurzfassung

- Zeichnung: 416 Schemasymbolstile. **393 davon sind Symbole des Nutzers** (Block gleichen Namens in seinen DXF-Exporten), 23 stehen nur in der Zeichnung (darunter 3 ASG-Stile). 21 Stile sind eingesetzt.
- DXF: 475 Blöcke, **76 ohne Schemasymbolstil** in der Zeichnung (u. a. ganze Gruppen Sammler-Verteiler, Strang-Symbole, große Teile von Elektro).
- Unter den Symbolen des Nutzers: 127 mit nur 1 Anschluss, 47 mit Einfügepunkt nicht auf einem Anschluss.
- **Kürzel:** Kein Stil trägt ein Kürzel. Am Stil hängt nur der Satz „StilSchemaSymbol“ mit `BeschreibungBauteil`; an eingesetzten Symbolen steht das Kürzel nur als Teil der Positionsnummer im Satz „TAGBauteil“ (`PosNr=01PUM02` → PUM). Ein Feld `KurzZeichenSymbol` gibt es in der Zeichnung nicht.
- 99 Schemasystemdefinitionen, alle mit LabelName (Kürzel). 10 Anzeigethemen, davon färben 2 nach System (Medien, Stoffgruppen).

## 1. Schemasymbolstile des Nutzers (Abgleich mit seinen DXF-Exporten)

Zuordnung: DXF-Blockname = Stilname (ohne Groß/klein, Umlaute/Leerzeichen/Bindestriche gleichgesetzt). Einfügepunkt = (0,0) im Stil. Anschlüsse: Lage relativ zum Einfügepunkt, Richtung, Name (Beschreibung). Grafik = Inhalt der Ansichtsblöcke (Farbe/Linienstärke: ByLayer, ByBlock oder fest).

| Gruppe (DXF) | Stil | Beschreibung | Anschl. | Lage/Richtung der Anschlüsse | EP auf Anschluss | Farbe | Linienstärke | Layer | Ansichten | eingesetzt |
|---|---|---|---|---|---|---|---|---|---|---|
| Antriebe | Antrieb 2-stufig | Antrieb 2-stufig, schaltet den Antrieb in zwei Stufen | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Antriebe | Antrieb-Gewicht | Antrieb-Gewicht, stellt die Armatur über ein Hebelgewicht | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Antriebe | Antrieb-Hydraulik | Antrieb-Hydraulik, stellt die Armatur hydraulisch | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Antriebe | Antrieb-Membran | Antrieb-Membran, stellt die Armatur über eine Steuerdruckmembran | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Antriebe | Dehungsantrieb | Dehnstoffantrieb, stellt die Armatur über einen Dehnstoff temperaturabhängig | 1 | (0, 0)→(0, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Antriebe | Feder-Antrieb | Feder-Antrieb, stellt die Armatur über eine vorgespannte Feder | 1 | (0, 0)→(0, 0) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Antriebe | Frequenzumrichter | Frequenzumrichter, regelt die Drehzahl stufenlos | 5 | (0, 0)→(0, 0); (100, 0)→(1, 0); (-100, 0)→(-1, 0); (0, 100)→(0, 1); (0, -100)→(0, -1) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Antriebe | Hubbegrenzung | Hubbegrenzung, begrenzt den Stellweg der Armatur | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Antriebe | Magnetantrieb | Magnetantrieb, schaltet die Armatur elektromagnetisch | 1 | (0, 0)→(0, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Antriebe | Motorantrieb | Motorantrieb, stellt die Armatur elektromotorisch | 4 | (100, 0)→(100, 0); (-100, 0)→(-100, 0); (0, 100)→(0, 100); (0, -100)→(0, -100) | nein | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Antriebe | Plombierung | Plombierung, sichert die Armatur gegen unbefugtes Verstellen | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Antriebe | schließt bei Ausfall der Hilfsenergie | Antrieb schließt die Armatur bei Ausfall der Hilfsenergie | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Antriebe | Stellungsregler | Stellungsregler, führt den Antrieb auf die vorgegebene Stellung | 4 | (0, 0)→(0, 0); (0, 50)→(0, 1); (65, 0)→(1, 0); (0, -50)→(0, -1) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Antriebe | öffnet bei Ausfall der Hilfsenergie | Antrieb öffnet die Armatur bei Ausfall der Hilfsenergie | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Armaturen | 2-Wege Regelventil | 2-Wege Regelventil, stellt den Durchfluss stufenlos | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×3 | ByLineWeightDefault×3 | 0×3 | 1 | – |
| Armaturen | 2-Wege Regelventil Motor | 2-Wege Regelventil mit Motorantrieb, stellt den Durchfluss stufenlos | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 230)→(0, 1) | ja | ByLayer×5 | ByLineWeightDefault×3, ByLayer×2 | 0×5 | 1 | – |
| Armaturen | 2-Wege Regelventil Pneumatik | 2-Wege Regelventil mit pneumatischem Antrieb, stellt den Durchfluss stufenlos | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 268)→(0, 1) | ja | ByLayer×6 | ByLineWeightDefault×3, ByLayer×3 | 0×6 | 1 | – |
| Armaturen | 3-Wege Kugelhahn Kolbenantrieb | 3-Wege Kugelhahn mit Kolbenantrieb, lenkt den Strom über eine gebohrte Kugel auf | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -150)→(0, -1); (0, 305)→(0, 1) | ja | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Armaturen | 3-Wege Mischventil Hand | 3-Wege Mischventil mit Handantrieb, stellt den Durchfluss stufenlos | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByLineWeightDefault×5, ByLayer×2 | 0×7 | 1 | – |
| Armaturen | 3-Wege Regelventil | 3-Wege Regelventil, stellt den Durchfluss stufenlos | 4 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, -150)→(0, 0); (0, 0)→(0, 0) | ja | ByLayer×5 | ByLineWeightDefault×5 | 0×5 | 1 | – |
| Armaturen | 3-Wege Regelventil Motor | 3-Wege Regelventil mit Motorantrieb, stellt den Durchfluss stufenlos | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 230)→(0, 1) | ja | ByLayer×7 | ByLineWeightDefault×5, ByLayer×2 | 0×7 | 1 | – |
| Armaturen | 3-Wege Regelventil Pneumatik | 3-Wege Regelventil mit pneumatischem Antrieb, stellt den Durchfluss stufenlos | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -150)→(0, -1) | ja | ByLayer×8 | ByLineWeightDefault×5, ByLayer×3 | 0×8 | 1 | – |
| Armaturen | 3-Wege Umschalthahn | 3-Wege Umschalthahn, lenkt den Strom über eine gebohrte Kugel auf einen anderen  | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -150)→(0, -1); (0, 30)→(0, 1) | ja | ByLayer×5 | LineWeight035×4, ByLineWeightDefault×1 | 0×5 | 1 | – |
| Armaturen | 3-Wege Umschalthahn Hand | 3-Wege Umschalthahn mit Handantrieb, lenkt den Strom über eine gebohrte Kugel au | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -150)→(0, -1) | ja | ByLayer×7 | LineWeight035×4, ByLayer×2, ByLineWeightDefault×1 | 0×7 | 1 | – |
| Armaturen | 3-Wege Umschaltventil | 3-Wege Umschaltventil, lenkt den Strom auf einen anderen Weg | 4 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, -150)→(0, 0); (0, 0)→(0, 0) | ja | ByLayer×2 | LineWeight035×2 | 0×2 | 1 | – |
| Armaturen | 3-Wege Umschaltventil Hand | 3-Wege Umschaltventil mit Handantrieb, lenkt den Strom auf einen anderen Weg | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -150)→(0, -1) | ja | ByLayer×4 | LineWeight035×2, ByLayer×2 | 0×4 | 1 | – |
| Armaturen | 3-Wege Umschaltventil Pneumatik | 3-Wege Umschaltventil mit pneumatischem Antrieb, lenkt den Strom auf einen ander | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -150)→(0, -1); (0, 268)→(0, 1) | ja | ByLayer×5 | ByLayer×3, LineWeight035×2 | 0×5 | 1 | – |
| Armaturen | 4-Wege Umschalthahn | 4-Wege Umschalthahn, lenkt den Strom über eine gebohrte Kugel auf einen anderen  | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×6 | LineWeight035×5, ByLineWeightDefault×1 | 0×6 | 1 | – |
| Armaturen | 4-Wege Umschaltventil | 4-Wege Umschaltventil, lenkt den Strom auf einen anderen Weg | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×3 | LineWeight035×3 | 0×3 | 1 | – |
| Armaturen | 6-Wege Umschaltventil Motor | 6-Wege Umschaltventil mit Motorantrieb, lenkt den Strom auf einen anderen Weg | 9 | (0, 0)→(0, 0); (150, 140)→(1, 0); (-150, -140)→(-1, 0); (150, -140)→(1, 0); (-150, 140)→(-1, 0); (0, 290)→(0, 1); (0, -290)→(0, -1); (100, 0)→(1, 0); (-100, 0)→ | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Armaturen | Abscheider | Abscheider, trennt Fremdstoffe aus dem Medium | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -150)→(0, -1); (0, 150)→(0, 1) | ja | ByLayer×6 | ByLineWeightDefault×4, ByLayer×2 | 0×6 | 1 | – |
| Armaturen | Abscheider Magnet | Abscheider Magnet, trennt Fremdstoffe aus dem Medium | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -187.5)→(0, -1); (0, 112.5)→(0, 1) | ja | ByLayer×11 | ByLayer×6, ByLineWeightDefault×5 | 0×11 | 1 | – |
| Armaturen | Absperrklappe | Absperrklappe, sperrt den Durchfluss über eine drehbare Scheibe ab | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×6 | ByLineWeightDefault×5, LineWeight015×1 | 0×6 | 1 | 3 |
| Armaturen | Absperrklappe Motor | Absperrklappe mit Motorantrieb, sperrt den Durchfluss über eine drehbare Scheibe | 6 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 274.6)→(0, 1); (-100, 175)→(-1, 0); (100, 175)→(1, 0) | ja | ByLayer×8 | ByLineWeightDefault×5, ByLayer×2, LineWeight015×1 | 0×8 | 1 | – |
| Armaturen | Absperrklappe-Hand | Absperrklappe-Hand, sperrt den Durchfluss über eine drehbare Scheibe ab | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×8 | ByLineWeightDefault×5, ByLayer×2, LineWeight015×1 | 0×8 | 1 | – |
| Armaturen | Absperrklappe-Pneumatik | Absperrklappe-Pneumatik, sperrt den Durchfluss über eine drehbare Scheibe ab | 3 | (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 0)→(0, 0) | ja | ByLayer×9 | ByLineWeightDefault×5, ByLayer×3, LineWeight015×1 | 0×9 | 1 | – |
| Armaturen | Absperrorgan Allgemein | Absperrorgan, allgemeine Darstellung, sperrt den Durchfluss ab | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×1 | ByLineWeightDefault×1 | 0×1 | 1 | – |
| Armaturen | Absperrorgan Allgemein Hand | Absperrorgan Allgemein mit Handantrieb, sperrt den Durchfluss ab | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×3 | ByLayer×2, ByLineWeightDefault×1 | 0×3 | 1 | – |
| Armaturen | Absperrorgan Allgemein Kolbenantrieb | Absperrorgan Allgemein mit Kolbenantrieb, sperrt den Durchfluss ab | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 305)→(0, 1) | ja | ByLayer×7 | ByLayer×6, ByLineWeightDefault×1 | 0×7 | 1 | – |
| Armaturen | Absperrorgan Allgemein Pneumatik | Absperrorgan Allgemein mit pneumatischem Antrieb, sperrt den Durchfluss ab | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×4 | ByLayer×3, ByLineWeightDefault×1 | 0×4 | 1 | – |
| Armaturen | Absperrschieber | Absperrschieber, sperrt den Durchfluss über eine quer fahrende Platte ab | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×5 | ByLineWeightDefault×5 | 0×5 | 1 | – |
| Armaturen | Absperrventil Differenzdruck | Absperrventil Differenzdruck, sperrt den Durchfluss über einen geradlinig bewegt | 5 | (0, 0)→(0, 0); (75, 150)→(0, 1); (-75, 150)→(0, 1); (-75, -150)→(0, -1); (75, -150)→(0, -1) | ja | ByLayer×10 | ByLineWeightDefault×6, ByLayer×4 | 0×10 | 1 | – |
| Armaturen | Absperrventil Differenzdruck mit Prüfanschluss | Absperrventil Differenzdruck mit Prüfanschluss, sperrt den Durchfluss über einen | 7 | (0, 0)→(0, 0); (75, 150)→(0, 1); (-75, 150)→(0, 1); (-75, -150)→(0, -1); (75, -150)→(0, -1); (325, 150)→(1, 0); (-325, 150)→(-1, 0) | ja | ByLayer×24 | ByLineWeightDefault×14, ByLayer×10 | 0×24 | 1 | – |
| Armaturen | Absperrventil mit Prüfanschluss | Absperrventil mit Prüfanschluss, sperrt den Durchfluss über einen geradlinig bew | 4 | (0, 0)→(0, 0); (0, 150)→(0, 1); (0, -150)→(0, -1); (-250, 150)→(-1, 0) | ja | ByLayer×13 | ByLineWeightDefault×8, ByLayer×5 | 0×13 | 1 | – |
| Armaturen | Automatische Entlüftung | Automatische Entlüftung, lässt Luft aus der Leitung entweichen | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | LineWeight015×4, ByLineWeightDefault×1 | 0×5 | 1 | – |
| Armaturen | Berstscheibe | Berstscheibe, öffnet bei Überdruck bleibend und gibt den Querschnitt frei | 5 | (0, 0)→(0, 0); (0, 75)→(0, 1); (0, -75)→(0, -1); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×5 | ByLineWeightDefault×4, ByLayer×1 | 0×5 | 1 | – |
| Armaturen | Diffusor | Diffusor, verzögert die Strömung und wandelt Geschwindigkeit in Druck | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×6 | ByLayer×5, LineWeight035×1 | 0×6 | 1 | – |
| Armaturen | Druckreduzierung | Druckreduzierung, hält den Ausgangsdruck unabhängig vom Eingangsdruck konstant | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×4 | ByLineWeightDefault×4 | 0×4 | 1 | – |
| Armaturen | Düse | Düse, erzeugt einen definierten Strahl oder Druckverlust | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(1, 0) | ja | ByLayer×6 | ByLayer×5, LineWeight035×1 | 0×6 | 1 | – |
| Armaturen | Entleerung | Entleerung, entleert die Leitung am Tiefpunkt | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | LineWeight015×3, ByLineWeightDefault×1 | 0×4 | 1 | – |
| Armaturen | Entlüftung | Entlüftung, lässt Luft aus der Leitung entweichen | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | LineWeight015×2, ByLineWeightDefault×1 | 0×3 | 1 | – |
| Armaturen | Entlüftungsgefäss | Entlüftungsgefäss, sammelt die Luft an der Hochstelle zur Entlüftung | 5 | (0, 0)→(0, 0); (0, 200)→(0, 1); (75, 0)→(1, 0); (0, -200)→(0, -1); (-75, 0)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Armaturen | Feinfilter | Feinfilter, hält Feststoffe aus dem Medium zurück | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×6 | ByLayer×5, LineWeight035×1 | 0×6 | 1 | – |
| Armaturen | Filter | Filter, hält Feststoffe aus dem Medium zurück | 5 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 75)→(0, 1); (0, -75)→(0, -1); (0, 0)→(0, 0) | ja | ByLayer×2 | LineWeight035×1, ByLayer×1 | 0×2 | 1 | – |
| Armaturen | Filter-Überwachung | Filter-Überwachung, überwacht den Druck und meldet bei Über- oder Unterschreiten | 6 | (0, 0)→(0, 0); (-325, -320)→(0, -1); (325, -320)→(0, -1); (-625, 0)→(-1, 0); (625, 0)→(1, 0); (0, 400)→(0, 1) | ja | ByLayer×44 | ByLayer×40, ByLineWeightDefault×4 | 0×44 | 1 | – |
| Armaturen | Hygiene Anschluss | Hygiene Anschluss, totraumfreier Anschluss für Reinstmedien | 2 | (0, 0)→(0, 0); (0, -25)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Armaturen | Hygiene Gehäuse Durchgang | Hygiene Gehäuse Durchgang, totraumfreies Einbauteil zur Aufnahme von Sensoren | 5 | (0, 0)→(0, 0); (112.5, 0)→(1, 0); (-112.5, 0)→(-1, 0); (0, 112.5)→(0, 1); (0, -112.5)→(0, -1) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Armaturen | Hygiene Gehäuse Eck | Hygiene Gehäuse Eck, totraumfreies Einbauteil zur Aufnahme von Sensoren | 4 | (0, 0)→(0, 0); (-112.5, 0)→(-1, 0); (0, -112.5)→(0, -1); (0, 112.5)→(0, 1) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Armaturen | Kappenventil | Kappenventil, sperrt den Durchfluss über einen geradlinig bewegten Kegel ab | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×5 | LineWeight015×3, LineWeight035×2 | 0×5 | 1 | – |
| Armaturen | KFE-Hahn | KFE-Hahn, entleert die Leitung am Tiefpunkt | 3 | (0, 0)→(0, 0); (75, 0)→(1, 0); (-75, 0)→(-1, 0) | ja | ByLayer×3 | ByLineWeightDefault×3 | 0×3 | 1 | 1 |
| Armaturen | KFR-Ventil | KFR-Ventil, absperrbarer Rückflussverhinderer in Schrägsitzform nach DIN 1988-10 | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×4 | ByLayer×3, ByLineWeightDefault×1 | 0×4 | 1 | – |
| Armaturen | Kondensatableiter | Kondensatableiter, lässt Kondensat ab und hält den Dampf zurück | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×3 | ByLineWeightDefault×3 | 0×3 | 1 | – |
| Armaturen | Kugelhahn | Kugelhahn, sperrt den Durchfluss über eine gebohrte Kugel ab | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×3 | ByLineWeightDefault×3 | 0×3 | 1 | 2 |
| Armaturen | Kugelhahn Hand | Kugelhahn mit Handantrieb, sperrt den Durchfluss über eine gebohrte Kugel ab | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Armaturen | Kugelhahn Kolbenantrieb | Kugelhahn mit Kolbenantrieb, sperrt den Durchfluss über eine gebohrte Kugel ab | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 305)→(0, 1) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Armaturen | Kugelhahn Motor | Kugelhahn mit Motorantrieb, sperrt den Durchfluss über eine gebohrte Kugel ab | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 230)→(0, 1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Armaturen | Kugelhahn Pneumatik | Kugelhahn mit pneumatischem Antrieb, sperrt den Durchfluss über eine gebohrte Ku | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Armaturen | Magnetventil | Magnetventil, sperrt den Durchfluss über einen geradlinig bewegten Kegel ab | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 230)→(0, 1) | ja | ByLayer×10 | ByLayer×6, ByLineWeightDefault×4 | 0×10 | 1 | – |
| Armaturen | Membranventil | Membranventil, sperrt den Durchfluss über eine Membran totraumfrei ab | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×2 | ByLineWeightDefault×1, ByLayer×1 | 0×2 | 1 | – |
| Armaturen | Membranventil Motor | Membranventil mit Motorantrieb, sperrt den Durchfluss über eine Membran totraumf | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×5 | ByLayer×4, ByLineWeightDefault×1 | 0×5 | 1 | – |
| Armaturen | Membranventil-Hand | Membranventil-Hand, sperrt den Durchfluss über eine Membran totraumfrei ab | 3 | (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×3, ByLineWeightDefault×1 | 0×4 | 1 | – |
| Armaturen | Membranventil-Kolbenantrieb | Membranventil-Kolbenantrieb, sperrt den Durchfluss über eine Membran totraumfrei | 4 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 310)→(0, 1) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Armaturen | Membranventil-Pneumatik | Membranventil-Pneumatik, sperrt den Durchfluss über eine Membran totraumfrei ab | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×5 | ByLayer×4, ByLineWeightDefault×1 | 0×5 | 1 | – |
| Armaturen | Nadelventil | Nadelventil, drosselt kleine Durchflüsse feinfühlig | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Armaturen | Phasentrenner | Phasentrenner, trennt zwei nicht mischbare Phasen | 4 | (0, 0)→(0, 0); (0, 200)→(0, 1); (100, 0)→(1, 0); (0, -200)→(0, -1) | ja | ByLayer×19 | ByLayer×19 | 0×19 | 1 | – |
| Armaturen | Prüfkammer | Prüfkammer, Einbauort für Probenahme oder Prüfung | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Armaturen | Regel-Kugelhahn Motor | Regel-Kugelhahn mit Motorantrieb, regelt den Durchfluss über eine profilierte Ku | 3 | (0, 0)→(0, 0); (-150, 0)→(-1, 0); (150, 0)→(1, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Armaturen | Regulierventil | Regulierventil, stellt den Strang auf den geplanten Volumenstrom ein | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×5 | ByLineWeightDefault×3, LineWeight015×2 | 0×5 | 1 | – |
| Armaturen | Rohrtrenner | Rohrtrenner, lässt das Medium nur in eine Richtung durch | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×8 | LineWeight035×4, ByLayer×4 | 0×8 | 1 | – |
| Armaturen | Rückflussverhinderer | Rückflussverhinderer, lässt das Medium nur in eine Richtung durch | 3 | (75, 0)→(75, 0); (-75, 0)→(-75, 0); (0, 0)→(0, 0) | ja | ByLayer×3 | ByLineWeightDefault×3 | 0×3 | 1 | – |
| Armaturen | Rückschlagklappe | Rückschlagklappe, verhindert den Rückfluss über eine schwenkende Klappe | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×6 | ByLineWeightDefault×5, LineWeight015×1 | 0×6 | 1 | 4 |
| Armaturen | Rückschlagventil | Rückschlagventil, lässt das Medium nur in eine Richtung durch | 2 | (150, 0)→(1, 0); (-150, 0)→(-1, 0) | nein | ByLayer×2 | ByLineWeightDefault×2 | 0×2 | 1 | – |
| Armaturen | Rückspülfilter | Rückspülfilter, hält Feststoffe aus dem Medium zurück | 4 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, -125)→(0, 0); (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×2, LineWeight035×1 | 0×3 | 1 | – |
| Armaturen | Schauglas | Schauglas, erlaubt die Sichtkontrolle des Mediums | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×5 | LineWeight035×5 | 0×5 | 1 | – |
| Armaturen | Schmutzfänger | Schmutzfänger, hält Feststoffe aus dem Medium zurück | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×2 | LineWeight035×2 | 0×2 | 1 | – |
| Armaturen | Schrägsitzventil-Hand | Schrägsitzventil-Hand, sperrt den Durchfluss über einen geradlinig bewegten Kege | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×3 | ByLayer×2, ByLineWeightDefault×1 | 0×3 | 1 | – |
| Armaturen | Schrägsitzventil-Pneumatik | Schrägsitzventil-Pneumatik, sperrt den Durchfluss über einen geradlinig bewegten | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×4 | ByLayer×3, ByLineWeightDefault×1 | 0×4 | 1 | – |
| Armaturen | Serviceventil |  | 3 | (0, 0)→(0, 0); (250, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×7 | ByLayer×4, ByLineWeightDefault×3 | 0×7 | 1 | – |
| Armaturen | Sicherheitsventil Eckform | Sicherheitsventil Eckform, bläst bei Überdruck ab und schließt wieder | 3 | (150, 0)→(1, 0); (0, -150)→(0, -1); (0, 0)→(0, 0) | ja | ByLayer×4 | ByLineWeightDefault×4 | 0×4 | 1 | – |
| Armaturen | Sicherheitsventil Eckform Feder | Sicherheitsventil Eckform Feder, bläst bei Überdruck ab und schließt wieder | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (0, -150)→(0, -1) | ja | ByLayer×12 | ByLayer×8, ByLineWeightDefault×4 | 0×12 | 1 | – |
| Armaturen | Sprühkugel | Sprühkugel, reinigt den Behälter im CIP-Verfahren | 1 | (0, 0)→(0, 0) | ja | ByLayer×9 | ByLayer×8, ByLineWeightDefault×1 | 0×9 | 1 | – |
| Armaturen | Strahlpumpe Motor | Strahlpumpe mit Motorantrieb, fördert über einen Treibstrahl ohne bewegte Teile | 7 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 300)→(0, 1); (0, -230)→(0, -1); (100, -130)→(1, 0); (-100, -130)→(-1, 0) | ja | ByLayer×9 | ByLineWeightDefault×7, ByLayer×2 | 0×9 | 1 | – |
| Armaturen | Vakuumbrecher | Vakuumbrecher, belüftet die Leitung und verhindert Unterdruck | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Armaturen | Verschneide-Armatur | Verschneide-Armatur, stellt den Strang auf den geplanten Volumenstrom ein | 5 | (0, 0)→(0, 0); (-150, 0)→(-1, 0); (150, 0)→(1, 0); (-65, -75)→(0, -1); (65, -75)→(0, -1) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Armaturen | Volumenstromregler Einstellbar | Volumenstromregler Einstellbar, hält den Volumenstrom ohne Hilfsenergie konstant | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×18 | ByLineWeightDefault×16, LineWeight015×2 | 0×18 | 1 | 28 |
| Armaturen | Volumenstromregler Einstellbar Motor | Volumenstromregler Einstellbar mit Motorantrieb, stellt den Durchfluss stufenlos | 6 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, -275)→(0, -1); (-100, -175)→(-1, 0); (100, -175)→(1, 0) | ja | ByLayer×20 | ByLineWeightDefault×16, LineWeight015×2, ByLayer×2 | 0×20 | 1 | 282 |
| Armaturen | Volumenstromregler Festwert | Volumenstromregler Festwert, hält den Volumenstrom ohne Hilfsenergie konstant | 3 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 0)→(0, 0) | ja | ByLayer×16 | ByLineWeightDefault×16 | 0×16 | 1 | – |
| Armaturen | Wechselventil Hand | Wechselventil mit Handantrieb, lenkt den Strom auf einen anderen Weg | 3 | (0, 0)→(0, -1); (200, 150)→(0, 1); (-200, 150)→(0, 1) | ja | ByLayer×15 | ByLineWeightDefault×12, ByLayer×3 | 0×15 | 1 | – |
| Armaturen | Ölspiegelregulator | ÖR | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×15 | ByLayer×15 | 0×15 | 1 | – |
| Armaturen | Überströmventil | Überströmventil, gibt bei Überdruck einen Bypass frei | 3 | (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 0)→(0, 0) | ja | ByLayer×3 | ByLineWeightDefault×3 | 0×3 | 1 | – |
| Armaturen | Überströmventil Feder | Überströmventil Feder, gibt bei Überdruck einen Bypass frei | 2 | (150, 0)→(1, 0); (-150, 0)→(-1, 0) | nein | ByLayer×11 | ByLayer×8, ByLineWeightDefault×3 | 0×11 | 1 | – |
| Behälter | Behälter | Behälter, speichert oder bevorratet das Medium | 6 | (-460, 650)→(0, 0); (-460, -650)→(0, 0); (0, 930)→(-460, 0); (0, -930)→(460, 0); (460, 650)→(0, 0); (460, -650)→(0, 0) | nein | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Behälter | Behälter rechteckig | Behälter rechteckig, speichert oder bevorratet das Medium | 4 | (0, 0)→(0, 0); (1750, 0)→(1, 0); (-1750, 0)→(-1, 0); (0, 1000)→(0, 1) | ja | ByLayer×1 | ByLayer×1 | 0×1 | 1 | – |
| Behälter | MAG Grösse 1 | MAG Größe 1, nimmt die Volumenänderung des Heiz- oder Kühlwassers auf | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Behälter | MAG Grösse 2 | MAG Größe 2, nimmt die Volumenänderung des Heiz- oder Kühlwassers auf | 6 | (360, 200)→(0, 0); (-360, -200)→(0, 0); (-360, 200)→(0, 0); (360, -200)→(0, 0); (0, 440)→(440, 0); (0, -420)→(-420, 0) | nein | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Behälter | MAG Grösse 3 | MAG Größe 3, nimmt die Volumenänderung des Heiz- oder Kühlwassers auf | 6 | (460, 450)→(0, 0); (460, -450)→(0, 0); (-460, -450)→(0, 0); (-460, 450)→(0, 0); (0, 680)→(680, 0); (0, -680)→(-680, 0) | nein | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Behälter | Mannloch | Mannloch, Einstiegsöffnung am Behälter | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Behälter | Pufferspeicher | Pufferspeicher, speichert oder bevorratet das Medium | 6 | (460, 650)→(0, 0); (460, -650)→(0, 0); (-460, -650)→(0, 0); (-460, 650)→(0, 0); (0, 930)→(460, 0); (0, -930)→(-460, 0) | nein | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Behälter | Pufferspeicher mit Wärmetauscher | Pufferspeicher mit Wärmetauscher, speichert oder bevorratet das Medium | 8 | (460, 650)→(0, 0); (460, -650)→(0, 0); (-460, -650)→(0, 0); (-460, 650)→(0, 0); (0, 930)→(460, 0); (0, -930)→(-460, 0); (580, 250)→(0, 0); (580, -250)→(0, 0) | nein | ByLayer×13 | ByLayer×13 | 0×13 | 1 | – |
| Behälter | Schauglas Behälter | Schauglas Behälter, erlaubt die Sichtkontrolle des Mediums | 1 | (0, 0)→(0, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Behälter | Speicher Wasser Erwärmer Bivalent | Speicher Wasser Erwärmer Bivalent, erwärmt und speichert das Trinkwasser | 8 | (0, 930)→(460, 0); (0, -930)→(-460, 0); (460, 650)→(0, 0); (580, -650)→(0, 0); (-460, -650)→(0, 0); (580, -150)→(0, 0); (-580, 650)→(0, 0); (-580, 150)→(0, 0) | nein | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Behälter | Speicher Wasser Erwärmer Monovalent | Speicher Wasser Erwärmer Monovalent, erwärmt und speichert das Trinkwasser | 7 | (460, 650)→(0, 0); (580, -650)→(0, 0); (-460, -650)→(0, 0); (0, 930)→(460, 0); (0, -930)→(-460, 0); (580, -150)→(0, 0); (-460, 650)→(0, 0) | nein | ByLayer×13 | ByLayer×13 | 0×13 | 1 | – |
| Behälter | Tank-liegend | Tank-liegend, speichert oder bevorratet das Medium | 1 | (0, 0)→(0, 0) | ja | ByLayer×140 | ByLayer×140 | 0×140 | 1 | – |
| Behälter | Tank-liegend-gedämmt | Tank-liegend-gedämmt, speichert oder bevorratet das Medium | 1 | (0, 0)→(0, 0) | ja | ByLayer×238 | ByLayer×238 | 0×238 | 1 | – |
| Behälter | Tank-stehend | Tank-stehend, speichert oder bevorratet das Medium | 1 | (0, 0)→(0, 0) | ja | ByLayer×133 | ByLayer×133 | 0×133 | 1 | – |
| Behälter | Tank-stehend-gedämmt | Tank-stehend-gedämmt, speichert oder bevorratet das Medium | 1 | (0, 0)→(0, 0) | ja | ByLayer×107 | ByLayer×107 | 0×107 | 1 | – |
| Behälter | Tank-stehend-Temperiermantel | Tank-stehend-Temperiermantel, speichert oder bevorratet das Medium | 1 | (0, 0)→(0, 0) | ja | ByLayer×34 | ByLayer×34 | 0×34 | 1 | – |
| Behälter | Vorschaltgefäss | Vorschaltgefäß, schützt das Ausdehnungsgefäß vor zu hoher Temperatur | 6 | (460, 450)→(0, 0); (460, -450)→(0, 0); (-460, -450)→(0, 0); (-460, 450)→(0, 0); (0, 680)→(680, 0); (0, -680)→(-680, 0) | nein | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Brandschott | Brandschott L120 | Brandschott L120, verschließt die Wand- oder Deckendurchführung im Brandfall | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByLayer×5, ByLineWeightDefault×2 | 0×7 | 1 | – |
| Brandschott | Brandschott L30 | Brandschott L30, verschließt die Wand- oder Deckendurchführung im Brandfall | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByLayer×5, ByLineWeightDefault×2 | 0×7 | 1 | – |
| Brandschott | Brandschott L90 | Brandschott L90, verschließt die Wand- oder Deckendurchführung im Brandfall | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByLayer×5, ByLineWeightDefault×2 | 0×7 | 1 | – |
| Datenpunkte | Datenpunkt Feldbus | Datenpunkt Feldbus, Datenpunkt der Feldbusebene | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Datenpunkte | Datenpunkt Fremd | Datenpunkt Fremd, Datenpunkt einer fremden Anlage | 5 | (0, 0)→(0, 0); (25, 0)→(1, 0); (-25, 0)→(-1, 0); (0, 25)→(0, 1); (0, -25)→(0, 1) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Datenpunkte | Datenpunkt Gebäudeautomation | Datenpunkt Gebäudeautomation, Datenpunkt der Gebäudeautomation | 5 | (0, 0)→(0, 0); (25, 0)→(1, 0); (-25, 0)→(-1, 0); (0, 25)→(0, 1); (0, -25)→(0, -1) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | 1 |
| Datenpunkte | Datenpunkt Monitoring System | Datenpunkt Monitoring System, Datenpunkt des Monitoringsystems | 5 | (0, 0)→(0, 0); (25, 0)→(1, 0); (-25, 0)→(-1, 0); (0, 25)→(0, 1); (0, -25)→(0, -1) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | 1 |
| Datenpunkte | Datenpunkt Prozess | Datenpunkt Prozess, Datenpunkt der Prozessleittechnik | 5 | (0, 0)→(0, 0); (25, 0)→(1, 0); (-25, 0)→(-1, 0); (0, 25)→(0, 1); (0, -25)→(0, -1) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | 3 |
| Elektro | Antennendose | AD | 2 | (0, 1)→(0, 1); (0, -150)→(0, -1) | nein | ByLayer×7 | ByLayer×6, ByLineWeightDefault×1 | 0×7 | 1 | – |
| Elektro | Bewegunsgmelder |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Elektro | Deckenleuchte |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×2, ByLineWeightDefault×1 | 0×3 | 1 | – |
| Elektro | Gegensprechanlage |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Elektro | Netzwerkdose |  | 2 | (0, 0)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×6 | ByLayer×5, ByLineWeightDefault×1 | 0×6 | 1 | – |
| Elektro | Rauchmelder | RM | 3 | (0, 0)→(0, 0); (75, 0)→(1, 0); (-75, 0)→(-1, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Elektro | Schalter | S | 5 | (0, 0)→(0, 0); (0, 25)→(0, 1); (0, -25)→(0, -1); (-25, 0)→(-1, 0); (25, 0)→(1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Elektro | Schalter mit Kontrollleuchte | S | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Elektro | Steckdose 2-fach mit Schutzkontakt |  | 3 | (0, 0)→(0, 0); (0, 1)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×5 | ByLayer×4, ByLineWeightDefault×1 | 0×5 | 1 | – |
| Elektro | Steckdose 3-fach mit Schutzkontakt |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×4, ByLineWeightDefault×1 | 0×5 | 1 | – |
| Elektro | Steckdose 4-fach mit Schutzkontakt |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×4, ByLineWeightDefault×1 | 0×5 | 1 | – |
| Elektro | Steckdose 5-fach mit Schutzkontakt |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×4, ByLineWeightDefault×1 | 0×5 | 1 | – |
| Elektro | Steckdose mit Schutzkontakt |  | 2 | (0, 1)→(0, 1); (0, -150)→(0, -1) | nein | ByLayer×3 | ByLayer×2, ByLineWeightDefault×1 | 0×3 | 1 | – |
| Elektro | Telefondose |  | 2 | (0, 1)→(0, 1); (0, -150)→(0, -1) | nein | ByLayer×4 | ByLayer×3, ByLineWeightDefault×1 | 0×4 | 1 | – |
| Elektro | Wandleuchte | WL | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×3, ByLineWeightDefault×1 | 0×4 | 1 | – |
| Heizkörper | Heiz-Kühldecke Anschluss-Oben | Heiz-Kühldecke, Anschluss oben, gibt Wärme oder Kälte über die Deckenfläche ab | 3 | (0, 0)→(0, 0); (715.5, 150.6)→(0, 1); (-715.5, 150.6)→(0, 1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Konvektor-Heizkörper Anschluss-Links | Konvektor-Heizkörper, Anschluss links, gibt Wärme an den Raum ab | 1 | (0, 0)→(0, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Heizkörper | Plan-Heizkörper Anschluss Rechts | Plan-Heizkörper, Anschluss rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (825, 425)→(1, 0); (825, -425)→(1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Plan-Heizkörper Anschluss Unten | Plan-Heizkörper, Anschluss unten, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (665.7, -575)→(0, -1); (-665.7, -575)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Plan-Heizkörper Anschluss Unten Links | Plan-Heizkörper, Anschluss unten links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-515.7, -575)→(0, -1); (-665.7, -575)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Plan-Heizkörper Anschluss Unten Mitte | Plan-Heizkörper, Anschluss unten mitte, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (75, -575)→(0, -1); (-75, -575)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Plan-Heizkörper Anschluss Unten Rechts | Plan-Heizkörper, Anschluss unten rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (515.7, -575)→(0, -1); (665.7, -575)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Plan-Heizkörper Anschluss Wechselseitig Links | Plan-Heizkörper, Anschluss wechselseitig links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-825, 425)→(-1, 0); (825, -425)→(1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Plan-Heizkörper Anschluss Wechselseitig Rechts | Plan-Heizkörper, Anschluss wechselseitig rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (825, 425)→(1, 0); (-825, -425)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Plan-Heizkörper Anschluss-Links | Plan-Heizkörper, Anschluss links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-825, 425)→(-1, 0); (-825, -425)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Heizkörper | Profiliert-Heizkörper Anschluss Rechts | Profiliert-Heizkörper, Anschluss rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (825, 425)→(1, 0); (825, -425)→(1, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Heizkörper | Profiliert-Heizkörper Anschluss Unten | Profiliert-Heizkörper, Anschluss unten, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (665.7, -575)→(0, -1); (-665.7, -575)→(0, -1) | ja | ByLayer×1 | ByLayer×1 | 0×1 | 1 | – |
| Heizkörper | Profiliert-Heizkörper Anschluss Unten Links | Profiliert-Heizkörper, Anschluss unten links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-515.7, -575)→(0, -1); (-665.7, -575)→(0, -1) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Heizkörper | Profiliert-Heizkörper Anschluss Unten Mitte | Profiliert-Heizkörper, Anschluss unten mitte, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (75, -575)→(0, -1); (-75, -575)→(0, -1) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Heizkörper | Profiliert-Heizkörper Anschluss Unten Rechts | Profiliert-Heizkörper, Anschluss unten rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (515.7, -575)→(0, -1); (665.7, -575)→(0, -1) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Heizkörper | Profiliert-Heizkörper Anschluss Wechselseitig Links | Profiliert-Heizkörper, Anschluss wechselseitig links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-825, 425)→(-1, 0); (825, -425)→(1, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Heizkörper | Profiliert-Heizkörper Anschluss Wechselseitig Rechts | Profiliert-Heizkörper, Anschluss wechselseitig rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (825, 425)→(1, 0); (-825, -425)→(-1, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Heizkörper | Profiliert-Heizkörper Anschluss-Links | Profiliert-Heizkörper, Anschluss links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-825, 425)→(-1, 0); (-825, -425)→(-1, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Heizkörper | Röhren-Heizkörper Anschluss Rechts | Röhren-Heizkörper, Anschluss rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (825, -425)→(1, 0); (825, 425)→(1, 0) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Heizkörper | Röhren-Heizkörper Anschluss Unten | Röhren-Heizkörper, Anschluss unten, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (665.7, -575)→(0, -1); (-665.7, -575)→(0, -1) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Heizkörper | Röhren-Heizkörper Anschluss Unten Links | Röhren-Heizkörper, Anschluss unten links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-515.7, -575)→(0, -1); (-665.7, -575)→(0, -1) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Heizkörper | Röhren-Heizkörper Anschluss Unten Mitte | Röhren-Heizkörper, Anschluss unten mitte, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (75, -575)→(0, -1); (-75, -575)→(0, -1) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Heizkörper | Röhren-Heizkörper Anschluss Unten Rechts | Röhren-Heizkörper, Anschluss unten rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (665.7, -575)→(0, -1); (515.7, -575)→(0, -1) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Heizkörper | Röhren-Heizkörper Anschluss Wechselseitig Links | Röhren-Heizkörper, Anschluss wechselseitig links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-825, 425)→(-1, 0); (825, -425)→(1, 0) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Heizkörper | Röhren-Heizkörper Anschluss Wechselseitig Rechts | Röhren-Heizkörper, Anschluss wechselseitig rechts, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (825, 425)→(1, 0); (-825, -425)→(-1, 0) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Heizkörper | Röhren-Heizkörper Anschluss-Links | Röhren-Heizkörper, Anschluss links, gibt Wärme an den Raum ab | 3 | (0, 0)→(0, 0); (-825, -425)→(-1, 0); (-825, 425)→(-1, 0) | ja | ByLayer×17 | ByLayer×17 | 0×17 | 1 | – |
| Leitungsverbinder | Antrieb-Hand | Antrieb-Hand, die Armatur wird von Hand gestellt | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Leitungsverbinder | Festpunkt | Festpunkt, nimmt die Kräfte der Leitung auf und legt sie in ihrer Lage fest | 2 | (50, 0)→(50, 0); (-50, 0)→(-50, 0) | nein | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Leitungsverbinder | Flansch-Stutzen | Flansch-Stutzen, Anschluss an Behälter oder Leitung | 2 | (0, 0)→(0, 0); (125, 0)→(1, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Leitungsverbinder | Flansch-Verbindung | Flansch-Verbindung, lösbare Verbindung über verschraubte Flansche | 3 | (25, 0)→(25, 0); (-25, 0)→(-25, 0); (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | 6 |
| Leitungsverbinder | Gegenflansch | Gegenflansch, lösbare Verbindung über verschraubte Flansche | 2 | (0, 0)→(0, 0); (50, 0)→(1, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Leitungsverbinder | Gleitpunkt | Gleitpunkt, führt die Leitung und lässt die Längsdehnung zu | 2 | (50, 0)→(50, 0); (-50, 0)→(-50, 0) | nein | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Leitungsverbinder | Hosen-Bogen |  | 4 | (0, 0)→(0, 0); (-150, 100)→(-1, 0); (150, 100)→(1, 0); (0, -100)→(0, -1) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Leitungsverbinder | Kompensator | Kompensator, nimmt die Längsdehnung der Leitung auf | 2 | (200, 0)→(200, 0); (-200, 0)→(-200, 0) | nein | ByLayer×15 | ByLayer×15 | 0×15 | 1 | – |
| Leitungsverbinder | Kupplung | Kupplung, schnell lösbare Schlauch- oder Leitungsverbindung | 2 | (107.5, 0)→(1, 0); (-107.5, 0)→(-1, 0) | nein | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Leitungsverbinder | Kupplung Female | Kupplung Female, schnell lösbare Schlauch- oder Leitungsverbindung | 1 | (0, 0)→(-1, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Leitungsverbinder | Kupplung Male | Kupplung Male, schnell lösbare Schlauch- oder Leitungsverbindung | 1 | (0, 0)→(1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Leitungsverbinder | Leitungsabschluss | Leitungsabschluss, schließt die Leitung ab | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Leitungsverbinder | Lochblende | Lochblende, drosselt den Durchfluss über einen festen Querschnitt | 2 | (0, 25)→(0, 1); (0, -25)→(0, -1) | nein | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Leitungsverbinder | Materialwechsel | Materialwechsel, Übergang zwischen zwei Rohrwerkstoffen | 1 | (0, 0)→(0, 0) | ja | ByLayer×1 | ByLayer×1 | 0×1 | 1 | 6 |
| Leitungsverbinder | Paßstück | Passstück, gleicht die Einbaulänge aus | 3 | (0, 0)→(0, 0); (0, 100)→(0, 1); (0, -100)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Leitungsverbinder | PaßStück ausgebaut | Passstück ausgebaut, gleicht die Einbaulänge aus | 3 | (0, 100)→(0, 1); (0, -100)→(0, -1); (0, 0)→(0, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Leitungsverbinder | Reduzierung | Reduzierung, Übergang zwischen zwei Nennweiten | 3 | (35, 0)→(35, 0); (-35, 0)→(-35, 0); (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | 18 |
| Leitungsverbinder | Reduzierung exentrisch | Reduzierung exzentrisch, Übergang zwischen zwei Nennweiten | 3 | (0, 0)→(0, 0); (75, 0)→(1, 0); (-75, 0)→(-1, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Leitungsverbinder | Schlauch | Schlauch, flexible Leitungsverbindung | 2 | (280, 0)→(280, 0); (-280, 0)→(-280, 0) | nein | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Leitungsverbinder | Schraub-Verbindung | Schraub-Verbindung, lösbare Verbindung über eine Überwurfmutter | 3 | (25, 0)→(25, 0); (-25, 0)→(-25, 0); (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Leitungsverbinder | Steckscheibe | Steckscheibe, trennt die Leitung sicher auf | 2 | (0, 25)→(0, 1); (0, -25)→(0, -1) | nein | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Leitungsverbinder | T-Bogen |  | 4 | (0, 0)→(0, 0); (-150, 0)→(-1, 0); (150, 0)→(1, 0); (0, 200)→(0, 1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Leitungsverbinder | TriClamp-Stutzen | TriClamp-Stutzen, Anschluss an Behälter oder Leitung | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Leitungsverbinder | TriClamp-Verbindung | TriClamp-Verbindung, lösbare Klemmverbindung nach DIN 32676 | 3 | (25, 0)→(25, 0); (-25, 0)→(-25, 0); (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Leitungsverbinder | Verbindungspunkt |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Lüftung | 2-Leiter Umluft-Kühler-Heizer | 2-Leiter Umluft-Kühler-Heizer, kühlt die Raumluft im Umluftbetrieb | 3 | (0, 0)→(0, 0); (-140, 750)→(0, 1); (140, 750)→(0, 1) | ja | ByLayer×36 | ByLayer×36 | 0×36 | 1 | – |
| Lüftung | 4-Leiter Umluft-Kühler-Heizer | 4-Leiter Umluft-Kühler-Heizer, kühlt die Raumluft im Umluftbetrieb | 5 | (0, 0)→(0, 0); (-140, 750)→(0, 1); (140, 750)→(0, 1); (-290, 750)→(0, 1); (290, 750)→(0, 1) | ja | ByLayer×50 | ByLayer×50 | 0×50 | 1 | – |
| Lüftung | Absperrklappe Lüftung | Absperrklappe Lüftung, sperrt den Durchfluss über eine drehbare Scheibe ab | 3 | (0, 0)→(0, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Absperrklappe Lüftung Motorantrieb | Absperrklappe Lüftung mit Motorantrieb, sperrt den Durchfluss über eine drehbare | 6 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 350)→(0, 1); (100, 250)→(1, 0); (-100, 250)→(-1, 0) | ja | ByLayer×10 | ByLayer×10 | 0×10 | 1 | – |
| Lüftung | Airbreak Abluft | Airbreak Abluft, führt die Luft dem Raum zu oder aus ihm ab | 3 | (0, 0)→(0, 0); (0, 125)→(0, 1); (0, -125)→(0, -1) | ja | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Lüftung | Airbreak Zuluft | Airbreak Zuluft, führt die Luft dem Raum zu oder aus ihm ab | 3 | (0, 0)→(0, 0); (0, 125)→(0, 1); (0, -125)→(0, -1) | ja | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Lüftung | Anschluss elastisch | Anschluss elastisch, entkoppelt Gerät und Kanal schwingungstechnisch | 3 | (0, 0)→(0, 0); (100, 0)→(0, 1); (-100, 0)→(0, -1) | ja | ByLayer×13 | ByLayer×13 | 0×13 | 1 | – |
| Lüftung | Befeuchtung Dampf | Befeuchtung Dampf, führt der Zuluft Feuchte zu | 5 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0); (400, -450)→(0, -1); (-400, -450)→(0, -1) | ja | ByLayer×26 | ByLayer×26 | 0×26 | 1 | – |
| Lüftung | Befeuchtung Dampf Zone | Befeuchtung Dampf Zone, führt der Zuluft Feuchte zu | 1 | (0, 0)→(0, 0) | ja | ByLayer×21 | ByLayer×21 | 0×21 | 1 | – |
| Lüftung | Befeuchtung Umlauf | Befeuchtung Umlauf, führt der Zuluft Feuchte zu | 3 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0) | ja | ByLayer×32 | ByLayer×32 | 0×32 | 1 | – |
| Lüftung | Brandschutz Tellerventil Abströmend | Brandschutz Tellerventil, abströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×23 | ByLayer×23 | 0×23 | 1 | – |
| Lüftung | Brandschutz Tellerventil Zuströmend | Brandschutz Tellerventil, zuströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×23 | ByLayer×23 | 0×23 | 1 | – |
| Lüftung | Brandschutzklappe | Brandschutzklappe, verschließt den Kanal im Brandfall | 3 | (0, 0)→(0, 0); (0, 110)→(0, 1); (0, -110)→(0, -1) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Brandschutzklappe Motor | Brandschutzklappe mit Motorantrieb, verschließt den Kanal im Brandfall | 6 | (0, 0)→(0, 0); (0, 110)→(0, 1); (0, -110)→(0, -1); (-350, 0)→(-1, 0); (-250, 100)→(0, 1); (-250, -100)→(0, -1) | ja | ByLayer×10 | ByLayer×10 | 0×10 | 1 | – |
| Lüftung | Dachaufsatz Ventilator | Dachaufsatz Ventilator, fördert die Luft im Kanalnetz | 1 | (0, 0)→(0, -1) | ja | ByLayer×16 | ByLayer×16 | 0×16 | 1 | – |
| Lüftung | Drosselklappe Lüftung | Drosselklappe Lüftung, drosselt den Luftvolumenstrom im Kanal | 3 | (0, 0)→(0, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Drosselklappe Lüftung Motor | Drosselklappe Lüftung mit Motorantrieb, drosselt den Luftvolumenstrom im Kanal | 6 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 350)→(0, 1); (100, 250)→(1, 0); (-100, 250)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Lüftung | Einzelraum Ventilator | Einzelraum Ventilator, fördert die Luft im Kanalnetz | 3 | (0, 0)→(0, 0); (0, 112.5)→(0, 1); (0, -112.5)→(0, -1) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Lüftung | Erhitzer Elektro Zone | Erhitzer Elektro Zone, erwärmt die Zuluft nach der zentralen Aufbereitung | 5 | (0, 0)→(0, 0); (250, 0)→(1, 0); (-250, 0)→(-1, 0); (200, -250)→(0, -1); (-200, -250)→(0, -1) | ja | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Lüftung | Erhitzer Kühler Zone | Erhitzer Kühler Zone, kühlt die Zuluft nach der zentralen Aufbereitung | 13 | (250, 200)→(1, 0); (250, -200)→(1, 0); (0, 0)→(0, 0); (-250, 200)→(-1, 0); (-250, -200)→(-1, 0); (250, 0)→(1, 0); (-250, 0)→(-1, 0); (-200, 250)→(0, 1); (0, -25 | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Erhitzer Luft Dampf Gerät | Erhitzer Luft Dampf, Gerätedarstellung, erwärmt die Luft in der zentralen Aufber | 5 | (0, 0)→(0, 0); (400, -450)→(0, -1); (-400, -450)→(0, -1); (450, 0)→(1, 0); (-450, 0)→(-1, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Lüftung | Erhitzer Luft Elektro Gerät | Erhitzer Luft Elektro, Gerätedarstellung, erwärmt die Luft in der zentralen Aufb | 5 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0); (400, -450)→(0, -1); (-400, -450)→(0, -1) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Erhitzer Luft Wasser Gerät | Erhitzer Luft Wasser, Gerätedarstellung, erwärmt die Luft in der zentralen Aufbe | 5 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0); (400, -450)→(0, -1); (-400, -450)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Lüftung | Erhitzer Zone | Erhitzer Zone, erwärmt die Zuluft nach der zentralen Aufbereitung | 5 | (0, 0)→(0, 0); (250, 0)→(1, 0); (-250, 0)→(-1, 0); (200, -250)→(0, -1); (-200, -250)→(0, -1) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | 280 |
| Lüftung | Erhitzer-Kühler Luft Wasser Gerät | Erhitzer-Kühler Luft Wasser, Gerätedarstellung, kühlt die Luft in der zentralen  | 9 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0); (0, 450)→(0, 1); (0, -450)→(0, -1); (400, -450)→(0, -1); (-400, -450)→(0, -1); (400, 450)→(0, 1); (-400, 450) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Fan Coil Heizen | Fan Coil Heizen, heizt oder kühlt den Raum mit eigenem Ventilator | 3 | (0, 0)→(0, 0); (-450, 247.5)→(-1, 0); (-450, -247.5)→(-1, 0) | ja | ByLayer×39 | ByLayer×39 | 0×39 | 1 | – |
| Lüftung | Fan Coil Heizen Kühlen | Fan Coil Heizen Kühlen, heizt oder kühlt den Raum mit eigenem Ventilator | 4 | (0, 0)→(0, 0); (-450, 247.5)→(-1, 0); (-450, -247.5)→(-1, 0); (-450, 0)→(-1, 0) | ja | ByLayer×51 | ByLayer×51 | 0×51 | 1 | – |
| Lüftung | Fan Coil Kühlen | Fan Coil Kühlen, heizt oder kühlt den Raum mit eigenem Ventilator | 4 | (0, 0)→(0, 0); (-450, 247.5)→(-1, 0); (-450, -247.5)→(-1, 0); (-450, 0)→(-1, 0) | ja | ByLayer×49 | ByLayer×49 | 0×49 | 1 | – |
| Lüftung | Filter Fan Unit | Filter Fan Unit, scheidet Partikel aus der Luft ab | 9 | (0, 0)→(0, 0); (350, 137)→(1, 0); (210, 485)→(1, 0); (-350, 137)→(-1, 0); (-210, 485)→(-1, 0); (210, 337.5)→(1, 0); (-210, 337.5)→(-1, 0); (-210, 632.5)→(-1, 0) | ja | ByLayer×35 | ByLineWeightDefault×28, ByLayer×7 | 0×35 | 1 | – |
| Lüftung | Filter Luft | Filter Luft, scheidet Partikel aus der Luft ab | 3 | (0, 0)→(0, 0); (300, 0)→(1, 0); (-300, 0)→(-1, 0) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Frostschutz Gitter | Frostschutz Gitter, schützt die Außenluftöffnung vor Regen und Fremdkörpern | 1 | (0, 0)→(0, 0) | ja | ByLayer×13 | ByLayer×13 | 0×13 | 1 | – |
| Lüftung | Gitter Abströmend | Gitter, abströmend, Luftdurchlass in Gitterausführung | 1 | (0, 0)→(0, 1) | ja | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Lüftung | Gitter Zuströmend | Gitter, zuströmend, Luftdurchlass in Gitterausführung | 1 | (0, 0)→(0, 1) | ja | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Lüftung | Irisblende | Irisblende, hält den Luftvolumenstrom auf dem eingestellten Wert | 3 | (0, 0)→(0, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×11 | ByLayer×11 | 0×11 | 1 | – |
| Lüftung | Irisblende Motor | Irisblende mit Motorantrieb, hält den Luftvolumenstrom auf dem eingestellten Wer | 6 | (0, 0)→(0, 0); (0, 150)→(0, 1); (0, -150)→(0, -1); (-350, 0)→(-1, 0); (-250, 100)→(0, 1); (-250, -100)→(0, -1) | ja | ByLayer×10 | ByLayer×10 | 0×10 | 1 | – |
| Lüftung | Jalousieklappe Gegenläufig | Jalousieklappe Gegenläufig, regelt oder sperrt den Luftstrom über verstellbare L | 3 | (0, 0)→(0, 0); (100, 0)→(1, 0); (-100, 0)→(-1, 0) | ja | ByLayer×28 | ByLayer×28 | 0×28 | 1 | – |
| Lüftung | Jalousieklappe Gegenläufig Motor | Jalousieklappe Gegenläufig mit Motorantrieb, regelt oder sperrt den Luftstrom üb | 6 | (0, 0)→(0, 0); (100, 0)→(1, 0); (-100, 0)→(-1, 0); (0, 650)→(0, 1); (100, 550)→(1, 0); (-100, 550)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Lüftung | Jalousieklappe Gegenläufig Motor Zone | Jalousieklappe Gegenläufig Motor Zone, regelt oder sperrt den Luftstrom über ver | 6 | (0, 0)→(0, 0); (100, 0)→(1, 0); (-100, 0)→(-1, 0); (0, 350)→(0, 1); (100, 250)→(1, 0); (-100, 250)→(-1, 0) | ja | ByLayer×15 | ByLayer×15 | 0×15 | 1 | – |
| Lüftung | Jalousieklappe Gleichläufig | Jalousieklappe Gleichläufig, regelt oder sperrt den Luftstrom über verstellbare  | 3 | (0, 0)→(0, 0); (100, 0)→(1, 0); (-100, 0)→(-1, 0) | ja | ByLayer×28 | ByLayer×28 | 0×28 | 1 | – |
| Lüftung | Kreuzstrom Wärmetauscher | Kreuzstrom Wärmetauscher, überträgt Wärme von der Fort- auf die Zuluft | 5 | (0, 0)→(0, 0); (318.2, 318.2)→(1, 1); (-318.2, 318.2)→(-1, 1); (-318.2, -318.2)→(-1, -1); (318.2, -318.2)→(1, -1) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Lüftung | Kühler Luft Kältemittel Gerät | Kühler Luft Kältemittel, Gerätedarstellung, kühlt die Luft in der zentralen Aufb | 5 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0); (400, -450)→(0, -1); (-400, -450)→(0, -1) | ja | ByLayer×10 | ByLayer×10 | 0×10 | 1 | – |
| Lüftung | Kühler Luft Wasser Gerät | Kühler Luft Wasser, Gerätedarstellung, kühlt die Luft in der zentralen Aufbereit | 5 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0); (400, -450)→(0, -1); (-400, -450)→(0, -1) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Lüftung | Kühler Zone | Kühler Zone, kühlt die Zuluft nach der zentralen Aufbereitung | 5 | (0, 0)→(0, 0); (250, 0)→(1, 0); (-250, 0)→(-1, 0); (200, -250)→(0, -1); (-200, -250)→(0, -1) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Lüftung | Kühler Zone Kältemittel | Kühler Zone Kältemittel, kühlt die Zuluft nach der zentralen Aufbereitung | 5 | (0, 0)→(0, 0); (250, 0)→(1, 0); (-250, 0)→(-1, 0); (200, -250)→(0, -1); (-200, -250)→(0, -1) | ja | ByLayer×10 | ByLayer×10 | 0×10 | 1 | – |
| Lüftung | Luftdurchlass Abströmend | Luftdurchlass, abströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×24 | ByLineWeightDefault×20, ByLayer×4 | 0×24 | 1 | – |
| Lüftung | Luftdurchlass Abströmend Allgemein | Luftdurchlass Abströmend, allgemeine Darstellung, führt die Luft dem Raum zu ode | 2 | (0, 60)→(0, 1); (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Lüftung | Luftdurchlass Drall Draufsicht | Luftdurchlass Drall Draufsicht, führt die Luft dem Raum zu oder aus ihm ab | 5 | (311.5, 0)→(1, 0); (-311.5, 0)→(-1, 0); (0, -311.5)→(0, -1); (0, 311.5)→(0, 1); (0, 0)→(0, 0) | ja | ByLayer×128 | ByLayer×64, LineWeight025×64 | 0×128 | 1 | – |
| Lüftung | Luftdurchlass Filter Abströmend | Luftdurchlass Filter, abströmend, scheidet Partikel aus der Luft ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×28 | ByLineWeightDefault×28 | 0×28 | 1 | – |
| Lüftung | Luftdurchlass Filter Zuströmend | Luftdurchlass Filter, zuströmend, scheidet Partikel aus der Luft ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×28 | ByLineWeightDefault×28 | 0×28 | 1 | – |
| Lüftung | Luftdurchlass Lochblech Abströmend | Luftdurchlass Lochblech, abströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×50 | ByLayer×50 | 0×50 | 1 | – |
| Lüftung | Luftdurchlass Lochblech Zuströmend | Luftdurchlass Lochblech, zuströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×50 | ByLayer×50 | 0×50 | 1 | – |
| Lüftung | Luftdurchlass Zuströmend | Luftdurchlass, zuströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×24 | ByLineWeightDefault×20, ByLayer×4 | 0×24 | 1 | – |
| Lüftung | Luftdurchlass Zuströmend Allgemein | Luftdurchlass Zuströmend, allgemeine Darstellung, führt die Luft dem Raum zu ode | 2 | (0, 0)→(0, 0); (0, 60)→(0, 1) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Lüftung | Luftturm | Luftturm, Ansaug- oder Fortluftturm über Dach | 1 | (0, 0)→(0, -1) | ja | ByLayer×25 | ByLayer×25 | 0×25 | 1 | – |
| Lüftung | Mischkammer | Mischkammer, führt Außen- und Umluft zusammen | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Lüftung | Mischkammer Mischröhren | Mischkammer Mischröhren, führt Außen- und Umluft zusammen | 5 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0); (0, 450)→(0, 1); (0, -450)→(0, -1) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Lüftung | Pfeil Abströmung |  | 3 | (0, 0)→(1, 0); (0, 0)→(-1, 0); (0, 0)→(0, 0) | ja | ByLayer×657 | ByLayer×657 | 0×657 | 1 | – |
| Lüftung | Pfeil Druckausgleich |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×666 | ByLayer×666 | 0×666 | 1 | – |
| Lüftung | Pfeil Zuströmung |  | 3 | (0, 0)→(0, 0); (0, 0)→(1, 0); (0, 0)→(-1, 0) | ja | ByLayer×657 | ByLayer×657 | 0×657 | 1 | – |
| Lüftung | Rauchschutzklappe | Rauchschutzklappe, verhindert die Rauchübertragung über den Kanal | 3 | (0, 110)→(0, 1); (0, -110)→(0, -1); (0, 0)→(0, 0) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Rückschlagklappe Lüftung | Rückschlagklappe Lüftung, verhindert den Rückfluss über eine schwenkende Klappe | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Lüftung | Schalldämpfer | Schalldämpfer, mindert die Schallübertragung in Kanal oder Leitung | 3 | (0, 0)→(0, 0); (250, 0)→(1, 0); (-250, 0)→(-1, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Lüftung | Schalldämpfer Gerät | Schalldämpfer, Gerätedarstellung, mindert die Schallübertragung in Kanal oder Le | 3 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Lüftung | Schlitzschiene Abströmend | Schlitzschiene, abströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×43 | ByLayer×43 | 0×43 | 1 | – |
| Lüftung | Schlitzschiene Zuströmend | Schlitzschiene, zuströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×43 | ByLayer×43 | 0×43 | 1 | – |
| Lüftung | Tellerventil Abströmend | Tellerventil, abströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×25 | ByLayer×25 | 0×25 | 1 | – |
| Lüftung | Tellerventil Draufsicht Abströmend | Tellerventil Draufsicht, abströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×22 | ByLayer×22 | 0×22 | 1 | – |
| Lüftung | Tellerventil Draufsicht Zuströmend | Tellerventil Draufsicht, zuströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×22 | ByLayer×22 | 0×22 | 1 | – |
| Lüftung | Tellerventil Zuströmend | Tellerventil, zuströmend, führt die Luft dem Raum zu oder aus ihm ab | 1 | (0, 0)→(0, 1) | ja | ByLayer×25 | ByLayer×25 | 0×25 | 1 | – |
| Lüftung | Tropfenfänger | Tropfenfänger, hält mitgerissene Wassertropfen zurück | 4 | (0, 0)→(0, 0); (75, 0)→(1, 0); (-75, 0)→(-1, 0); (101.2, -825.4)→(0, -1) | ja | ByLayer×24 | ByLayer×24 | 0×24 | 1 | – |
| Lüftung | Tropfenfänger Zone | Tropfenfänger Zone, hält mitgerissene Wassertropfen zurück | 4 | (0, 0)→(0, 0); (75, 0)→(1, 0); (-75, 0)→(-1, 0); (101.2, -600.4)→(0, -1) | ja | ByLayer×18 | ByLayer×18 | 0×18 | 1 | – |
| Lüftung | Umluftheitzer | Umluftheizer, erwärmt die Raumluft im Umluftbetrieb | 1 | (0, 0)→(0, 0) | ja | ByLayer×15 | ByLayer×15 | 0×15 | 1 | – |
| Lüftung | Umluftheitzer 2-Regelventil | Umluftheizer 2-Regelventil, erwärmt die Raumluft im Umluftbetrieb | 1 | (0, 0)→(0, 0) | ja | ByLayer×23 | ByLayer×19, ByLineWeightDefault×4 | 0×23 | 1 | – |
| Lüftung | Umluftheitzer 3-Regelventil | Umluftheizer 3-Regelventil, erwärmt die Raumluft im Umluftbetrieb | 1 | (0, 0)→(0, 0) | ja | ByLayer×27 | ByLayer×19, ByLineWeightDefault×8 | 0×27 | 1 | – |
| Lüftung | Umluftkühler | Umluftkühler, kühlt die Raumluft im Umluftbetrieb | 2 | (0, 0)→(0, 0); (0, -510)→(0, -1) | ja | ByLayer×18 | ByLayer×18 | 0×18 | 1 | – |
| Lüftung | Umluftkühler 2-Regelventil | Umluftkühler 2-Regelventil, kühlt die Raumluft im Umluftbetrieb | 2 | (0, 0)→(0, 0); (0, -510)→(0, -1) | ja | ByLayer×26 | ByLayer×22, ByLineWeightDefault×4 | 0×26 | 1 | – |
| Lüftung | Umluftkühler 2-Regelventil Pumpe | Umluftkühler 2-Regelventil Pumpe, kühlt die Raumluft im Umluftbetrieb | 2 | (0, 0)→(0, 0); (450, 300)→(1, 0) | ja | ByLayer×32 | ByLayer×28, ByLineWeightDefault×4 | 0×32 | 1 | – |
| Lüftung | Umluftkühler 3-Regelventil | Umluftkühler 3-Regelventil, kühlt die Raumluft im Umluftbetrieb | 2 | (0, 0)→(0, 0); (0, -510)→(0, -1) | ja | ByLayer×30 | ByLayer×22, ByLineWeightDefault×8 | 0×30 | 1 | – |
| Lüftung | Umluftkühler 3-Regelventil Pumpe | Umluftkühler 3-Regelventil Pumpe, kühlt die Raumluft im Umluftbetrieb | 2 | (0, 0)→(0, 0); (450, 300)→(1, 0) | ja | ByLayer×36 | ByLayer×28, ByLineWeightDefault×8 | 0×36 | 1 | – |
| Lüftung | Umluftkühler Pumpe | Umluftkühler Pumpe, kühlt die Raumluft im Umluftbetrieb | 2 | (0, 0)→(0, 0); (450, 300)→(1, 0) | ja | ByLayer×24 | ByLayer×24 | 0×24 | 1 | – |
| Lüftung | Ventilator | Ventilator, fördert die Luft im Kanalnetz | 3 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Lüftung | Ventilator Gerät | Ventilator, Gerätedarstellung, fördert die Luft im Kanalnetz | 3 | (0, 0)→(0, 0); (450, 0)→(1, 0); (-450, 0)→(-1, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Lüftung | Ventilator Wand | Ventilator Wand, fördert die Luft im Kanalnetz | 5 | (0, 0)→(0, 0); (-450, 0)→(-1, 0); (450, 0)→(1, 0); (0, 450)→(0, 1); (0, -450)→(0, -1) | ja | ByLayer×10 | ByLayer×10 | 0×10 | 1 | – |
| Lüftung | Volumenstromregler | Volumenstromregler, hält den Luftvolumenstrom auf dem eingestellten Wert | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Lüftung | Volumenstromregler konstant | Volumenstromregler konstant, hält den Luftvolumenstrom auf dem eingestellten Wer | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Lüftung | Volumenstromregler konstant mit Hilfsenergie | Volumenstromregler konstant mit Hilfsenergie, hält den Luftvolumenstrom auf dem  | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Lüftung | Volumenstromregler variabel | Volumenstromregler variabel, hält den Luftvolumenstrom auf dem eingestellten Wer | 3 | (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 0)→(0, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Lüftung | Volumenstromregler variabel mit Hilfsenergie | Volumenstromregler variabel mit Hilfsenergie, hält den Luftvolumenstrom auf dem  | 3 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0) | ja | ByLayer×10 | ByLayer×10 | 0×10 | 1 | – |
| Lüftung | Volumenstromregler variabel mit Motor | Volumenstromregler variabel mit Motor, hält den Luftvolumenstrom auf dem eingest | 6 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 350)→(0, 1); (100, 250)→(1, 0); (-100, 250)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Lüftung | VSR mit Schalldämpfer Abluft | VSR mit Schalldämpfer Abluft, hält den Luftvolumenstrom auf dem eingestellten We | 6 | (0, 0)→(0, 0); (400, 0)→(1, 0); (-400, 0)→(-1, 0); (250, 350)→(0, 1); (350, 250)→(1, 0); (150, 250)→(-1, 0) | ja | ByLayer×15 | ByLayer×15 | 0×15 | 1 | – |
| Lüftung | VSR mit Schalldämpfer Zuluft | VSR mit Schalldämpfer Zuluft, hält den Luftvolumenstrom auf dem eingestellten We | 6 | (0, 0)→(0, 0); (400, 0)→(1, 0); (-400, 0)→(-1, 0); (350, 250)→(1, 0); (250, 350)→(0, 1); (150, 250)→(-1, 0) | ja | ByLayer×15 | ByLayer×15 | 0×15 | 1 | – |
| Lüftung | Wetterschutzgitter links | Wetterschutzgitter links, schützt die Außenluftöffnung vor Regen und Fremdkörper | 1 | (0, 0)→(1, 0) | ja | ByLayer×22 | ByLayer×22 | 0×22 | 1 | – |
| Lüftung | Wetterschutzgitter rechts | Wetterschutzgitter rechts, schützt die Außenluftöffnung vor Regen und Fremdkörpe | 1 | (0, 0)→(-1, 0) | ja | ByLayer×22 | ByLayer×22 | 0×22 | 1 | – |
| Lüftung | WRG Luft Wasser Gerät | WRG Luft Wasser, Gerätedarstellung, überträgt Wärme von der Fort- auf die Zuluft | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Lüftung | Wärmerad | Wärmerad, überträgt Wärme von der Fort- auf die Zuluft | 5 | (0, 0)→(0, 0); (450, 900)→(1, 0); (-450, 900)→(-1, 0); (-450, -900)→(-1, 0); (450, -900)→(1, 0) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Messung-Anzeige | Anzeige Differenz-Druck | Anzeige Differenz-Druck, zeigt den Druck vor Ort an | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Messung-Anzeige | Anzeige Druck | Anzeige Druck, zeigt den Druck vor Ort an | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Messung-Anzeige | Anzeige Feuchte | Anzeige Feuchte, zeigt die Feuchte vor Ort an | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Messung-Anzeige | Anzeige Temperatur | Anzeige Temperatur, zeigt die Temperatur vor Ort an | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | 4 |
| Messung-Anzeige | Differenzdruck Messung Fluid | Differenzdruck Messung Fluid, erfasst eine Prozessgröße | 2 | (325, 0)→(325, 0); (-325, 0)→(-325, 0) | nein | ByLayer×18 | ByLayer×12, ByLineWeightDefault×6 | 0×18 | 1 | – |
| Messung-Anzeige | Druckbegrenzer | Druckbegrenzer, überwacht den Druck und meldet bei Über- oder Unterschreiten | 1 | (0, 0)→(0, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Messung-Anzeige | Druckbegrenzer Max. | Druckbegrenzer Max., überwacht den Druck und meldet bei Über- oder Unterschreite | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Messung-Anzeige | Druckbegrenzer Min. | Druckbegrenzer Min., überwacht den Druck und meldet bei Über- oder Unterschreite | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Messung-Anzeige | Messblende | Messblende, erfasst den Volumenstrom in der Leitung | 4 | (150, 0)→(150, 0); (-150, 0)→(-150, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | nein | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Messung-Anzeige | Messstutzen Fluid | Messstutzen Fluid, Anschluss für ein Messgerät | 2 | (0, 0)→(0, 0); (0, 150)→(0, 1) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Messung-Anzeige | Messstutzen Luft | Messstutzen Luft, Anschluss für ein Messgerät | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Messung-Anzeige | Messung Durchfluss Differenzdruck | Messung Durchfluss Differenzdruck, erfasst den Volumenstrom in der Leitung | 5 | (0, 0)→(0, 0); (0, 150)→(0, 1); (150, 0)→(1, 0); (0, -150)→(0, -1); (-150, 0)→(-1, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Messung-Anzeige | Messung Durchfluss Induktion | Messung Durchfluss Induktion, erfasst den Volumenstrom in der Leitung | 5 | (0, 0)→(0, 0); (0, 150)→(0, 1); (150, 0)→(1, 0); (0, -150)→(0, -1); (-150, 0)→(-1, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Messung-Anzeige | Messung Durchfluss Schall | Messung Durchfluss Schall, erfasst den Volumenstrom in der Leitung | 5 | (0, 0)→(0, 0); (0, 150)→(0, 1); (150, 0)→(1, 0); (0, -150)→(0, -1); (-150, 0)→(-1, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Messung-Anzeige | Messung Energie | Messung Energie, erfasst die übertragene Wärme- oder Kältemenge | 5 | (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 150)→(0, 1); (0, -150)→(0, -1); (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Messung-Anzeige | Messung Volumen | Messung Volumen, erfasst den Volumenstrom in der Leitung | 5 | (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 150)→(0, 1); (0, -150)→(0, -1); (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Messung-Anzeige | Meßstutzen mit Kugelhahn | Messstutzen mit Kugelhahn, Anschluss für ein Messgerät | 2 | (0, 0)→(0, 0); (0, 300)→(0, 1) | ja | ByLayer×13 | ByLineWeightDefault×8, ByLayer×5 | 0×13 | 1 | – |
| Messung-Anzeige | Meßstutzen mit Kugelhahn und Manometer | Messstutzen mit Kugelhahn und Manometer, Anschluss für ein Messgerät | 1 | (0, 0)→(0, 0) | ja | ByLayer×17 | ByLayer×9, ByLineWeightDefault×8 | 0×17 | 1 | – |
| Messung-Anzeige | Meßstutzen mit Thermometer | Messstutzen mit Thermometer, zeigt die Temperatur vor Ort an | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Messung-Anzeige | MSR Messstelle Differenz-Druck | MSR Messstelle Differenz-Druck, erfasst eine Prozessgröße | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Messung-Anzeige | MSR Messstelle Druck | MSR Messstelle Druck, erfasst eine Prozessgröße | 3 | (0, 0)→(0, 0); (100, 0)→(1, 0); (-100, 0)→(-1, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Messung-Anzeige | MSR Messstelle Feuchte | MSR Messstelle Feuchte, erfasst eine Prozessgröße | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Messung-Anzeige | MSR Messstelle Niveau | MSR Messstelle Niveau, erfasst eine Prozessgröße | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Messung-Anzeige | MSR Messstelle Strömung | MSR Messstelle Strömung, erfasst eine Prozessgröße | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Messung-Anzeige | MSR Messstelle Temperatur | MSR Messstelle Temperatur, erfasst eine Prozessgröße | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | 8 |
| Messung-Anzeige | MSR Messstelle Temperatur-Feuchte | MSR Messstelle Temperatur-Feuchte, erfasst eine Prozessgröße | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Messung-Anzeige | Sicherheits-Temperaturbegrenzer | Sicherheits-Temperaturbegrenzer, schaltet die Wärmequelle bei Übertemperatur dau | 1 | (0, 0)→(0, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Messung-Anzeige | Sicherheits-Temperaturwächter | Sicherheits-Temperaturwächter, schaltet die Wärmequelle bei Übertemperatur ab | 1 | (0, 0)→(0, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Messung-Anzeige | Temperatur-Regler | Temperatur-Regler, hält die Temperatur auf dem eingestellten Wert | 1 | (0, 0)→(0, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Messung-Anzeige | Vorabsperrung | Vorabsperrung, sperrt den Durchfluss ab | 3 | (0, 75)→(0, 1); (0, -75)→(0, -1); (0, 0)→(0, 0) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Pfeile | Pfeil |  | 3 | (0, 109)→(0, 1); (0, -109)→(0, -1); (0, 0)→(0, 0) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | 3 |
| Pfeile | Pfeil 3-Wege |  | 3 | (0, 0)→(0, 0); (-125, 0)→(-1, 0); (125, 0)→(1, 0) | ja | ByLayer×8 | ByLayer×8 | 0×8 | 1 | – |
| Pfeile | Pfeil Gefälle | PG | 2 | (100, 0)→(100, 0); (-100, 0)→(-100, 0) | nein | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Pfeile | Pfeil Richtung | PR | 3 | (60, 0)→(60, 0); (-60, 0)→(-60, 0); (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | 14 |
| Pumpen | Doppel Hebeanlage | Doppel Hebeanlage, fördert Abwasser über die Rückstauebene | 4 | (650, 0)→(650, 0); (-650, 0)→(-650, 0); (54, 665)→(0, 0); (554.5, 665)→(0, 0) | nein | ByLayer×21 | ByLayer×21 | 0×21 | 1 | – |
| Pumpen | Doppel-Pumpe | Doppel-Pumpe, fördert das Medium in der Leitung | 2 | (200, 0)→(200, 0); (-200, 0)→(-200, 0) | nein | ByLayer×14 | ByLayer×14 | 0×14 | 1 | – |
| Pumpen | Hebeanlage | Hebeanlage, fördert Abwasser über die Rückstauebene | 1 | (0, 500)→(500, 0) | nein | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Pumpen | Pumpe | Pumpe, fördert das Medium in der Leitung | 5 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 150)→(0, 1); (0, -150)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | 4 |
| Pumpen | Ruehrwerk Allgemein | Rührwerk, allgemeine Darstellung, hält das Medium im Behälter in Bewegung | 1 | (0, 0)→(0, 1) | ja | ByLayer×4 | ByLineWeightDefault×3, ByLayer×1 | 0×4 | 1 | – |
| Pumpen | Tauchpumpe | Tauchpumpe, fördert das Medium in der Leitung | 2 | (0, 0)→(0, 0); (0, 250)→(0, 1) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Pumpen | Tauchpumpe mit Schwimmerschalter | Tauchpumpe mit Schwimmerschalter, fördert das Medium in der Leitung | 1 | (0, 500)→(0, 0) | nein | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| Pumpen | Vakuumpumpe | Vakuumpumpe, erzeugt den Unterdruck im System | 9 | (0, 0)→(0, 0); (150, 0)→(1, 0); (-150, 0)→(-1, 0); (0, 150)→(0, 1); (0, -150)→(0, -1); (106.1, 106.1)→(1, 1); (106.1, -106.1)→(1, -1); (-106.1, -106.1)→(-1, -1) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Sanitär | 5 Liter Gerät | 5 Liter, Gerätedarstellung, erwärmt das Trinkwasser dezentral an der Zapfstelle | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByBlock×5 | 0×5 | 1 | – |
| Sanitär | Ablauf-Rinne 4fach | Ablauf-Rinne 4fach, nimmt Wasser über die Länge auf | 1 | (0, 135.4)→(0, 0) | nein | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Sanitär | Ablauf-Rinne 5fach | Ablauf-Rinne 5fach, nimmt Wasser über die Länge auf | 1 | (0, 130)→(0, 0) | nein | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Sanitär | Ablauf-Rinne 6fach | Ablauf-Rinne 6fach, nimmt Wasser über die Länge auf | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Sanitär | Ablauf-Rinne 7fach | Ablauf-Rinne 7fach, nimmt Wasser über die Länge auf | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| Sanitär | Ablauftrichter | Ablauftrichter, nimmt anfallendes Wasser auf | 2 | (0, 90)→(0, 90); (0, -150)→(0, -150) | nein | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Sanitär | Augendusche | Augendusche, Sanitärobjekt zum Duschen | 1 | (0, 240.5)→(0, 0) | nein | ByLayer×41 | ByBlock×41 | 0×41 | 1 | – |
| Sanitär | Ausgussbecken | Ausgussbecken, Sanitärobjekt zur Entsorgung von Putzwasser | 1 | (0, 17)→(0, 0) | nein | ByLayer×72 | ByBlock×72 | 0×72 | 1 | – |
| Sanitär | Badewanne | Badewanne, Sanitärobjekt zum Baden | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByBlock×3 | 0×3 | 1 | – |
| Sanitär | Bodeneinlauf | Bodeneinlauf, nimmt anfallendes Wasser auf | 1 | (0, 0)→(0, 0) | ja | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| Sanitär | Bodeneinlauf Siphon | Bodeneinlauf Siphon, Geruchverschluss im Ablauf | 1 | (0, 0)→(1, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Sanitär | Dacheinlauf Freispiegel | Dacheinlauf Freispiegel, entwässert die Dachfläche im Freispiegel | 1 | (0, -100)→(0, -1) | nein | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Sanitär | Dosieranlage | Dosieranlage, gibt Zusatzstoffe geregelt zu | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Sanitär | Durchlauferhitzer elektrisch | Durchlauferhitzer elektrisch, erwärmt das Trinkwasser im Durchfluss | 1 | (0, 0)→(0, 0) | ja | ByLayer×7 | ByBlock×7 | 0×7 | 1 | – |
| Sanitär | Dusche | Dusche, Sanitärobjekt zum Duschen | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByBlock×3 | 0×3 | 1 | – |
| Sanitär | Enthärtungsanlage | Enthärtungsanlage, senkt die Härte des Trinkwassers | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Sanitär | Frischwasserstation | Frischwasserstation, erwärmt das Trinkwasser im Durchfluss über einen Wärmetausc | 7 | (0, 0)→(0, 0); (0, 1065)→(0, 1); (548.5, 1065)→(0, 1); (-245.1, -1065)→(0, -1); (303.4, -1065)→(0, -1); (-693.3, 712.2)→(-1, 0); (-480, 872.2)→(0, 1) | ja | ByLayer×109 | ByLayer×85, ByBlock×24 | 0×109 | 1 | – |
| Sanitär | Geschirrspüler | Geschirrspüler, Küchengerät mit Wasser- und Abwasseranschluss | 1 | (0, 0)→(0, 0) | ja | ByLayer×14 | ByBlock×12, ByLayer×2 | 0×14 | 1 | – |
| Sanitär | Handwaschbecken | Handwaschbecken, Sanitärobjekt zum Händewaschen | 1 | (0, 0)→(0, 0) | ja | ByLayer×3 | ByBlock×3 | 0×3 | 1 | – |
| Sanitär | Notdusche | Notdusche, Sanitärobjekt zum Duschen | 1 | (0, -887.6)→(0, 0) | nein | ByLayer×40 | ByBlock×40 | 0×40 | 1 | – |
| Sanitär | Rinne eckig | Rinne eckig, nimmt Wasser über die Länge auf | 1 | (0, -50)→(0, -1) | nein | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Sanitär | Siphon | Siphon, Geruchverschluss im Ablauf | 2 | (-67.5, 90)→(0, 90); (67.5, -90)→(0, -90) | nein | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| Sanitär | Spülbecken | Spülbecken, Sanitärobjekt zum Spülen | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByBlock×5 | 0×5 | 1 | – |
| Sanitär | SpülStation-1fach | Spülstation einfach, Spülstation für Reinigungszwecke | 5 | (0, 0)→(0, 0); (135, 375)→(0, 1); (135, -375)→(0, -1); (285, 215)→(1, 0); (200.9, -147.5)→(1, 0) | ja | ByLayer×20 | ByLayer×20 | 0×20 | 1 | – |
| Sanitär | SpülStation-2fach | Spülstation zweifach, Spülstation für Reinigungszwecke | 9 | (0, 0)→(0, 0); (135, 375)→(0, 1); (135, -375)→(0, -1); (285, 215)→(1, 0); (200.9, -147.5)→(1, 0); (-135, 375)→(0, 1); (-135, -375)→(0, -1); (-285, 215)→(-1, 0); | ja | ByLayer×36 | ByLayer×36 | 0×36 | 1 | – |
| Sanitär | Strömungsteiler | Strömungsteiler, teilt den Volumenstrom auf | 5 | (0, 0)→(0, 0); (0, 150)→(0, 1); (0, -150)→(0, -1); (90, 100)→(1, 0); (90, -100)→(1, 0) | ja | ByLayer×12 | ByLayer×10, ByLineWeightDefault×2 | 0×12 | 1 | – |
| Sanitär | Strömungsteiler Absperrung | Strömungsteiler Absperrung, teilt den Volumenstrom auf | 5 | (0, 0)→(0, 0); (0, 150)→(0, 1); (0, -150)→(0, -1); (240, 100)→(1, 0); (240, -100)→(1, 0) | ja | ByLayer×18 | ByLayer×10, ByLineWeightDefault×8 | 0×18 | 1 | – |
| Sanitär | Temperatur-Volumenstrom-Sensor | Temperatur-Volumenstrom-Sensor, erfasst eine Prozessgröße | 5 | (0, 0)→(0, 0); (0, 150)→(0, 1); (0, -150)→(0, -1); (75, 0)→(1, 0); (-75, 0)→(-1, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Sanitär | Trichter-Siphon | Trichter-Siphon, Geruchverschluss im Ablauf | 2 | (0, 90)→(0, 90); (135, -180)→(0, -180) | nein | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Sanitär | Untertisch Gerät | Untertisch, Gerätedarstellung, erwärmt das Trinkwasser dezentral an der Zapfstel | 1 | (0, 0)→(0, 0) | ja | ByLayer×5 | ByBlock×5 | 0×5 | 1 | – |
| Sanitär | Urinal | Urinal, wandhängendes Sanitärobjekt | 1 | (0, 0)→(0, 0) | ja | ByLayer×50 | ByBlock×50 | 0×50 | 1 | – |
| Sanitär | Waschmaschine | Waschmaschine, Haushaltsgerät mit Wasser- und Abwasseranschluss | 1 | (0, 0)→(0, 0) | ja | ByLayer×10 | ByBlock×8, ByLayer×2 | 0×10 | 1 | – |
| Sanitär | Waschtisch | Waschtisch, Sanitärobjekt zum Waschen | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByBlock×4 | 0×4 | 1 | – |
| Sanitär | WC | WC, Sanitärobjekt zur Fäkalienentsorgung | 5 | (0, 0)→(0, 0); (175, 212.5)→(1, 0); (-175, 212.5)→(-1, 0); (0, -412.5)→(0, -1); (0, 412.5)→(0, 1) | ja | ByLayer×4 | ByBlock×4 | 0×4 | 1 | – |
| Strang-Symbole | Rückschlagklappe Flansch | Rückschlagklappe Flansch, verhindert den Rückfluss über eine schwenkende Klappe | 1 | (0, 6.4)→(0, 0) | nein | ByLayer×8 | ByLineWeightDefault×7, LineWeight015×1 | 0×8 | 1 | – |
| Wärme-Kälteerzeuger | Rückkühler | Rückkühler, gibt Wärme an die Außenluft ab | 1 | (0, 0)→(0, 0) | ja | ByLayer×21 | ByLayer×21 | 0×21 | 1 | – |
| Wärme-Kälteerzeuger | Verdichter Allgemein | Verdichter, allgemeine Darstellung, verdichtet Gas oder Kältemittel | 5 | (0, 0)→(0, 0); (180, 0)→(1, 0); (-180, 0)→(-1, 0); (0, 180)→(0, 1); (0, -180)→(0, -1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| Wärme-Kälteerzeuger | Verdichter Hubkolben | Verdichter Hubkolben, verdichtet Gas oder Kältemittel | 5 | (0, 0)→(0, 0); (180, 0)→(1, 0); (-180, 0)→(-1, 0); (0, 180)→(0, 1); (0, -180)→(0, 0) | ja | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Wärme-Kälteverbraucher | Aufbau dreifach |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×13 | ByLayer×13 | 0×13 | 1 | – |
| Wärme-Kälteverbraucher | Aufbau_dreifach |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×13 | ByLayer×13 | 0×13 | 1 | – |
| Wärme-Kälteverbraucher | Verbraucher-Kälte | Verbraucher-Kälte, Sammelsymbol für eine Wärme- oder Kälteabnahme | 4 | (525, 0)→(1, 0); (0, 525)→(0, 1); (-525, 0)→(-1, 0); (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Wärme-Kälteverbraucher | Verbraucher-Wärme | Verbraucher-Wärme, Sammelsymbol für eine Wärme- oder Kälteabnahme | 4 | (525, 0)→(1, 0); (-525, 0)→(-1, 0); (0, 525)→(0, 1); (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| Wärme-Kälteverbraucher | Verdampfer | Verdampfer, überträgt Wärme zwischen zwei Medien | 9 | (0, 0)→(0, 0); (-500, 350)→(-1, 0); (-500, -350)→(-1, 0); (-500, 0)→(-1, 0); (500, 350)→(1, 0); (500, -350)→(1, 0); (500, 0)→(1, 0); (0, 625)→(0, 1); (0, -625)→ | ja | ByLayer×25 | ByLayer×25 | 0×25 | 1 | – |
| Wärme-Kälteverbraucher | Verdampfer 2fach | Verdampfer 2fach, überträgt Wärme zwischen zwei Medien | 9 | (0, 0)→(0, 0); (-1000, 350)→(-1, 0); (-1000, -350)→(-1, 0); (1000, 350)→(1, 0); (1000, -350)→(1, 0); (-1000, 0)→(-1, 0); (0, 625)→(0, 1); (0, -625)→(0, -1); (10 | ja | ByLayer×49 | ByLayer×49 | 0×49 | 1 | – |
| Wärme-Kälteverbraucher | Verdampfer 3fach | Verdampfer 3fach, überträgt Wärme zwischen zwei Medien | 12 | (0, 0)→(0, 0); (-1500, 350)→(-1, 0); (-1500, -350)→(-1, 0); (-1500, 0)→(-1, 0); (1500, 350)→(1, 0); (1500, -350)→(1, 0); (1500, 0)→(1, 0); (0, 625)→(0, 1); (0,  | ja | ByLayer×73 | ByLayer×73 | 0×73 | 1 | – |
| Wärme-Kälteverbraucher | Verdampfer 4fach | Verdampfer 4fach, überträgt Wärme zwischen zwei Medien | 11 | (0, 0)→(0, 0); (2000, 350)→(1, 0); (2000, 0)→(1, 0); (2000, -350)→(1, 0); (-2000, 350)→(-1, 0); (-2000, -350)→(-1, 0); (-2000, 0)→(-1, 0); (0, 625)→(0, 1); (100 | ja | ByLayer×97 | ByLayer×97 | 0×97 | 1 | – |
| Wärmetauscher | Wärmetauscher allgemein | Wärmetauscher, allgemeine Darstellung, überträgt Wärme zwischen zwei Medien | 6 | (550, 250)→(1, 0); (550, -250)→(1, 0); (500, 0)→(1, 0); (-500, 0)→(-1, 0); (0, 500)→(0, 1); (0, -500)→(0, -1) | nein | ByLayer×5 | ByLayer×5 | 0×5 | 1 | – |
| Wärmetauscher | Wärmetauscher Elektro | Wärmetauscher Elektro, überträgt Wärme zwischen zwei Medien | 5 | (0, 0)→(0, 0); (500, 0)→(1, 0); (-500, 0)→(-1, 0); (0, 500)→(0, 1); (0, -500)→(0, -1) | ja | ByLayer×10 | ByLayer×10 | 0×10 | 1 | – |
| Wärmetauscher | Wärmetauscher Platte | Wärmetauscher Platte, überträgt Wärme zwischen zwei Medien | 5 | (0, 0)→(0, 0); (500, 500)→(1, 0); (-500, 500)→(-1, 0); (500, -500)→(1, 0); (-500, -500)→(-1, 0) | ja | ByLayer×12 | ByLayer×12 | 0×12 | 1 | – |
| Wärmetauscher | Wärmetauscher Rohrbündel | Wärmetauscher Rohrbündel, überträgt Wärme zwischen zwei Medien | 6 | (500, 275)→(0, 1); (-500, 275)→(0, 1); (500, -275)→(0, -1); (-500, -275)→(0, -1); (1000, 0)→(1, 0); (-1000, 0)→(-1, 0) | nein | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| sonstigeBauteile | Bauteil Allgemein | BA | 4 | (300, 0)→(300, 0); (-300, 0)→(-300, 0); (0, 300)→(0, 300); (0, -300)→(0, -300) | nein | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| sonstigeBauteile | Dampf-Erzeuger | Dampf-Erzeuger, erzeugt Dampf aus Speisewasser | 1 | (0, 0)→(0, 0) | ja | ByLayer×9 | ByLayer×9 | 0×9 | 1 | – |
| sonstigeBauteile | Druckhaltung | Druckhaltung, hält den Anlagendruck und speist bei Bedarf nach | 4 | (0, 0)→(0, 0); (-300, 0)→(-1, 0); (-225, 300)→(0, 1); (225, 300)→(0, 1) | ja | ByLayer×22 | ByLayer×22 | 0×22 | 1 | – |
| sonstigeBauteile | Filter-Prozess | Filter-Prozess, hält Feststoffe aus dem Medium zurück | 8 | (150, 300)→(0, 1); (-150, 300)→(0, 1); (150, -300)→(0, -1); (-150, -300)→(0, -1); (0, -300)→(0, -1); (0, 300)→(0, 1); (200, 0)→(1, 0); (-200, 0)→(-1, 0) | nein | ByLayer×7 | ByLayer×7 | 0×7 | 1 | – |
| sonstigeBauteile | Filter-Steril | Filter-Steril, hält Feststoffe aus dem Medium zurück | 8 | (0, 300)→(0, 1); (0, -300)→(0, -1); (150, 300)→(0, 1); (-150, 300)→(0, 1); (-150, -300)→(0, -1); (150, -300)→(0, -1); (200, 0)→(1, 0); (-200, 0)→(-1, 0) | nein | ByLayer×21 | ByLayer×21 | 0×21 | 1 | – |
| sonstigeBauteile | Heizkreisverteiler | Heizkreisverteiler, verteilt das Heizwasser auf die einzelnen Heizkreise | 1 | (0, 0)→(0, 0) | ja | ByLayer×71 | ByLayer×71 | 0×71 | 1 | – |
| sonstigeBauteile | Heizung | H | 3 | (1, 0)→(0, 0); (-280, 150)→(-1, 0); (-280, -150)→(-1, 0) | nein | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| sonstigeBauteile | Katalysator | Katalysator, wandelt Stoffe im Gasstrom chemisch um | 8 | (150, 300)→(0, 1); (-150, 300)→(0, 1); (0, 300)→(0, 1); (150, -300)→(0, -1); (-150, -300)→(0, -1); (0, -300)→(0, -1); (200, 0)→(1, 0); (-200, 0)→(-1, 0) | nein | ByLayer×6 | ByLayer×6 | 0×6 | 1 | – |
| sonstigeBauteile | Kolone | Kolonne, trennt Stoffgemische durch Stoffaustausch | 8 | (0, 1)→(0, -1); (0, 3500)→(0, 1); (262.5, 500)→(1, 0); (-262.5, 500)→(-1, 0); (262.5, 3000)→(1, 0); (-262.5, 3000)→(-1, 0); (262.5, 1750)→(1, 0); (-262.5, 1750) | nein | ByLayer×27 | ByLayer×27 | 0×27 | 1 | – |
| sonstigeBauteile | MedienPunkt |  | 1 | (0, 0)→(0, 0) | ja | ByLayer×2 | ByLayer×2 | 0×2 | 1 | – |
| sonstigeBauteile | Pump-Druckhaltung-Entgasung-Nachspeisung | Pump-Druckhaltung-Entgasung-Nachspeisung, hält den Anlagendruck und speist bei B | 7 | (0, 0)→(0, 0); (730, 1855)→(1, 0) „EintrittMedium“; (200, 2195)→(1, 0); (1060, 1025)→(0, 1); (-206.2, 565)→(0, -1); (853.8, 565)→(0, -1); (-2226.8, -37.1)→(0, - | ja | ByLayer×207 | ByLayer×207 | 0×207 | 1 | – |
| sonstigeBauteile | Rohrstutzen | Rohrstutzen, Anschluss an Behälter oder Leitung | 5 | (0, 0)→(0, 0); (75, 0)→(1, 0); (-75, 0)→(-1, 0); (0, -75)→(0, -1); (0, 75)→(0, 1) | ja | ByLayer×3 | ByLayer×3 | 0×3 | 1 | – |
| sonstigeBauteile | Schnittstelle | ST | 1 | (0, 0)→(0, 0) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |
| sonstigeBauteile | Tiefpunkt | Tiefpunkt, tiefste Stelle der Leitung zur Entleerung | 1 | (0, 0)→(0, -1) | ja | ByLayer×4 | ByLayer×4 | 0×4 | 1 | – |

### Zuordnung DXF ↔ Zeichnung

- **Gefunden:** 393 Stile (Tabelle oben).
- **Fehlen in der Zeichnung (76 DXF-Blöcke ohne Stil):**
  - Armaturen: 3-Wege Umschaltventil Motor, Dampfentlüfter, Weiterführende-Probenahme, Orientierende-Probenahme
  - Behälter: Behälter ohne Füsse
  - Brandschott: Brandschott R120, Brandschott R90, Brandschott R30
  - Datenpunkte: Strömung
  - Elektro: Motor, Kühl-Gefrierschrank, Gefrierschrank, Kühlschrank, Herd, Backofen, WP-Aussenteil, WP-Innenteil, Trockner, E-Heizkörper, Dunstabzug, Mikrowelle, Wechselschalter, Erdung, Zählerplatz, Temperaturfühler-Aussen, Temperaturfühler-Innen, Raumthermostat-Fussbodenheizung, Durchlauferhitzer, Bodenleuchte
  - Heizkörper: Konvektor-Heizkörper Anschluss Rechts, Konvektor-Heizkörper Anschluss Unten Links, Konvektor-Heizkörper Anschluss Unten Rechts, Konvektor-Heizkörper Anschluss Unten Mitte, Konvektor-Heizkörper Anschluss Wechselseitig Rechts, Konvektor-Heizkörper Anschluss Wechselseitig Links, Profiliert-Heizkörper Anschluss Unten Rechts Links, Konvektor-Heizkörper Anschluss Unten
  - Lüftung: Luftdurchlass Übertsrömung, Filter Fan Unit klein, Filter Fan Unit SR, Mischbox
  - Messpunkte-RRD: Messpunkt ReinRaumDecke
  - Messung-Anzeige: Trompetenrohr mit Absperrung, Trompetenrohr, U-Rohr mit Absperrung, U-Rohr
  - Pfeile: Strömungspfeil
  - Sammler-Verteiler: Verteiler 4-fach, Sammler 4-fach, Verteiler 5-fach, Sammler 5-fach, Verteiler 6-fach, Sammler 6-fach, Verteiler 7-fach, Sammler 7-fach, Verteiler 8-fach, Sammler 8-fach
  - Sanitär: Ablauf-Rinne 33fach, Spülstation, WC mit Hygiene Funktion
  - Strang-Symbole: Hindurchgehend, Beginnend-Abwärts, Beginnend-Aufwärts, beginnend-aufwärts-Belüftung, von-oben-kommend-endend-Belüftung, hindurchgehend-Belüftung, von-oben-kommend-endend, von-unten-kommend-endend, Steigleitung
  - Wärme-Kälteerzeuger: Verdichter Strahl, Verdichter Sroll, V-Rückkühler
  - Wärme-Kälteverbraucher: Verbraucher-allgemein
  - sonstigeBauteile: Begleitheizung, Rührer, Einweg-Filterset
- **Nur in der Zeichnung (23 Stile, nicht in den DXF):** 3-Wege-Absperrorgan, 3-Wege-Hahn, ASG_Startsymbol_L750_H1050_S2_A750_SL150 (eingesetzt 1×), ASG_Verteiler_Mehrkammer_druckbehaftet_o6_u2_A1050_6300x600_rund (eingesetzt 1×), ASG_Waermetauscher_Platten_B1000_H1300_A1000_N0_K (eingesetzt 1×), Ablauf-Rinne 3fach, Dampfgarer, Differenzdruck Messung, Eckhahn, Entspannungstopf, Festbettfilter, Lufttopf, Messstutzen Aerosolaufgabe, Messstutzen Fluid Druck, Messstutzen Fluid Temperatur, Platten Wärmetauscher, Rohrbündel Wärmetauscher, Standard, Varivent, Varivent Anschluss, Ventil allgemein, WC Unterputzspülkasten, Wand Kessel

## 2. Auffälligkeiten (Symbole des Nutzers)

- **Schreibweisen:** Mischung aus Umlauten und Ersatz (z. B. „Ruehrwerk“ vs. „Rührer“), Leerzeichen vs. Bindestrich (z. B. „Doppel-Pumpe“ vs. „Doppel Hebeanlage“), Groß/klein uneinheitlich (z. B. „beginnend-aufwärts-Belüftung“ vs. „Beginnend-Aufwärts“). Tippfehler in DXF-Namen: Luftdurchlass Übertsrömung, Verdichter Sroll.
- **Dubletten (gleicher Name nach Angleichen von Schreibweise):** Aufbau dreifach / Aufbau_dreifach.
- **Nur 1 Anschluss:** 127 Stile – Antrieb 2-stufig, Antrieb-Gewicht, Antrieb-Hydraulik, Antrieb-Membran, Dehungsantrieb, Feder-Antrieb, Hubbegrenzung, Magnetantrieb, Plombierung, schließt bei Ausfall der Hilfsenergie, öffnet bei Ausfall der Hilfsenergie, 3-Wege Mischventil Hand, Automatische Entlüftung, Entleerung, Entlüftung, Sprühkugel, MAG Grösse 1, Mannloch, Schauglas Behälter, Tank-liegend, Tank-liegend-gedämmt, Tank-stehend, Tank-stehend-gedämmt, Tank-stehend-Temperiermantel, Brandschott L120, Brandschott L30, Brandschott L90, Datenpunkt Feldbus, Bewegunsgmelder, Deckenleuchte, Gegensprechanlage, Schalter mit Kontrollleuchte, Steckdose 3-fach mit Schutzkontakt, Steckdose 4-fach mit Schutzkontakt, Steckdose 5-fach mit Schutzkontakt, Wandleuchte, Konvektor-Heizkörper Anschluss-Links, Antrieb-Hand, Kupplung Female, Kupplung Male, Leitungsabschluss, Materialwechsel, TriClamp-Stutzen, Verbindungspunkt, Befeuchtung Dampf Zone, Brandschutz Tellerventil Abströmend, Brandschutz Tellerventil Zuströmend, Dachaufsatz Ventilator, Frostschutz Gitter, Gitter Abströmend, Gitter Zuströmend, Luftdurchlass Abströmend, Luftdurchlass Filter Abströmend, Luftdurchlass Filter Zuströmend, Luftdurchlass Lochblech Abströmend, Luftdurchlass Lochblech Zuströmend, Luftdurchlass Zuströmend, Luftturm, Mischkammer, Pfeil Druckausgleich …
- **Einfügepunkt nicht auf einem Anschluss:** 47 Stile – Motorantrieb, Rückschlagventil, Überströmventil Feder, Behälter, MAG Grösse 2, MAG Grösse 3, Pufferspeicher, Pufferspeicher mit Wärmetauscher, Speicher Wasser Erwärmer Bivalent, Speicher Wasser Erwärmer Monovalent, Vorschaltgefäss, Antennendose, Steckdose mit Schutzkontakt, Telefondose, Festpunkt, Gleitpunkt, Kompensator, Kupplung, Lochblende, Schlauch, Steckscheibe, Differenzdruck Messung Fluid, Messblende, Pfeil Gefälle, Doppel Hebeanlage, Doppel-Pumpe, Hebeanlage, Tauchpumpe mit Schwimmerschalter, Ablauf-Rinne 4fach, Ablauf-Rinne 5fach, Ablauftrichter, Augendusche, Ausgussbecken, Dacheinlauf Freispiegel, Notdusche, Rinne eckig, Siphon, Trichter-Siphon, Rückschlagklappe Flansch, Wärmetauscher allgemein, Wärmetauscher Rohrbündel, Bauteil Allgemein, Filter-Prozess, Filter-Steril, Heizung, Katalysator, Kolone
- **Feste Farbe in der Grafik:** 0 Stile – 
- **Feste Linienstärke in der Grafik:** 29 Stile – 3-Wege Umschalthahn, 3-Wege Umschalthahn Hand, 3-Wege Umschaltventil, 3-Wege Umschaltventil Hand, 3-Wege Umschaltventil Pneumatik, 4-Wege Umschalthahn, 4-Wege Umschaltventil, Absperrklappe, Absperrklappe Motor, Absperrklappe-Hand, Absperrklappe-Pneumatik, Automatische Entlüftung, Diffusor, Düse, Entleerung, Entlüftung, Feinfilter, Filter, Kappenventil, Regulierventil, Rohrtrenner, Rückschlagklappe, Rückspülfilter, Schauglas, Schmutzfänger, Volumenstromregler Einstellbar, Volumenstromregler Einstellbar Motor, Luftdurchlass Drall Draufsicht, Rückschlagklappe Flansch
- **Kürzel fehlt:** an allen 393 Stilen (siehe Kurzfassung). ATT führt die Kürzel in `ATT_kuerzel.csv` (aus dem AKS) – eine feste Zuordnung Stil → Kürzel gibt es in der Zeichnung nicht.
- **Ohne BeschreibungBauteil:** 33 – Serviceventil, Ölspiegelregulator, Antennendose, Bewegunsgmelder, Deckenleuchte, Gegensprechanlage, Netzwerkdose, Rauchmelder, Schalter, Schalter mit Kontrollleuchte, Steckdose 2-fach mit Schutzkontakt, Steckdose 3-fach mit Schutzkontakt, Steckdose 4-fach mit Schutzkontakt, Steckdose 5-fach mit Schutzkontakt, Steckdose mit Schutzkontakt, Telefondose, Wandleuchte, Hosen-Bogen, T-Bogen, Verbindungspunkt, Pfeil Abströmung, Pfeil Druckausgleich, Pfeil Zuströmung, Pfeil, Pfeil 3-Wege, Pfeil Gefälle, Pfeil Richtung, Aufbau dreifach, Aufbau_dreifach, Bauteil Allgemein, Heizung, MedienPunkt, Schnittstelle; ohne jeden Eigenschaftssatz am Stil: 12.
- **Anschlüsse ohne Namen:** 1205 von 1206 Anschlüssen haben keine Beschreibung – für ANA (Schnittstelle Anschlussnamen) und ATT nicht unterscheidbar.
- **Zwei Verbinderstile im Einsatz:** „Schaltbildverbinderstil“ (16 Stile), „Schematic Connector Style“ (5 Stile) – deutsch und englisch nebeneinander (Datenpunkte/Pfeile englisch).
- **Fehlende Stile:** 76 Symbole des Nutzers gibt es nur als DXF-Block, nicht als Schemasymbolstil (siehe 1).

## 3. Schemasystemdefinitionen

99 Systeme, alle mit LabelName. Ein Verbinderstil ist an der Systemdefinition nicht lesbar hinterlegt (nur an den Anschlüssen der Symbole, siehe 2).

| System | Kürzel (LabelName) | Gewerk (FamilyName) | Beschreibung |
|---|---|---|---|
| Abgas | AG | Heizung | Abgas von Verbrennungsmaschinen |
| Abluft | ETA | Lüftung | Abluft (ETA) |
| Acetylen | AC | Technische Gase | Acetylen |
| Aerosol-Aufgabe | AEA | Allgemein | Leitung für Aerosol-Aufgabe |
| Aerosol-Messung | AEM | Allgemein | Leitung für Aerosol-Messung |
| Aqua-Purificata | AP | Prozess-/Reinmedien | Aqua-Purificata-Vorlauf |
| Atemluft | ATL | Technische Gase | Atemluft |
| Aussenluft | ODA | Lüftung | Aussenluft (ODA) |
| Be-Entlüftung | BEENTLUE | Sanitär | Entlüftung |
| Brauchwasser | BW | Sanitär | Brauchwasser |
| Cleaning in Place | CIP | Prozess-/Reinmedien | Cleaning in Place |
| CO2-Druckleitung | CO2-D | Kälte |  |
| CO2-Saugleitung | CO2-S | Kälte |  |
| Dampf 2.5bar | D-2.5 | Medien | Dampf 2.5bar (ü) |
| Dampf 20bar | D-20 | Medien | Dampf 20bar (ü) |
| Dampf 8.0bar | D-8.0 | Medien | Dampf 8.0bar (ü) |
| Demontage | DEM | Heizung | Demontage |
| Differenzdruck | DID | Allgemein | Dofferenzdruck |
| Druckausgleich | DA | Lüftung | Druckausgleich |
| Druckluft | LD | Technische Gase | Druckluft |
| Eiswasser-Rücklauf | EIS-RL | Medien | Eiswasser Rücklauf |
| Eiswasser-Vorlauf | EIS-VL | Medien | Eiswasser Vorlauf |
| Entleerung | ENTLE | Sanitär | Entleerung |
| Entlüftung | ENTL | Sanitär | Entlüftung |
| Entrauchung | ENT | Lüftung | Entrauchung |
| Feuerlöschleitung-Nass | FLN | Sprinkler/Feuerlöschtechnik | Feuerlöschleitung-Nass |
| Feuerlöschleitung-Trocken | FLT | Sprinkler/Feuerlöschtechnik | Feuerlöschleitung-Trocken |
| Flüssigsalz | FS | Medien | Flüssigsalz |
| Fortluft | EHA | Lüftung | Fortluft (EHA) |
| Fäkalabwasser | FA | Sanitär | Fäkalabwasser |
| Fäkalabwasser Druckleitung | FADL | Sanitär | Fäkalabwasser Druckleitung |
| Highly Purified Water | HPW | Prozess-/Reinmedien | Highly Purified Water |
| Klima-Kalt-Wasser-Rücklauf | KKW-RL | Medien | Klima-Kalt-Wasser-Rücklauf |
| Klima-Kalt-Wasser-Vorlauf | KKW-VL | Medien | Klima-Kalt-Wasser-Vorlauf |
| Kondensat Dampf 2.5bar | KD-2.5 | Medien | Kondensat Dampf 2.5bar |
| Kondensat Dampf 20bar | KD-20 | Medien | Kondensat Dampf 20bar |
| Kondensat Dampf 8.0bar | KD-8.0 | Medien | Kondensat Dampf 8.0bar |
| Kondensat Kühlung | KOK | Sanitär | Kondensat Allgemein |
| Kondensat-Dampf-Allgemein | KDA | Medien | Kondensat-Dampf-Allgemein |
| Kondensat-Reindampf Klima | KRDK | Medien | Kondensat-Reindampf |
| Kondensat-Reinstdampf | KRSD | Medien | Kondensat-Reinstdampf |
| Kühl-Wasser-Rücklauf | KW-RL | Medien | Kühl-Wasser-Rücklauf |
| Kühl-Wasser-Rücklauf-sekundär | KW-RL-S | Medien | Kühl-Wasser-Rücklauf |
| Kühl-Wasser-Verwurf | KW-VE | Medien | Kühlwasser Verwurf |
| Kühl-Wasser-Vorlauf | KW-VL | Medien | Kühl-Wasser-Vorlauf |
| Kühl-Wasser-Vorlauf-sekundär | KW-VL-S | Medien | Kühl-Wasser-Vorlauf |
| Mischabwasser | MA | Sanitär | Mischabwasser |
| Mischabwasser-Druckleitung | MADL | Sanitär | Druckleitung |
| Mischluft | MIA | Lüftung | Mischluft (MIA) |
| NH3-Druckleitung | NH3-D | Kälte |  |
| NH3-Saugleitung | NH3-S | Kälte |  |
| Notentwässerung | NOEW | Sanitär |  |
| Produktionsabwasser | PA | Sanitär | Produktionsabwasser |
| Produktionsabwasser belastet | PAK3b | Sanitär |  |
| Produktionsabwasser Grundleitung | PAGL | Sanitär |  |
| Propan | PR | Technische Gase | Propan |
| Prozessabluft | PEA | Lüftung | Prozessabluft (PEA) |
| Pumpen-Kalt-Wasser-Rücklauf | PKW-RL | Medien | Pumpen-Kalt-Wasser-Rücklauf |
| Pumpen-Kalt-Wasser-Vorlauf | PKW-VL | Medien | Pumpen-Kalt-Wasser-Vorlauf |
| Pumpen-Warm-Wasser-Rücklauf | PWW-RL | Heizung | Pumpen-Warm-Wasser-Rücklauf |
| Pumpen-Warm-Wasser-Vorlauf | PWW-VL | Heizung | Test-Pumpen-Warm-Wasser-Vorlauf |
| Regenwasser | RW | Sanitär | Regenwasser |
| Regenwasser-Druckleitung | RWDL | Sanitär | Druckleitung |
| Reindampf-Klima | RDK | Medien | Reindampf für Lüftungsanlagen |
| Reinstdampf | RSD | Prozess-/Reinmedien | Reinstdampf für Prozess |
| Schmutzabwasser | SA | Sanitär | Schmutzabwasser |
| Schmutzabwasser-Druckleitung | SADL | Sanitär | Druckleitung |
| Sicherheits-Abblaseleitung | SIAL | Medien | Sicherheitsabblaseleitung |
| Sole-Rücklauf | SO-RL | Kälte | Sole-Rücklauf |
| Sole-Vorlauf | SO-VL | Kälte | Sole-Vorlauf |
| Sprinkler-Nass | SPN | Sprinkler/Feuerlöschtechnik | Sprinkler Leitung Nass |
| Sprinkler-Trocken | SPT | Sprinkler/Feuerlöschtechnik | Sprinkler Leitung Trocken |
| Standard | STA | Allgemein | allne nicht zugeordneten Syteme |
| Steuerluft | LS | Technische Gase | Steuerluft |
| Stickstoff | N2 | Technische Gase | Stickstoff 6.0 |
| Synthetische Luft | SYL | Technische Gase | Synthetische Luft |
| Thermo-Öl-Rücklauf | TOERL | Medien | Thermo-Öl-Rücklauf |
| Thermo-Öl-Vorlauf | TOEVL | Medien | Thermo-Öl-Vorlauf |
| Trinkwasser-Kalt | TWK | Sanitär | Trinkwasser-Kalt |
| Trinkwasser-Warm | TWW | Sanitär | S-Trinkwasser-Warm |
| Trinkwasser-Zirkulation | TWZ | Sanitär | Trinkwasser-Zirkulation |
| Umlauf-Wasser | ULW | Medien | Umlauf-Wasser |
| Umluft | RCA | Lüftung | Umluft (RCA) |
| Undefiniert | UDF | Allgemein |  |
| Vakuum | VA | Technische Gase | Vakuum |
| Vollentsalztes-Wasser | VE | Prozess-/Reinmedien | Vollentsalztes-Wasser-Vorlauf |
| Wasser für Injektion | WFI | Prozess-/Reinmedien | Wasser für Injektionszwecke |
| Wasserstoff | H2 | Technische Gase | Wasserstoff |
| Wasserstoffperoxid | H2O2 | Prozess-/Reinmedien | H2O2 Wasserstoffperoxid |
| Weich-Wasser | WW | Sanitär | Weichwasser aus VE- und Trinkwasser |
| Wirklinie Fremd BMK | WLFBMK | Elektro | Wirklinie Fremd BMK |
| Wirklinie Gebäude BMK | WLGBMK | Elektro | Wirklinie Gebäude BMK |
| Wirklinie Monitoring BMK | WLMBMK | Elektro | Wirklinie Monitoring BMK |
| Wirklinie Prozess BMK | WLPBMK | Elektro | Wirklinie Prozess BMK |
| Wirklinie Trinkwasser Beprobung | WLTWB | Sanitär | Wirklinie Gebäude BMK |
| Wärme-Rück-Gewinnung-Rücklauf | WRG-RL | Heizung | Wärmerückgewinnung-Rücklauf |
| Wärme-Rück-Gewinnung-Vorlauf | WRG-VL | Heizung | Wärmerückgewinnung-Vorlauf |
| Zuluft | SUP | Lüftung | Zuluft (SUP) |
| Überströmung | UEST | Lüftung | Überströmung |

Doppelte Kürzel: keine.

## 4. Anzeigethemen (10)

| Thema | Art der Regel | Regeln | angelegt von | eingesetzt |
|---|---|---|---|---|
| ANA Bewertung | Wert aus Eigenschaftssatz (Text: OK / im Toleranzbereich / Rohrreibung zu hoch / Geschwindigkeit zu hoch) | 4 | ANA | nein |
| ANA Geschwindigkeit | Zahlenbereich aus Eigenschaftssatz (m/s) | 11 | ANA | ja |
| ANA Leistung | Zahlenbereich aus Eigenschaftssatz (kW) | 11 | ANA | ja |
| ANA Rohr DN | Nennweite (DN6 … ) | 20 | ANA | ja |
| ANA Rohrreibung | Zahlenbereich aus Eigenschaftssatz (Pa/m) | 13 | ANA | ja |
| DN Rohrleitung | Nennweite (DN6 … ) – trägt intern den Titel „ANA Rohrreibung“, also aus einem ANA-Thema kopiert | 20 | Vorlage (aus ANA-Thema abgeleitet) | nein |
| Medien | System (Bezeichnung „Systemname (Kürzel)“), Farbe ACI/RGB | 99 | Vorlage | ja |
| RohrKanalKlassen | Rohrklasse/Schemalinienstil (RK001 …) | 23 | Vorlage | ja |
| Standard | keine Regeln | 0 | MEP-Standard | nein |
| Stoffgruppen | System, gruppiert nach DIN 2403 / DIN EN 16798-3 („Gruppe - Systemname (Kürzel)“) | 99 | Vorlage | ja |

Die Bedingung einer Regel (welche Eigenschaft) speichert MEP ohne .NET-Schnittstelle; lesbar sind Titel, Bezeichnung und Farbe. „eingesetzt“ = im Modellbereich als Anzeigethema-Objekt platziert (laut ASGTHEMA).

### Regeln „Medien“ (99)

| Bezeichnung | Kürzel | Farbe |
|---|---|---|
| Abgas (AG) | AG | ACI 40 |
| Abluft (ETA) | ETA | RGB 11913995 |
| Acetylen (AC) | AC | ACI 40 |
| Aerosol-Aufgabe (AEA) | AEA | ACI 212 |
| Aerosol-Messung (AEM) | AEM | ACI 142 |
| Aqua-Purificata (AP) | AP | ACI 160 |
| Atemluft (ATL) | ATL | ACI 162 |
| Aussenluft (ODA) | ODA | ACI 70 |
| Be-Entlüftung (BEENTLUE) | BEENTLUE | ACI 40 |
| Brauchwasser (BW) | BW | ACI 120 |
| Cleaning in Place (CIP) | CIP | ACI 203 |
| CO2-Druckleitung (CO2-D) | CO2-D | ACI 34 |
| CO2-Saugleitung (CO2-S) | CO2-S | ACI 54 |
| Dampf 2.5bar (D-2.5) | D-2.5 | ACI 232 |
| Dampf 20bar (D-20) | D-20 | ACI 230 |
| Dampf 8.0bar (D-8.0) | D-8.0 | ACI 200 |
| Demontage (DEM) | DEM | ACI 254 |
| Differenzdruck (DID) | DID | ACI 252 |
| Druckausgleich (DA) | DA | RGB 1077396 |
| Druckluft (LD) | LD | ACI 25 |
| Eiswasser-Rücklauf (EIS-RL) | EIS-RL | ACI 142 |
| Eiswasser-Vorlauf (EIS-VL) | EIS-VL | ACI 102 |
| Entleerung (ENTLE) | ENTLE | ACI 55 |
| Entlüftung (ENTL) | ENTL | ACI 100 |
| Entrauchung (ENT) | ENT | ACI 20 |
| Feuerlöschleitung-Nass (FLN) | FLN | ACI 40 |
| Feuerlöschleitung-Trocken (FLT) | FLT | ACI 20 |
| Flüssigsalz (FS) | FS | ACI 82 |
| Fortluft (EHA) | EHA | ACI 31 |
| Fäkalabwasser (FA) | FA | ACI 22 |
| Fäkalabwasser Druckleitung (FADL) | FADL | ACI 22 |
| Highly Purified Water (HPW) | HPW | ACI 130 |
| Klima-Kalt-Wasser-Rücklauf (KKW-RL) | KKW-RL | ACI 200 |
| Klima-Kalt-Wasser-Vorlauf (KKW-VL) | KKW-VL | ACI 100 |
| Kondensat Dampf 2.5bar (KD-2.5) | KD-2.5 | ACI 232 |
| Kondensat Dampf 20bar (KD-20) | KD-20 | ACI 230 |
| Kondensat Dampf 8.0bar (KD-8.0) | KD-8.0 | ACI 200 |
| Kondensat Kühlung (KOK) | KOK | ACI 41 |
| Kondensat-Dampf-Allgemein (KDA) | KDA | ACI 130 |
| Kondensat-Reindampf Klima (KRDK) | KRDK | ACI 40 |
| Kondensat-Reinstdampf (KRSD) | KRSD | ACI 83 |
| Kühl-Wasser-Rücklauf (KW-RL) | KW-RL | ACI 100 |
| Kühl-Wasser-Rücklauf-sekundär (KW-RL-S) | KW-RL-S | ACI 162 |
| Kühl-Wasser-Verwurf (KW-VE) | KW-VE | ACI 104 |
| Kühl-Wasser-Vorlauf (KW-VL) | KW-VL | ACI 104 |
| Kühl-Wasser-Vorlauf-sekundär (KW-VL-S) | KW-VL-S | ACI 120 |
| Mischabwasser (MA) | MA | ACI 200 |
| Mischabwasser-Druckleitung (MADL) | MADL | ACI 42 |
| Mischluft (MIA) | MIA | ACI 22 |
| NH3-Druckleitung (NH3-D) | NH3-D | ACI 243 |
| NH3-Saugleitung (NH3-S) | NH3-S | ACI 15 |
| Notentwässerung (NOEW) | NOEW | ACI 160 |
| Produktionsabwasser (PA) | PA | ACI 90 |
| Produktionsabwasser belastet (PAK3b) | PAK3b | ACI 74 |
| Produktionsabwasser Grundleitung (PAGL) | PAGL | ACI 90 |
| Propan (PR) | PR | ACI 20 |
| Prozessabluft (PEA) | PEA | ACI 32 |
| Pumpen-Kalt-Wasser-Rücklauf (PKW-RL) | PKW-RL | ACI 222 |
| Pumpen-Kalt-Wasser-Vorlauf (PKW-VL) | PKW-VL | ACI 82 |
| Pumpen-Warm-Wasser-Rücklauf (PWW-RL) | PWW-RL | ACI 170 |
| Pumpen-Warm-Wasser-Vorlauf (PWW-VL) | PWW-VL | ACI 240 |
| Regenwasser (RW) | RW | ACI 160 |
| Regenwasser-Druckleitung (RWDL) | RWDL | ACI 160 |
| Reindampf-Klima (RDK) | RDK | ACI 214 |
| Reinstdampf (RSD) | RSD | ACI 244 |
| Schmutzabwasser (SA) | SA | ACI 42 |
| Schmutzabwasser-Druckleitung (SADL) | SADL | ACI 42 |
| Sicherheits-Abblaseleitung (SIAL) | SIAL | ACI 60 |
| Sole-Rücklauf (SO-RL) | SO-RL | ACI 140 |
| Sole-Vorlauf (SO-VL) | SO-VL | ACI 160 |
| Sprinkler-Nass (SPN) | SPN | ACI 102 |
| Sprinkler-Trocken (SPT) | SPT | ACI 142 |
| Standard (STA) | STA | ACI 252 |
| Steuerluft (LS) | LS | ACI 253 |
| Stickstoff (N2) | N2 | ACI 122 |
| Synthetische Luft (SYL) | SYL | ACI 90 |
| Thermo-Öl-Rücklauf (TOERL) | TOERL | RGB 1333186 |
| Thermo-Öl-Vorlauf (TOEVL) | TOEVL | RGB 1947946 |
| Trinkwasser-Kalt (TWK) | TWK | ACI 90 |
| Trinkwasser-Warm (TWW) | TWW | ACI 230 |
| Trinkwasser-Zirkulation (TWZ) | TWZ | ACI 30 |
| Umlauf-Wasser (ULW) | ULW | ACI 200 |
| Umluft (RCA) | RCA | ACI 30 |
| Undefiniert (UDF) | UDF | ACI 252 |
| Vakuum (VA) | VA | ACI 35 |
| Vollentsalztes-Wasser (VE) | VE | ACI 240 |
| Wasser für Injektion (WFI) | WFI | ACI 80 |
| Wasserstoff (H2) | H2 | ACI 40 |
| Wasserstoffperoxid (H2O2) | H2O2 | ACI 151 |
| Weich-Wasser (WW) | WW | ACI 134 |
| Wirklinie Fremd BMK (WLFBMK) | WLFBMK | ACI 220 |
| Wirklinie Gebäude BMK (WLGBMK) | WLGBMK | ACI 20 |
| Wirklinie Monitoring BMK (WLMBMK) | WLMBMK | ACI 142 |
| Wirklinie Prozess BMK (WLPBMK) | WLPBMK | ACI 3 |
| Wirklinie Trinkwasser Beprobung (WLTWB) | WLTWB | ACI 70 |
| Wärme-Rück-Gewinnung-Rücklauf (WRG-RL) | WRG-RL | ACI 190 |
| Wärme-Rück-Gewinnung-Vorlauf (WRG-VL) | WRG-VL | ACI 30 |
| Zuluft (SUP) | SUP | ACI 210 |
| Überströmung (UEST) | UEST | RGB 11913995 |

### Regeln „Stoffgruppen“ (99)

| Bezeichnung | Kürzel | Farbe |
|---|---|---|
| 1 Wasser - Aqua-Purificata (AP) | AP | ACI 80 |
| 1 Wasser - Brauchwasser (BW) | BW | ACI 81 |
| 1 Wasser - Eiswasser-Rücklauf (EIS-RL) | EIS-RL | ACI 82 |
| 1 Wasser - Eiswasser-Vorlauf (EIS-VL) | EIS-VL | ACI 83 |
| 1 Wasser - Entleerung (ENTLE) | ENTLE | ACI 84 |
| 1 Wasser - Feuerlöschleitung-Nass (FLN) | FLN | ACI 87 |
| 1 Wasser - Feuerlöschleitung-Trocken (FLT) | FLT | ACI 88 |
| 1 Wasser - Fäkalabwasser (FA) | FA | ACI 85 |
| 1 Wasser - Fäkalabwasser Druckleitung (FADL) | FADL | ACI 86 |
| 1 Wasser - Highly Purified Water (HPW) | HPW | ACI 89 |
| 1 Wasser - Klima-Kalt-Wasser-Rücklauf (KKW-RL) | KKW-RL | ACI 94 |
| 1 Wasser - Klima-Kalt-Wasser-Vorlauf (KKW-VL) | KKW-VL | ACI 95 |
| 1 Wasser - Kondensat Dampf 2.5bar (KD-2.5) | KD-2.5 | ACI 90 |
| 1 Wasser - Kondensat Dampf 20bar (KD-20) | KD-20 | ACI 91 |
| 1 Wasser - Kondensat Dampf 8.0bar (KD-8.0) | KD-8.0 | ACI 92 |
| 1 Wasser - Kondensat Kühlung (KOK) | KOK | ACI 96 |
| 1 Wasser - Kondensat-Dampf-Allgemein (KDA) | KDA | ACI 93 |
| 1 Wasser - Kondensat-Reindampf Klima (KRDK) | KRDK | ACI 97 |
| 1 Wasser - Kondensat-Reinstdampf (KRSD) | KRSD | ACI 98 |
| 1 Wasser - Kühl-Wasser-Rücklauf (KW-RL) | KW-RL | ACI 99 |
| 1 Wasser - Kühl-Wasser-Rücklauf-sekundär (KW-RL-S) | KW-RL-S | ACI 100 |
| 1 Wasser - Kühl-Wasser-Verwurf (KW-VE) | KW-VE | ACI 101 |
| 1 Wasser - Kühl-Wasser-Vorlauf (KW-VL) | KW-VL | ACI 102 |
| 1 Wasser - Kühl-Wasser-Vorlauf-sekundär (KW-VL-S) | KW-VL-S | ACI 103 |
| 1 Wasser - Mischabwasser (MA) | MA | ACI 104 |
| 1 Wasser - Mischabwasser-Druckleitung (MADL) | MADL | ACI 105 |
| 1 Wasser - Notentwässerung (NOEW) | NOEW | ACI 106 |
| 1 Wasser - Produktionsabwasser (PA) | PA | ACI 107 |
| 1 Wasser - Produktionsabwasser belastet (PAK3b) | PAK3b | ACI 109 |
| 1 Wasser - Produktionsabwasser Grundleitung (PAGL) | PAGL | ACI 108 |
| 1 Wasser - Pumpen-Kalt-Wasser-Rücklauf (PKW-RL) | PKW-RL | ACI 110 |
| 1 Wasser - Pumpen-Kalt-Wasser-Vorlauf (PKW-VL) | PKW-VL | ACI 111 |
| 1 Wasser - Pumpen-Warm-Wasser-Rücklauf (PWW-RL) | PWW-RL | ACI 112 |
| 1 Wasser - Pumpen-Warm-Wasser-Vorlauf (PWW-VL) | PWW-VL | ACI 113 |
| 1 Wasser - Regenwasser (RW) | RW | ACI 114 |
| 1 Wasser - Regenwasser-Druckleitung (RWDL) | RWDL | ACI 115 |
| 1 Wasser - Schmutzabwasser (SA) | SA | ACI 116 |
| 1 Wasser - Schmutzabwasser-Druckleitung (SADL) | SADL | ACI 117 |
| 1 Wasser - Sole-Rücklauf (SO-RL) | SO-RL | ACI 118 |
| 1 Wasser - Sole-Vorlauf (SO-VL) | SO-VL | ACI 119 |
| 1 Wasser - Sprinkler-Nass (SPN) | SPN | ACI 71 |
| 1 Wasser - Sprinkler-Trocken (SPT) | SPT | ACI 72 |
| 1 Wasser - Trinkwasser-Kalt (TWK) | TWK | ACI 73 |
| 1 Wasser - Trinkwasser-Warm (TWW) | TWW | ACI 74 |
| 1 Wasser - Trinkwasser-Zirkulation (TWZ) | TWZ | ACI 75 |
| 1 Wasser - Umlauf-Wasser (ULW) | ULW | ACI 76 |
| 1 Wasser - Vollentsalztes-Wasser (VE) | VE | ACI 77 |
| 1 Wasser - Wasser für Injektion (WFI) | WFI | ACI 78 |
| 1 Wasser - Weich-Wasser (WW) | WW | ACI 121 |
| 1 Wasser - Wärme-Rück-Gewinnung-Rücklauf (WRG-RL) | WRG-RL | ACI 79 |
| 1 Wasser - Wärme-Rück-Gewinnung-Vorlauf (WRG-VL) | WRG-VL | ACI 120 |
| 2 Wasserdampf - Dampf 2.5bar (D-2.5) | D-2.5 | ACI 10 |
| 2 Wasserdampf - Dampf 20bar (D-20) | D-20 | ACI 12 |
| 2 Wasserdampf - Dampf 8.0bar (D-8.0) | D-8.0 | ACI 14 |
| 2 Wasserdampf - Reindampf-Klima (RDK) | RDK | ACI 16 |
| 2 Wasserdampf - Reinstdampf (RSD) | RSD | ACI 18 |
| 2 Wasserdampf - Sicherheits-Abblaseleitung (SIAL) | SIAL | ACI 20 |
| 3 Luft - Abluft (ETA) | ETA | ACI 2 |
| 3 Luft - Aussenluft (ODA) | ODA | ACI 3 |
| 3 Luft - Be-Entlüftung (BEENTLUE) | BEENTLUE | ACI 250 |
| 3 Luft - Druckausgleich (DA) | DA | ACI 253 |
| 3 Luft - Entlüftung (ENTL) | ENTL | ACI 251 |
| 3 Luft - Entrauchung (ENT) | ENT | ACI 6 |
| 3 Luft - Fortluft (EHA) | EHA | ACI 36 |
| 3 Luft - Mischluft (MIA) | MIA | ACI 70 |
| 3 Luft - Prozessabluft (PEA) | PEA | ACI 52 |
| 3 Luft - Umluft (RCA) | RCA | ACI 30 |
| 3 Luft - Zuluft (SUP) | SUP | ACI 5 |
| 3 Luft - Überströmung (UEST) | UEST | ACI 9 |
| 4 Brennbare Gase - Acetylen (AC) | AC | ACI 50 |
| 4 Brennbare Gase - NH3-Druckleitung (NH3-D) | NH3-D | ACI 56 |
| 4 Brennbare Gase - NH3-Saugleitung (NH3-S) | NH3-S | ACI 58 |
| 4 Brennbare Gase - Propan (PR) | PR | ACI 51 |
| 4 Brennbare Gase - Wasserstoff (H2) | H2 | ACI 54 |
| 5 Nichtbrennbare Gase - Abgas (AG) | AG | ACI 40 |
| 5 Nichtbrennbare Gase - Atemluft (ATL) | ATL | ACI 42 |
| 5 Nichtbrennbare Gase - CO2-Druckleitung (CO2-D) | CO2-D | ACI 44 |
| 5 Nichtbrennbare Gase - CO2-Saugleitung (CO2-S) | CO2-S | ACI 46 |
| 5 Nichtbrennbare Gase - Druckluft (LD) | LD | ACI 48 |
| 5 Nichtbrennbare Gase - Steuerluft (LS) | LS | ACI 41 |
| 5 Nichtbrennbare Gase - Stickstoff (N2) | N2 | ACI 43 |
| 5 Nichtbrennbare Gase - Synthetische Luft (SYL) | SYL | ACI 45 |
| 5 Nichtbrennbare Gase - Vakuum (VA) | VA | ACI 47 |
| 7 Laugen - Cleaning in Place (CIP) | CIP | ACI 200 |
| 8 Brennbare Fluessigkeiten - Thermo-Öl-Rücklauf (TOERL) | TOERL | ACI 38 |
| 8 Brennbare Fluessigkeiten - Thermo-Öl-Vorlauf (TOEVL) | TOEVL | ACI 26 |
| 9 Nichtbrennbare Fluessigkeiten - Flüssigsalz (FS) | FS | ACI 32 |
| 9 Nichtbrennbare Fluessigkeiten - Wasserstoffperoxid (H2O2) | H2O2 | ACI 34 |
| – keine Gruppe - Aerosol-Aufgabe (AEA) | AEA | ACI 8 |
| – keine Gruppe - Aerosol-Messung (AEM) | AEM | ACI 8 |
| – keine Gruppe - Demontage (DEM) | DEM | ACI 8 |
| – keine Gruppe - Differenzdruck (DID) | DID | ACI 8 |
| – keine Gruppe - Standard (STA) | STA | ACI 8 |
| – keine Gruppe - Undefiniert (UDF) | UDF | ACI 8 |
| – keine Gruppe - Wirklinie Fremd BMK (WLFBMK) | WLFBMK | ACI 8 |
| – keine Gruppe - Wirklinie Gebäude BMK (WLGBMK) | WLGBMK | ACI 8 |
| – keine Gruppe - Wirklinie Monitoring BMK (WLMBMK) | WLMBMK | ACI 8 |
| – keine Gruppe - Wirklinie Prozess BMK (WLPBMK) | WLPBMK | ACI 8 |
| – keine Gruppe - Wirklinie Trinkwasser Beprobung (WLTWB) | WLTWB | ACI 8 |

Abgleich Systeme ↔ Thema Medien: Systeme ohne Regel: keine.

## 5. Einschätzung: „Symbolverwaltung bei ASG“

**Heute** erzeugt ASG nur seine eigenen, parametrischen Bauteile (Verteiler, Behälter, Wärmetauscher, Startsymbol) als
Schemasymbolstile: Grafik aus Parametern, Ansicht „Plan“, Anschlüsse mit Lage und Richtung, Verbinderstil der Zeichnung,
Füllung, Formdaten für ANA. Das Anlegen von Stilen samt Anschlüssen per Programm ist damit in MEP belegt.

**Konkret hieße „Symbolverwaltung bei ASG“:**

1. **Eine Definitionsliste als Quelle** (CSV/JSON im Repo, wie die Listen von ATT): je Symbol Name, Gruppe, Kürzel (aus dem
   AKS über ATT), Beschreibung, Grafikquelle (der DXF-Block des Nutzers), Einfügepunkt, Anschlüsse mit Lage, Richtung und
   **Namen**, Grafikregeln (Farbe/Linienstärke ByBlock oder ByLayer).
2. **Prüfen** (lesend, risikoarm): ein Befehl, der die Vorlage gegen die Liste prüft und die Auffälligkeiten aus Teil 2
   meldet – fehlende Stile, abweichende Anschlüsse, feste Linienstärken, Schreibweisen.
3. **Erzeugen/Aktualisieren** (schreibend): ASG legt fehlende Stile in der Vorlage an (z. B. die 76 DXF-Blöcke ohne Stil)
   und gleicht vorhandene an. Die MEP-Symbolverwaltung (Stilmanager, Werkzeugpaletten) bleibt das Werkzeug zum Einsetzen;
   ASG pflegt nur den Inhalt der Vorlage.

**Umfang:** groß. 393 vorhandene + 76 fehlende Symbole. Anschlussnamen fehlen fast überall (1205 von 1206) – sie
festzulegen ist Fachfrage, nicht Programmierung. 127 Symbole haben nur 1 Anschluss (meist Anbauteile wie Antriebe – ob
das so bleiben soll, entscheidet der Nutzer). Machbar in Stufen: erst Liste + Prüfen, dann Erzeugen der fehlenden, zuletzt
Angleichen vorhandener.

**Risiken:**

- **Stilnamen sind Schnittstelle:** Umbenennen bricht Bezüge in bestehenden Zeichnungen, in ATT-Tags/Listen, ADM-Auswertungen
  und der Erkennung von ANA. Schreibweisen nur für neue Stile vereinheitlichen oder mit einer Umbenennungsliste für alle Module.
- **Bestehende Zeichnungen:** Ein geänderter Stil kommt nur per Stilimport hinein; MEP überschreibt dabei gleichnamige
  Stile – Anschlüsse eingesetzter Symbole können sich verschieben (Leitungen lösen sich).
- **Grenzen der MEP-API:** Anschlüsse verbinden per Programm ist nicht belegt (ASG-5 Teil 2, eInvalidInput); Linienbruch
  beim Einsetzen macht MEP nicht von selbst (Handtest 23.10.); Bedingungen von Anzeigethemen sind nicht lesbar.
- **Doppelte Pflege** bis zum Umstieg: Vorlage von Hand und Liste nebeneinander → Liste muss die eine Quelle werden.
- **Aufwand und Testbarkeit:** jede Stiländerung braucht einen MEP-Nachweis (headless reicht für Anlegen/Prüfen, nicht für
  das Verhalten beim Einsetzen).

**Empfehlung:** Stufe 1 (Definitionsliste aus der Vorlage + DXF erzeugen, Prüfbefehl) zuerst – rein lesend, ohne Risiko
für bestehende Zeichnungen. Erzeugen erst nach den Entscheidungen unten.

## Entscheidungen für den Nutzer

1. **Schreibweise der Stilnamen** im Eichler-Hausstandard: Umlaute oder ae/oe/ue, Bindestrich oder Leerzeichen, Groß/klein –
   und gilt das nur für neue Stile oder werden vorhandene umbenannt (Bezüge in ATT/ADM/ANA beachten)?
2. **Kürzel am Stil:** ein Feld (z. B. `KurzZeichenSymbol`) im Satz „StilSchemaSymbol“, gefüllt aus dem AKS über ATT – ja/nein?
3. **Die 76 DXF-Blöcke ohne Stil** (u. a. Sammler-Verteiler 4–8-fach, Strang-Symbole, Elektro-Geräte, Brandschott): welche
   werden Schemasymbolstile? Sammler/Verteiler evtl. durch den ASG-Verteiler ersetzen?
4. **Die 23 Stile nur in der Zeichnung** (z. B. „Platten Wärmetauscher“, „Rohrbündel Wärmetauscher“, „Ventil allgemein“,
   Dublette „Aufbau dreifach / Aufbau_dreifach“): behalten, ins DXF-Set aufnehmen oder entfernen?
5. **Ein Verbinderstil** für alle Anschlüsse („Schaltbildverbinderstil“) statt deutsch/englisch gemischt?
6. **Einfügepunkt-Regel:** Bauteilmitte, Hauptanschluss oder frei? (47 Stile haben ihn nicht auf einem Anschluss.)
7. **Feste Linienstärken** in 29 Stilen auf ByBlock/ByLayer umstellen?
8. **Anschlussnamen:** für welche Bauteile festlegen (Vorrang: was ANA rechnet – Pumpen, Armaturen, Wärmetauscher, Behälter)?
9. **Anzeigethemen:** „DN Rohrleitung“ (Kopie eines ANA-Themas) und „Standard“ (leer) behalten? ANA-Themen fest in die
   Vorlage oder von ANA bei Bedarf anlegen lassen?
10. **Rolle von ASG:** nur Prüfen (Stufe 1–2) oder auch Erzeugen/Angleichen der Stile (Stufe 3)?
