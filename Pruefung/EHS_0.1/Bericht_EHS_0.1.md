# Bericht EHS 0.1 – leere Vorlage

Stand 23.10.2026 · erstellt von ASG mit `tools/ehs/EHS_bereinigen.ps1` (headless, wiederholbar)

- **Quelle:** Kopie von `Schema/Versionen/EHS_0.0_Basis_aus_RI_9.1_20261023.dwg`. Die Quelle selbst wurde nicht verändert.
- **Ergebnis:** `C:\Temp\AMK_Vorlage\EHS_0.1\EHS_0.1_leer.dwg`
- **Rohdaten:** `vorher.txt` (Inventur der Quelle), `plan.txt` (Plan und Ausführung), `nachher.txt` (Inventur des Ergebnisses), `lauf2/konsole.txt` (AUDIT).

## Gegenprobe

| Prüfung | Ergebnis |
|---|---|
| Ergebnis öffnet headless ohne Fehler | ja (Inventur des Ergebnisses vollständig gelaufen) |
| AUDIT (nur melden) | 0 Fehler gefunden, 0 behoben |
| Anzeigethemen vollständig | 10 von 10; Satz-Zeiger der Themen intakt: ja |
| Symbolstile | 416 von 416 (mit Kürzel 393, mit Ansichtsblock 415, wie vorher) |
| Systemdefinitionen | 99 von 99 |
| Fehler beim Entfernen | 0 |

Schon in der Quelle hatten 1 Stil(e) keinen gültigen Ansichtsblock und 23 Stile keine Beschreibung.

## Vorher und nachher

| Kategorie | vorher | nachher |
|---|---:|---:|
| Objekte gesamt | 40166 | 18915 |
| Objekte im Modellbereich | 3531 | 0 |
| Objekte im Layout „Vorlage“ | 9 | 9 |
| Eigenschaftssatzdefinitionen | 25 | 3 |
| Eigenschaftssätze (Instanzen) | 4312 | 0 |
| Bauteiltabellenstile | 14 | 0 |
| Mehransichtsblöcke | 48 | 0 |
| Blöcke (Blocktabelle) | 626 | 545 |
| Symbolstile | 416 | 416 |
| – davon mit Beschreibung (Kürzel) | 393 | 393 |
| – davon mit Ansichtsblock | 415 | 415 |
| Systemdefinitionen | 99 | 99 |
| Verbinderstile | 7 | 7 |
| Anzeigethemen | 10 | 10 |
| Eigenschaftsdatenformate | 57 | 57 |
| Layouts (mit Modell) | 2 | 2 |
| Layer | 29 | 22 |
| Linientypen | 16 | 16 |
| Textstile | 12 | 12 |
| Bemaßungsstile | 3 | 3 |
| RegApps | 93 | 51 |
| Fremde Wörterbücher LIN_* (NOD) | 16 | 16 |

## Was entfernt wurde

Ausführung: Sätze gelöst 677 | gelöscht 3705 | Fehler 0; RegApps gelöscht 45 von 45.

