# Entscheidungsliste EHS 1.0 – alle offenen Punkte an einer Stelle

Stand 23.10.2026 · AMK. Ersetzt die offenen Punkte der `Entscheidungsliste_EHS_0.1.md`. Grundlage: Bauplan „grüne Wiese“
(`Bauplan_EHS.md`), Stammdaten-Entwürfe der Module (`C:\Temp\AMK_Vorlage\Stammdaten_Entwurf\`), Prüfungen von ATT, ADM,
ANA, ASG, AVT.

**So antworten Sie:** „alle Empfehlungen ja“ – oder je Punkt die Nummer mit „ja“, eigener Angabe oder „später“.
Beispiel: `alle ja, außer K3: Kugelhahn bleibt Absperrarmatur · T1 später`. Die ★-Punkte zuerst, sie blockieren den Bau.

---

## Schon entschieden (nicht mehr fragen)

Grüne Wiese, Vorlage aus Stammdaten (AVT) · Name bleibt EHS, umschwenkbar · Ablage Schema-Ordner = Live, AVT = Werkstatt ·
Versionen x.y.z, Freigabe nur durch Sie, Versionskette, DWGPROPS vor jeder Fassung · Kern + Büro + Kunde · Stammdaten
führend, AKS abgeleitet · ASG verwaltet Symbole, Prüfung vor Aufnahme · A0 auf 0,0 + A1…An ab 9 Uhr im Uhrzeigersinn ·
Kürzel in Anlehnung an DIN EN IEC 81346-2:2020-10 · Symbole gewerkeneutral · Elektro entfällt, Geschirrspüler/Waschmaschine bleiben ·
Testzeichnungen nur als Derivate · Corporate Design · liNear bleibt (Bereinigen in AVT) · Pumpe 01PUM03 bleibt ·
Materialwechsel 1 Anschluss · AVT-Farbe anthrazit · leere Vorlage ohne Zeichnungsobjekte (G1, folgt aus „grüne Wiese“) ·
alte TAG-Stempel und Bauteiltabellen werden ersetzt, nicht repariert.

---

## ★ N – Namen und Kürzel (blockiert ASG v2)

| Nr | Frage | Empfehlung |
|---|---|---|
**Entschieden 23.10. (Nutzer an ASG):** Grundlage DIN EN IEC 81346-2:2020-10, Tabelle des Nutzers
`Desktop\DIN_EN_81346-2_3_Ebene_HLK_Bibliothek.xlsx` (z. B. GPA Umwälzpumpe, QMA Absperrarmatur, QMB Regel-/Mischventil,
QNA BSK, QNC VSR, TAA Platten-WT, CBB Puffer, FBA MAG, FCA SiV; Filter = ND). **TAG = Anlage 2 Ziffern + Kürzel genau
2 Kennbuchstaben + Zählnummer 3 Ziffern = 7 Zeichen, ohne Trennstriche** (Nutzer: „Zählnummer geht bis 999 … 01GP999“).
Keine Bauart im Kürzel – der TAG bleibt stabil, wenn ein Kugelhahn gegen eine Klappe getauscht wird. Alte und neue Kürzel
nie gemischt in einer Zeichnung (alt TAA = Abscheider, neu = Platten-WT), Umstellen nur über die Liste alt → neu.

| Nr | Frage | Empfehlung |
|---|---|---|
| ★N1 | Die 3. Ebene Ihrer Tabelle (GPA, QMA, QMB …) wird Angabe **„Unterklasse“** am Symbol, die genaue Armaturart (Regelventil 2-Wege, PICV, Kugelhahn … – 30 Arten laut ANA) Angabe **„Bauart“** am Symbol; beides schreibt ASG, nichts davon im TAG (Vorschlag ASG) | ja |
| ★N2 | Klassen für Bereiche, die Ihre Tabelle noch nicht hat (Sanitär, Formstücke, Verbindungen, Luftdurchlässe, Messstutzen …): aus dem Normtext ergänzen, nicht raten | bitte Normtext bzw. Ergänzung an ASG |
| N3 ✔ | **Entschieden 23.10.** („find ich gut so“, ohne 4. Zeichen): Stilname = `<Unterklasse 3 Zeichen> <Benennung> [- Betätigung] [- Ausführung]`, z. B. „QMB Regelventil 2-Wege - Motor“, „GPA Pumpe - doppelt“, „NDB Schmutzfänger“; mit Umlauten, ohne ß, Tippfehler korrigiert | ja |
| N5 ✔ | Erledigt 23.10.: Wärmetauscher und Behälter sind parametrisch (ASG-Generatoren), die festen Wärmetauscher-/Behälter-Stile werden ersetzt (Namensliste v8) | erledigt |
| N4 | Antriebsvarianten (Hand/Motor/Pneumatik) nur im Stilnamen, Wasser- und Luftarmaturen getrennt | ja |
| N5 | 4 Dubletten zusammenlegen (Aufbau 3-fach, Wärmetauscher Platten, Wärmetauscher Rohrbündel, Rührwerk) – eine ID bleibt, Grafik vorher verglichen | ja |
| N6 | 9 offene Elektro-nahe Stile (WP-Außen-/Innenteil, Temperaturfühler, Raumthermostat, E-Heizkörper, Durchlauferhitzer, Ventilator, Motor): in die passende Familie statt entfallen | ja, Zuordnung ASG |

## ★ F – Felder (blockiert AVT 0.4 Erzeugen)

| Nr | Frage | Empfehlung |
|---|---|---|
| ★F1 | **Begriffe eindeutig machen** (Vorschlag ADM, angepasst an N): **Familie** = 1. Kennbuchstabe = Hauptklasse der Norm (Gruppen in Legende/Stückliste/Excel) · **Kürzel** = 2 Kennbuchstaben (im TAG) · **Unterklasse** und **Bauart** = Angaben am Symbol (ASG; ANA erkennt daran) · **Bauteilart** = Funktion im Netz (ANA) · **Benennung** = Stilname ohne Kürzel | ja |
| F2 | Datenblattwerte (Nennleistung, Volumenstrom, Δp, Anschluss-DN, Wasserinhalt, P1) in `EHS_Bauteil`, Rechenergebnisse bleiben in ANA (ADM und ANA einig) | ja |
| F3 | Hersteller/Typ/Artikelnummer an einem Ort (`EHS_Bauteil`); ANA schreibt nur auf Knopfdruck „Übernehmen“ | ja |
| F4 | Kennzeichen-Teilfelder `Anlage` und laufende Nummer; Grundregel `{Anlage}{Kürzel}{Nummer}` (z. B. `01GP001`, entschieden) | ja |
| F5 | Sperre und Ausschluss als Spiegel am Bauteil sichtbar (`KennzeichenGesperrt`, `Taggen`) | ja |
| F6 | Kennung (GUID) vergibt das Modul, das den Satz anhängt (meist ASG beim Einfügen); ADM repariert nur auf Befehl | ja |
| F7 | Medium am System/Kreis, nicht am Bauteil; Projektwahl (z. B. Antifrogen) als ANA-Eingabe am Erzeuger | ja |
| F8 | Begleitsätze: 4 × `TAGBMK*` → `EHS_BMK`; `TAGRLTFilter` → `EHS_Filter`; Leitungen bekommen schlanken Satz `ANA_Leitung` | ja |
| F9 | Feld `Druck` (bar) aus alten Stempeln: erst aufnehmen, wenn die Bedeutung klar ist | später |
| F10 | Räume bleiben möglich (`EHS_Raum`, Raumbuch), ohne Räume nehmen Listen die Zone | ja |

## S – Symbole und Grafik

| Nr | Frage | Empfehlung |
|---|---|---|
| S1 | Füllung als Ausnahme von „VonBlock“ (ASG-Füllregel) | ja |
| S2 | Einfügepunkt: Durchgangsbauteile Mitte auf der Leitungsachse, Geräte/Behälter Mitte des Körpers (A3) | ja |
| S3 | Fließrichtung +X bei Pumpe, Rückschlagarmatur, Pfeil, Reduzierung (große Seite → klein) (A7) | ja |
| S4 | Pflichtanzahl Anschlüsse je Bauteilart nach ANA-Tabelle (A6); 36 Stile werden angeglichen (u. a. alle Umluftgeräte, Konvektor) | ja |
| S5 | Fehlende Stile (A4): Hydraulik, Brandschott, Heizkörper werden Stile; Sammler/Verteiler 4–8-fach durch ASG-Verteiler; Strangsymbole später | ja |
| S6 | ASG-eigene Bauteile auf A0/A1…An umstellen (neue Formversion + Übergang, mit ANA) | ja |

## E – ANA-Einordnung der Bauteile

| Nr | Frage | Empfehlung |
|---|---|---|
| E1 | ANA erkennt im Hausstandard über **Kürzel + Unterklasse + Bauart am Symbol** (Stammdaten); Stilwörter nur Rückfall für alte Zeichnungen | ja |
| E2 | **Berichtigt (ANA 23.10.):** Volumenstromregler „Einstellbar Motor“ = **PICV**, „Einstellbar“ = **PIBV** – so seit 09.10. mit dem Fachplaner abgestimmt (die frühere Empfehlung „beide PICV“ war falsch) | bestätigen |
| E3 | Druckreduzierung → „Druckminderer“ (Ventil mit Δp) · Umluftgeräte mit Ventil = Verbraucher · Differenzdruck-Messung = Messstelle · 3-Wege-Hahn/Umschalter = Umschaltarmatur | ja |
| E3c | „Absperrventil Differenzdruck (mit Prüfanschluss)“: Strangabsperrventil oder Partnerventil? | Ihre Angabe |
| E4 | Bisher nicht erkannte Armaturen nach ANA-Tabelle einordnen; abweichend: Regulierventil = Strangregulierventil, KFR-Ventil = Rückschlagventil, Verschneide-Armatur = 3-Wege-Regelventil | ja |
| E5 | Neu gefundene Fragen (ANA): Abscheider wie Schmutzfänger · Pufferspeicher mit WT = Weiche + Trennung · Tauch-/Hebe-/Vakuumpumpen nicht rechnen · Wärmemengenzähler mit Δp · Rückkühler/WRG = Verbraucher · Frischwasserstation = Systemtrennung · Speicher-Wassererwärmer = Verbraucher | ja |

## Y – Systeme, Farben, Themen

| Nr | Frage | Empfehlung |
|---|---|---|
| Y1 | System-Kürzel: Vorlage führend (KW-VL-S, D-8.0, BEENTLUE, WL…BMK); nur Thermo-Öl wird TOE-VL/TOE-RL (B1) | ja |
| Y2 | FLN/FLT: neue Themenfarben (ACI 40/20) gewollt, kein Versehen (B3) | bitte bestätigen |
| Y3 | 13 Systeme fehlen im AKS (AG, AC, DEM, KOK, MADL, NOEW, PAGL, PR, SPN, SPT, STA, SYL, UDF): AKS wird aus den Stammdaten ergänzt; AKS-Nr. und Gewerk vergibt ATT (B2) | ja |
| Y4 | Alte Lüftungskürzel AB, ZU, UM, AU, FO, MI streichen (EN 16798) (B4) | ja |
| Y5 | PWW im Standard = Wasser, Antifrogen nur im Projekt; `Kreise.json` an Y1 angleichen (B6) | ja |
| Y6 | In der Vorlage: Themen Medien, Stoffgruppen, RohrKanalKlassen; ANA-Themen legt ANA bei Bedarf an (D1) | ja |

| Y7 ✔ | **Entschieden 23.10.** (Nutzer: „Die Rohrklassen nur adaptieren, keine neuen erfinden. Hier auch jeglichen Hinweis auf Roche eliminieren.“): Die vorhandenen Rohrklassen (heute RK001…RK434) werden als `Stammdaten\Rohrklassen.csv` übernommen – Inhalt (Werkstoff, Norm, DN, Maße, Rauigkeit …) bleibt, jeder Roche-Bezug (Namen, Quellangaben, Kundenkennungen) entfällt; fachlich gepflegt von ANA | erledigt |

## L – Listen und Plankopf (ADM)

| Nr | Frage | Empfehlung |
|---|---|---|
| L1 | ADM füllt alle Listen (eine Listendefinition, Excel daraus); ANA löst nur „Listen aktualisieren“ aus (F1) | ja |
| L2 | AutoCAD-Tabellen `EHS_Liste` für Fachlisten und Legende; AEC-Tabelle nur fürs Raumbuch; live mitlaufende Stückliste (F2) | ja |
| L3 | Reihenfolge: Ventilliste, Einstellliste, Pumpenliste, Legende zuerst (F3) | ja |
| L4 | Legende als von ADM gefüllte Tabelle, Legendenblöcke entfallen (F4) | ja |
| L5 | Eichler-Plankopf mit Attributen (Projekt, Plan-Nr., Index, Datum) im Büro-Profil (D3) | ja |
| ★L6 | **Schrift und Textstile im Kern** (Roche-Schrift ROCHL__.TTF und Roche_*-Textstile entfallen): Textstile als Rollen nach Höhe – `EHS_Text_18`, `EHS_Text_25`, `EHS_Text_35`, `EHS_Text_50` (mm) – mit der Schrift **ISOCPEUR** (Normschrift nach DIN EN ISO 3098, liefert AutoCAD mit, keine Lizenzfrage, auf jedem Rechner vorhanden). Das Büro-Profil darf die Schrift tauschen, die Rollen bleiben. Datei `Stammdaten\Textstile.csv` | ja |

## B – Basis der Vorlage (AVT 0.2.0)

| Nr | Frage | Empfehlung |
|---|---|---|
| ★B1 | Leervorlage: `C:\ProgramData\Autodesk\MEP 2026\deu\Template\Aecb Model (D A CH Ctb) mm.dwt` (mm, CTB). RI 9.1 stammt nachweislich davon ab (gleiche Anzeigesätze), passt zu Ihrem Profil „AutoCAD MEP (D A CH)“. AVT behebt ihre 2 mitgelieferten AUDIT-Fehler und entfernt den Autodesk-Fachinhalt (66 Systeme, 22 Satzdefinitionen, 460 Klassifizierungen …) nach einer Liste | ja |

## V – Versionen der Module

| Nr | Frage | Empfehlung |
|---|---|---|
| V1 | Alle Module zählen ihre **EHS-Versionen ab 1.0.0** (ATT, ADM, ANA, ASG; AVT bleibt 0.x bis zur ersten Freigabe); der Altstand bleibt 0.x mit Markierung `altstand-ri91` – so ist an der Nummer erkennbar, ob ein Modul zum neuen System gehört (Vorschlag ANA) | ja |

## T – Übergang alter Zeichnungen

| Nr | Frage | Empfehlung |
|---|---|---|
| T1 | Fertige TAGs in alten Zeichnungen bei neuen Kürzeln: **behalten** (ATT meldet „veraltet“, nummeriert nur auf Wunsch neu; gesperrte bleiben immer) | behalten |
| T2 | ADM: gespeicherte Filter (4) mit Werkzeug auf neue Stilnamen umschreiben | ja |
| T3 | ATT: alte Testregel in `ATT_profile.json` („Drosselklappe Lüftung Motor X Versatz 75“) auf „Drosselklappe Lüftung Motor“ berichtigen | ja |
| T4 | Bis EHS 1.0.0 freigegeben ist, bleiben laufende Projekte auf RI 9.1 | ja |
| T5 | **Raum-Syntax** (BF18: 106 TAGs wie `0218-ZU-02`, FFU bis 15 Zeichen) für Luftdurchlässe und FFU: bleibt im Kunden-Profil „Roche“ parallel zur 7-Zeichen-Form (ATT kann beides je Bauteilart); im Kern gilt nur `01GP999` | ja |
| T7 | **Gewerkenummer** im TAG (erste 2 Ziffern): heute je **Medium** (PWW-VL → 01, WRG → 02 …; Lüftung: RLT-Anlage) – so lassen, oder künftig je **Gewerk** (Heizung, Kälte …)? Für ATT nur eine andere Liste, kein Umbau | je Medium lassen |
| T6 | Der Kürzel-Listensatz (RI 9.1 alt / EHS neu) wird an die Zeichnung gebunden (`EHS_Zeichnung`), nicht an den Rechner – so mischt keine Zeichnung alte und neue Kürzel (Vorschlag ATT) | ja |
