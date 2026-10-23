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
Kürzel in Anlehnung an DIN EN 81346-2 · Symbole gewerkeneutral · Elektro entfällt, Geschirrspüler/Waschmaschine bleiben ·
Testzeichnungen nur als Derivate · Corporate Design · liNear bleibt (Bereinigen in AVT) · Pumpe 01PUM03 bleibt ·
Materialwechsel 1 Anschluss · AVT-Farbe anthrazit · leere Vorlage ohne Zeichnungsobjekte (G1, folgt aus „grüne Wiese“) ·
alte TAG-Stempel und Bauteiltabellen werden ersetzt, nicht repariert.

---

## ★ N – Namen und Kürzel (blockiert ASG v2)

| Nr | Frage | Empfehlung |
|---|---|---|
| ★N1 | Kürzelaufbau: **2 Kennbuchstaben nach DIN EN 81346-2 + 1 Bauart-Zeichen nur wo nötig** (GP Pumpe, GPD Doppelpumpe, GPT Tauchpumpe); Familie = Hauptklasse der Norm | ja |
| ★N2 | **Normtext** DIN EN 81346-2 (Klassentabelle) an ASG geben – Sekundärquellen haben Doppelbelegungen | bitte liefern (Pfad) |
| N3 | Stilname = `<Kürzel> <Benennung> [- Betätigung] [- Ausführung] [- Maße]`, mit Umlauten, ohne ß, Tippfehler korrigiert (Begriffsliste) | ja |
| N4 | Je **Armaturart ein eigenes Kürzel** (30 Arten laut ANA, z. B. Regelventil 2-Wege ≠ 3-Wege ≠ PICV ≠ PIBV), Antriebsvarianten ohne eigenes Kürzel, Wasser ≠ Luft | ja |
| N5 | 4 Dubletten zusammenlegen (Aufbau 3-fach, Wärmetauscher Platten, Wärmetauscher Rohrbündel, Rührwerk) – eine ID bleibt, Grafik vorher verglichen | ja |
| N6 | 9 offene Elektro-nahe Stile (WP-Außen-/Innenteil, Temperaturfühler, Raumthermostat, E-Heizkörper, Durchlauferhitzer, Ventilator, Motor): in die passende Familie statt entfallen | ja, Zuordnung ASG |

## ★ F – Felder (blockiert AVT 0.4 Erzeugen)

| Nr | Frage | Empfehlung |
|---|---|---|
| ★F1 | **„Bauteilart“ eindeutig machen** (Vorschlag ADM): **Familie** = automatisch aus dem 1. Kürzelbuchstaben (Gruppen in Legende/Stückliste/Excel) · **Bauteilart** = Funktion im Netz (Werteliste, ANA-Sicht) · **Benennung** = Stilname ohne Kürzel | ja |
| F2 | Datenblattwerte (Nennleistung, Volumenstrom, Δp, Anschluss-DN, Wasserinhalt, P1) in `EHS_Bauteil`, Rechenergebnisse bleiben in ANA (ADM und ANA einig) | ja |
| F3 | Hersteller/Typ/Artikelnummer an einem Ort (`EHS_Bauteil`); ANA schreibt nur auf Knopfdruck „Übernehmen“ | ja |
| F4 | Kennzeichen-Teilfelder `Anlage` und laufende Nummer; Grundregel `{Anlage}{Kürzel}{Nummer}` (z. B. `01GP03`) | ja |
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
| E1 | ANA erkennt im Hausstandard zuerst über die Kürzel-Tabelle der Stammdaten; Stilwörter nur Rückfall | ja |
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

## L – Listen und Plankopf (ADM)

| Nr | Frage | Empfehlung |
|---|---|---|
| L1 | ADM füllt alle Listen (eine Listendefinition, Excel daraus); ANA löst nur „Listen aktualisieren“ aus (F1) | ja |
| L2 | AutoCAD-Tabellen `EHS_Liste` für Fachlisten und Legende; AEC-Tabelle nur fürs Raumbuch; live mitlaufende Stückliste (F2) | ja |
| L3 | Reihenfolge: Ventilliste, Einstellliste, Pumpenliste, Legende zuerst (F3) | ja |
| L4 | Legende als von ADM gefüllte Tabelle, Legendenblöcke entfallen (F4) | ja |
| L5 | Eichler-Plankopf mit Attributen (Projekt, Plan-Nr., Index, Datum) im Büro-Profil (D3) | ja |
| L6 | Roche-Textstile/-Schrift nicht in Kern/Büro; Ersatzschrift festlegen (D2) | ja, Vorschlag folgt |

## T – Übergang alter Zeichnungen

| Nr | Frage | Empfehlung |
|---|---|---|
| T1 | Fertige TAGs in alten Zeichnungen bei neuen Kürzeln: **behalten** (ATT meldet „veraltet“, nummeriert nur auf Wunsch neu; gesperrte bleiben immer) | behalten |
| T2 | ADM: gespeicherte Filter (4) mit Werkzeug auf neue Stilnamen umschreiben | ja |
| T3 | ATT: alte Testregel in `ATT_profile.json` („Drosselklappe Lüftung Motor X Versatz 75“) auf „Drosselklappe Lüftung Motor“ berichtigen | ja |
| T4 | Bis EHS 1.0.0 freigegeben ist, bleiben laufende Projekte auf RI 9.1 | ja |