- **Modellbereich** (3531 Objekte): AecDbDisplayTheme 7, AcDbMText 29, AcDbLine 36, AcDbBlockReference 21, AecbDbSchematic 1226, AcDbText 17, AecbDbSchematicSymbol 671, AecbDbLabelCurve 144, AecDbMvBlockRef 619, AcDbPolyline 15, AcDbAttributeDefinition 20, AecDbScheduleTable 4, AcDbCircle 722. Darin stecken Leitungen, Symbole, Beschriftungen, ADM-Marken, Legenden der Anzeigethemen und Bauteiltabellen.
- **Eigenschaftssatzdefinitionen** (22): ANA_Armatur, BeprobungspunktTrinkwasser, EDaten, HVACRaum, PositionsAnker, SpaceEngineeringClassifications, SpaceEngineeringObjects, StilSchemaSymbol, TAGBMKFremd, TAGBMKGebauede, TAGBMKMonitoring, TAGBMKProzess, TAGBauteil, TAGDaemmung, TAGEntNahme, TAGMedium, TAGMessStutzen, TAGProbeNahme, TAGRLTFilter, TAGStrömung, ThermalProperties, ZoneEngineeringObjects.
- **Eigenschaftssätze** (4312 Instanzen). An bleibenden Objekten (Symbolstile, Systemdefinitionen u. a.) über die Schnittstelle gelöst: 677. Die übrigen hingen an Objekten im Modellbereich oder in entfernten Blöcken.
- **Bauteiltabellenstile** (14): HVACRaumBuch, Legende, LeistungsBilanz, MessStutzen, RLTFilterliste, RLTMessStutzen, Standard, Stückliste hydraulische Volumenstromregler, StücklisteArmaturen, StücklisteKühlerErhitzer, StücklisteMSRBMK, StücklistePumpen, StücklisteRegelVentile, StücklisteULK.
- **Mehransichtsblöcke TAG*** (48): TAGBauteil_01_01, TAGBauteil3Zeilig, TAGBauteil4Zeilig, TAGBauteilBemerkung_01_01, TAGBauteilDruck_01_01, TAGBauteilDurchFluss_01_01, TAGBauteilEinStellWert_01_01, TAGBauteilFabrikat_01_01, TAGBauteilGroesse_01_01, TAGBauteilGroesse_01_02, TAGBauteilLeistung_01_01, TAGBauteilModul_01_01, TAGBauteilPosNr_01_01, TAGBauteilPosNr_01_02, TAGBauteilRegelAbgleichVentil_01_01, TAGBauteilRegelVentil_01_01, TAGBauteilRegelVentil_02_01, TAGBauteilTyp_01_01, TAGBauteilZone_01_01, TAGBeprobungspunktTrinkwasser_01_01, TAGBMKFremd_01_01, TAGBMKGebauede_01_01, TAGBMKMonitoring_01_01, TAGBMKProzess_01_01, TAGBMKProzess_01_02, TAGBMKProzess_01_03, TAGDaemmung_01_01, TAGDaemmung_01_02, TAGEntNahme_01_01, TAGFilterRLT_01_01, TAGFilterRLT_01_02, TAGFilterRLT_01_03, TAGFilterRLT_01_04, TAGFilterRLT_01_05, TAGFilterRLT_01_06, TAGFilterRLT_01_08, TAGFilterRLT_01_09, TAGFilterRLT_01_10, TAGFilterRLT_01_11, TAGFilterRLTDurchFluss_01_01, TAGHVACRaum_01_01, TAGHVACRaum_01_02, TAGHVACRaum_01_03, TAGHVACRaum_05_01, TAGHVACRaum_06_01, TAGHVACRaum_07_01, TAGProbeNahme_01_01, TAGRohrleitung_02_01.
- **Legendenblöcke eaklLeg-*** (23): eaklLeg-2-Wege Regelventil Motor, eaklLeg-Absperrklappe-Hand, eaklLeg-Airbreak Abluft, eaklLeg-Drosselklappe Lüftung Motor, eaklLeg-eakl3, eaklLeg-eakl4, eaklLeg-Erhitzer Zone, eaklLeg-Filter Fan Unit, eaklLeg-Kugelhahn, eaklLeg-Luftdurchlass Abströmend, eaklLeg-Luftdurchlass Filter Abströmend, eaklLeg-Luftdurchlass Filter Zuströmend, eaklLeg-Luftdurchlass Zuströmend, eaklLeg-Messstutzen Luft, eaklLeg-Pfeil Richtung, eaklLeg-Pumpe, eaklLeg-Reduzierung, eaklLeg-Schalldämpfer, eaklLeg-Schmutzfänger, eaklLeg-Volumenstromregler Einstellbar Motor, eaklLeg-Volumenstromregler konstant, eaklLeg-Volumenstromregler variabel mit Motor, eaklLeg-Wärmetauscher Platte.
- **Blöcke, die nur von Entferntem benutzt wurden** (58): LegendeDämmRohrklassenTag, LegendeRaumstempel, LegendeRohrleitungsBerechnungsTag, LegendeSchwebstofffilterkasten, TAGBauteil_01_01, TAGBauteil3Zeilig, TAGBauteil4Zeilig, TAGBauteilBemerkung_01_01, TAGBauteilDruck_01_01, TAGBauteilDurchFluss_01_01, TAGBauteilEinStellWert_01_01, TAGBauteilFabrikat_01_01, TAGBauteilGroesse_01_01, TAGBauteilGroesse_01_02, TAGBauteilLeistung_01_01, TAGBauteilModul_01_01, TAGBauteilPosNr_01_01, TAGBauteilPosNr_01_02, TAGBauteilRegelAbgleichVentil_01_01, TAGBauteilRegelVentil_01_01, TAGBauteilRegelVentil_02_01, TAGBauteilTyp_01_01, TAGBauteilZone_01_01, TAGBeprobungTrinkwasser_01_01, TAGDaemmung_01_01, TAGDaemmung_01_02, TAGEntNahme_01_01, TAGFilterRLT_01_01, TAGFilterRLT_01_02, TAGFilterRLT_01_03, TAGFilterRLT_01_04, TAGFilterRLT_01_05, TAGFilterRLT_01_06, TAGFilterRLT_01_08, TAGFilterRLT_01_09, TAGFilterRLT_01_10, TAGFilterRLT_01_11, TAGFilterRLTDurchFluss_01_01, TAGFremdBMK_01_01, TAGGebauedeBMK_01_01, TAGHVACRaum_01_01, TAGHVACRaum_01_02, TAGHVACRaum_01_03, TAGHVACRaum_05_01, TAGHVACRaum_06_01, TAGHVACRaum_07_01, TAGMonitoringBMK_01_01, TAGProbeNahme_01_01, TAGProzessBMK_01_01, TAGProzessBMK_01_02, TAGProzessBMK_01_03, TAGRohrleitung_02_01 sowie 6 anonyme Blöcke (*U…). Das sind Ansichtsblöcke der TAG-Mehransichtsblöcke, Legenden- und Stempelblöcke.
- **Modul-Spuren:** Wörterbucheinträge ANA_DIMENSIONIERUNG, ATT_REGISTER; RegApps ADM_MARKE, ANA_VERTEILER, ASG_BAUTEIL; Layer ADM_Marke, NA_BYPASS, NA_DN_WECHSEL, NA_OFFENE_ENDEN, NA_REDUZIERUNG, NA_TEILSTRECKEN, NA_VERZWEIGUNGEN. ADM und ANA legen sie bei Bedarf selbst neu an. `ADM_EICHLER` war nicht vorhanden.
- **Unbenutzte RegApps** (42): Kein bleibendes Objekt nutzt sie in XData. AutoCAD-eigene (AC*, AEC*) bleiben. Gelöscht wird über `Database.Purge` wie bei PURGE. Ohne diesen Weg holt AutoCAD sie beim Speichern zurück.

Es gab **kein pauschales PURGE**. Unbenutzte Symbolstile, Systemdefinitionen, Verbinderstile, Layer, Linientypen, Text- und Bemaßungsstile bleiben.

## Was bleiben musste, und warum

- **3 Eigenschaftssatzdefinitionen** bleiben, ohne Instanzen:
  - AecDbPropertySetDef „StilSchemaRohrKanal“ [1F5DE] | bleibt wegen AecDbDisplayThemeStyle „Medien“ [1FC49]
  - AecDbPropertySetDef „AecPolygonStil“ [1FC8F] | bleibt wegen AecDbDisplayThemeStyle „Medien“ [1FC49]
  - AecDbPropertySetDef „ANA_Hydraulik“ [440B3] | bleibt wegen AecDbDisplayThemeStyle „ANA Rohrreibung“ [44139]
  Die Anzeigethemen verweisen auf diese Definitionen **per Objektzeiger** (SoftPointer im Thema), nicht nur über den Namen.
  - `StilSchemaRohrKanal`: Medien, RohrKanalKlassen, Stoffgruppen
  - `AecPolygonStil`: ANA Bewertung, ANA Geschwindigkeit, ANA Leistung, ANA Rohr DN, ANA Rohrreibung, DN Rohrleitung, Medien, RohrKanalKlassen, Stoffgruppen
  - `ANA_Hydraulik`: ANA Bewertung, ANA Geschwindigkeit, ANA Leistung, ANA Rohr DN, ANA Rohrreibung, DN Rohrleitung
  Ohne die Definition zeigen die Regeln ins Leere. ANA hält die Regeln auch per Name (PropertyOwnerName/PropertyName). ANA verwendet die bleibende Definition weiter (Headless-Test ANA, siehe unten).
- **Blöcke, die nur im Modellbereich eingesetzt waren** und weder Stempel noch Legende sind (Entscheidung AMK): Beschrifter_01, Zeichnungsbereich im Modell, Beschrifter_02, ZeichnungsVerweis_02, ZeichnungsVerweis_01, Z_Hoehenkote, ZeichnungsVerweis_03. Sie bleiben als Definition.
- **Fremde Wörterbücher `LIN_*`** (16 im NOD, u. a. Disciplines, Gewerke, Medien, Komponenten): **offen – Nutzer** (Vorgabe AMK: vorerst drin lassen). Entfernen per zweitem Lauf: `EHS_bereinigen.ps1 -FremdeWoerterbuecher LIN_`.
- **3 RegApps ohne Benutzer** entstehen während des Bereinigungslaufs neu, vermutlich legt MEP sie beim Laden oder Speichern an (neue Handles, keine XData, keine Zeiger). Sie sind harmlos; ein PURGE in MEP kann sie entfernen, sie kommen aber wohl wieder.
- **4 RegApps (außer AC*/AEC*) mit Benutzern** bleiben, vor allem XData an Schraffuren und Polylinien in Symbolblöcken.
- **Layout „Vorlage“** ist unverändert (AcDbViewport×3, AcDbDictionary×1, AcDbBlockBegin×1, AcDbBlockEnd×1, AcDbMText×1, AcDbBlockReference×2). Blöcke: *U537 (Layer Z_Rahmen), Aspire_TB_A2 (Layer Z_Plankopf). Ein anonymer Rahmenblock bekommt beim Speichern einen neuen Namen (*U…). Das ist AutoCAD-üblich.
- **Eigenschaftsdatenformate** (57) bleiben. Sie sind keine Satzdefinitionen und tragen keine Daten.

## Hinweise für die Module

- **Stand der Feststellungen** zu ANA und LIN_* (Lauf 23.10.2026) unten bitte bei einem neuen Lauf gegenlesen.
- **ANA, Headless-Test an einer Kopie von EHS 0.1: bestanden.** Belege in `C:\Temp\ANA_EHS01\`. Ablauf: speichern, öffnen, Mini-Netz einklonen, rechnen, NETZANALYSE_THEMA, speichern, öffnen.
  - `StelleDefinitionSicher` verwendet `ANA_Hydraulik` [440B3] weiter und ergänzt nur fehlende Felder. Handle und 127 Felder bleiben gleich.
  - Alle Themenregeln zeigen in jedem Schritt auf 440B3, 1FC8F bzw. 1F5DE. Die Werte passen zu den Regeln.
  - `ANA_Armatur` wird beim Rechnen sauber neu angelegt.
  - Ob die Leitungen sichtbar gefärbt werden, ist nur in MEP prüfbar (Legende einfügen, Thema anwenden).
- **Altlast beim Einkopieren aus alten Zeichnungen (Befund ANA):** Beim Einklonen (wie Einfügen/INSERT) legt AEC eine abweichende alte Definition als „ANA_Hydraulik (2)“ an.
  - Die Eingaben landen dort, und ANA rechnet ohne sie.
  - TAGBauteil, EDaten, TAGBMK*, TAGDaemmung, TAGRLTFilter, HVACRaum und PositionsAnker kommen als Definitionen wieder herein.
  - Dabei ging auch die DN der Leitungen verloren.
  - Echtes Kopieren und Einfügen in MEP ist ungeprüft. Folgearbeit für ANA (Werte aus „(2)“ übernehmen) nur nach Go des Nutzers.
- **Themen (Befund ANA):** „ANA Rohr DN“ ist ein altes Thema, ANA nutzt nur noch „DN Rohrleitung“. Ob es raus soll, entscheidet der Nutzer. „ANA Druckverlust“ fehlt, NETZANALYSE_THEMA legt es bei Bedarf an.
- **ATT/ADM:** `TAGBauteil` und alle TAG*-Sätze, Stempel (TAG-Mehransichtsblöcke) und Bauteiltabellen fehlen in EHS 0.1 bewusst. Sie werden neu gebaut (Basis-Satz EHS_Bauteil später).
- **Wiederholen:** `powershell -File tools\ehs\EHS_bereinigen.ps1` (Schalter `-Trocken` nur Inventur und Plan), dann `python -I -X utf8 tools\ehs\ehs_bericht.py C:\Temp\AMK_Vorlage\EHS_0.1`.
