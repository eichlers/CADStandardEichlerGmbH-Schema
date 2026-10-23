# Felder ANA – Vorschlag für EHS_Bauteil (Stand 23.10.2026, ANA 0.9.29)

Quelle: Felddefinitionen im Code (`AnaHydraulikPropertySet.cs`, `AnaArmaturPropertySet.cs`), keine Zeichnung geändert.

## Heute
- ANA liest aus **TAGBauteil** nur zwei Dinge:
  - `PosNr`, als Quelle für das ANA-Kennzeichen (NETZANALYSE_KENNZEICHEN, einstellbar).
  - `Leistung`, aber nur als Warnung „steht in TAGBauteil“. ANA rechnet nie damit.
- ANA schreibt nichts nach TAGBauteil oder EDaten.
- **ANA_Hydraulik**: rund 115 Felder an allen Schemaobjekten (Bauteile und Leitungen). Darin stehen Eingaben am Bauteil, Eingaben an der Leitung (Gleichzeitigkeit, Auslegung, LaengeVorgabe) und Ergebnisse (`Erg_…`).
- **ANA_Armatur**: rund 35 Felder, nur an Armaturen. Darin stehen Art, Produkt, DN, kvs, Einstellung und Bewertung.
- Doppelt vorhanden sind heute:
  - Leistung (TAGBauteil, EDaten?, ANA_Hydraulik.Leistung)
  - Kennzeichen (TAGBauteil.PosNr, ANA_Hydraulik.Kennzeichen)
  - Hersteller und Typ (TAGBauteil?, ANA_Armatur)
  - DN (Stil bzw. Linie, ANA_Armatur.Nennweite, ANA_Hydraulik.AnschlussDN)
  - Volumenstrom (EDaten?, ANA_Hydraulik.Erg_Volumenstrom)
  - Druckverlust (Datenblatt-Eingabe ANA, ggf. EDaten)

## Grundsatz (Vorschlag)
1. **EHS_Bauteil** enthält nur, was ein Bauteil *ist* und was mehrere Module brauchen: Kennzeichen, Art, Produkt, Nenndaten laut Datenblatt.
   - **Eingaben laut Datenblatt** (Nennleistung, Δp bei Nennvolumenstrom, Anschluss-DN) stehen genau einmal hier.
   - ANA liest sie von hier und hat keine eigene Kopie mehr.
2. **Rechenergebnisse** (`Erg_…`) bleiben in ANA_Hydraulik bzw. ANA_Armatur.
   - Andere Module lesen sie dort nur, z. B. ATT für Beschriftung, ADM für die Datenbank.
   - Ein Wert hat damit genau einen Schreiber.
3. **Leistung und Volumenstrom** sind zwei verschiedene Werte und sollen getrennt bleiben, damit nichts überschrieben wird:
   - Die **Auslegung** ist eine Eingabe (EHS_Bauteil).
   - Das **Ergebnis der Rechnung** steht in ANA (Erg_).
   Beide unter einem Namen hieße: Entweder ANA überschreibt die Planereingabe, oder die Beschriftung zeigt nicht, was gerechnet wurde.
4. **Leitungen** bekommen kein EHS_Bauteil, denn eine Leitung ist kein Bauteil.
   - Ihre Daten sind DN, Rohrklasse und System. Sie stehen im MEP-Objekt bzw. im Stil.
   - ANA_Hydraulik bleibt an Leitungen. Dort stehen 3 Eingaben und die Ergebnisse (Volumenstrom, v, R, Teilstrecke …). Daraus beschriftet ATT, darauf beruhen die Anzeigethemen.
   - Vorschlag: einen eigenen, schlanken Satz **ANA_Leitung** abspalten. Dann steht an einer Leitung nicht der ganze Bauteilsatz mit 100 leeren Feldern. Das ist nur auf Go möglich, denn ATT-Beschriftungen und Anzeigethemen hängen am Namen.
5. **Beschriftungen** (MvBlockRef/Tags) sollen kein ANA_Hydraulik tragen.
   - ANA hängt den Satz an Schemaobjekte (Symbol und Linie), nicht an Beschriftungen.
   - Wenn ADM ihn an Beschriftungen findet (K1/K2), kommt er vermutlich aus Kopien bzw. aus der Vorlage oder von ATT. ANA prüft das gern an einem Beispiel-Handle.

## Felder für EHS_Bauteil (aus Sicht ANA)

| Name (Vorschlag) | Bedeutung | Typ / Einheit | schreibt | liest | ersetzt heute |
|---|---|---|---|---|---|
| Kennzeichen | Anlagenkennzeichen/Positionsnummer, eindeutig | Text | Planer bzw. ATT (Stempel), ADM (Datenbank) | alle; ANA für Bericht und Fenster | TAGBauteil.PosNr, ANA_Hydraulik.Kennzeichen |
| Bauteilart | Funktion im Netz, z. B. Verbraucher, Erzeuger, Pumpe, Armatur, Systemtrennung, Weiche, Formstück | Liste | Planer bzw. Vorlage (aus Kurzzeichen vorbelegt) | ANA (Rolle), ATT, ADM | ANA_Hydraulik.Rolle (Liste ANA_Rolle; „Automatisch“ bleibt als Wert) |
| Armaturart | Unterart bei Armaturen und Formstücken (Regelventil, PICV, Schmutzfänger, Reduzierung, Materialwechsel …) | Liste | Planer bzw. Vorlage | ANA, ATT, ADM | ANA_Armatur.ArmaturArt (Liste aus ANA-Enum, Text unverändert) |
| Kurzzeichen | Kurzzeichen des Symbols (FMW, PU, …) | Text, vom Stil | Vorlage (Stil) | ANA (Erkennung), ATT | heute StilSchemaSymbol/KurzZeichenSymbol (ASG prüft Herkunft); nur übernehmen, wenn nicht ohnehin am Stil |
| Hersteller | Hersteller des gewählten Produkts | Text | ANA-Auswahl (Armaturen) bzw. Planer/ADM | alle | ANA_Armatur.Hersteller (Eingabe) und Erg_HerstellerGewaehlt |
| Produktreihe | Serie | Text | wie Hersteller | ANA, ADM | ANA_Armatur.Produktreihe |
| Typ | Typbezeichnung/Produkt | Text | wie Hersteller | alle | ANA_Armatur.Erg_Produkt |
| Artikelnummer | Bestellnummer des Herstellers | Text | wie Hersteller | ADM, ATT | ANA_Armatur.ProduktAuswahl und Erg_Artikelnummer |
| Bestelltext | Langtext für LV/Bestellung | Text | ANA (Messstellen-Katalog) bzw. ADM | ADM | ANA_Armatur.Erg_Bestelltext |
| Merkmale | technische Daten produktneutral („Anzeigebereich: 0 … 120 °C“) | Text | ANA-Fenster bzw. Planer | ATT, ADM | ANA_Armatur.Merkmale (+ Unterart) |
| NennweiteAnschluss | DN der Anschlüsse laut Datenblatt (0 = unbekannt) | Ganzzahl, DN | Planer bzw. ADM; bei Armaturen ANA-Auswahl | ANA (Reduzierungsprüfung), ATT | ANA_Hydraulik.AnschlussDN, ANA_Armatur.Nennweite und Erg_DNGewaehlt |
| Nennleistung | Leistung laut Auslegung/Datenblatt: am Verbraucher die Bedarfsleistung, am Erzeuger und an der Systemtrennung die Nennleistung | Real, kW | Planer bzw. ADM | ANA (Eingabe), ATT, ADM | ANA_Hydraulik.Leistung (Verbraucher), Nennleistung (Erzeuger), TrennungLeistung; TAGBauteil.Leistung; EDaten-Leistung |
| Spreizung | Auslegungsspreizung | Real, K | Planer | ANA, ATT | ANA_Hydraulik.Spreizung |
| VolumenstromNenn | Volumenstrom laut Datenblatt bzw. Auslegungspunkt der Pumpe | Real, m³/h | Planer bzw. ADM | ANA (Pumpe: Soll-Volumenstrom), ATT | ANA_Hydraulik.VolumenstromGewaehlt; EDaten-Volumenstrom |
| DruckverlustNenn | Δp bei Nennvolumenstrom laut Datenblatt | Real, kPa | Planer bzw. ADM | ANA | ANA_Hydraulik.DruckverlustBauteil |
| Wasserinhalt | Inhalt laut Datenblatt | Real, l | Planer bzw. ADM | ANA (Anlageninhalt) | ANA_Hydraulik.Wasserinhalt |
| ElektrischeLeistung | P1 laut Hersteller (Pumpe, Gerät) | Real, W | Planer bzw. ADM | ANA (Pumpenenergie), Elektro | ANA_Hydraulik.PumpenP1Hersteller |
| Betrieb | Laufend/Reserve | Liste | Planer | ANA, ADM | ANA_Hydraulik.Betrieb |
| Medium | Medium des Kreises am Erzeuger (leer = aus Kreise.json/System) | Text | Planer | ANA, ATT | ANA_Hydraulik.Medium. Fraglich, denn das Medium gehört eher zum System bzw. Kreis als zum Bauteil (Entscheidung Nutzer) |

**Systemtrennung** (zwei Seiten): Die je Seite doppelten Felder (TemperaturPrimaer…, DruckverlustPrimaer/Sekundaer, WasserinhaltPrimaer/Sekundaer, MediumPrimaer/Sekundaer) sind ANA-spezifisch und bleiben in ANA_Hydraulik. Nur `Nennleistung` geht nach EHS_Bauteil.

## Bleibt ANA-intern

**ANA_Hydraulik, Eingaben**
- TemperaturVorlauf/-Ruecklauf (Erzeuger)
- Leistungsreserve
- BauteilSperre
- Kreisname
- ReduzierungImAnschluss
- PumpeImErzeuger
- DruckerhoehungGewaehlt, MindestvolumenstromPumpe
- PumpenBauart, -Regelung, -Wirkungsgrad
- Strompreis, Betriebsstunden, Lastannahme
- Behaelter…/Puffer… (Weiche)
- Verteiler…
- Trennung… (s. o.)
- an Leitungen: Gleichzeitigkeit, Auslegung, LaengeVorgabe

**ANA_Hydraulik, Ergebnisse**
- alle `Erg_…`, darunter Erg_Volumenstrom, Erg_Leistung, Erg_Druckverlust, Erg_Druckerhoehung, Erg_Foerderhoehe, Erg_Teilstrecke, Erg_Nennweite usw.
- Andere Module lesen sie nur.

**ANA_Armatur**
- KvsVorgabe, Schliessfeder, Einbaulage, VolumenstromVorgabe, TemperaturSekundaerVorlauf
- alle `Erg_…` (Kvs, Voreinstellung, Einsatz, Auslastung, Δp, Autorität, Regelgüte, Reduzierung, Rohrklasse …)

## Fragen an den Nutzer bzw. AMK
1. **Schreibrecht an Hersteller/Typ/Artikelnummer**: Bei Armaturen wählt heute ANA das Produkt aus Herstellerdaten. Soll ANA künftig nach EHS_Bauteil schreiben? Das wäre der einzige Fall, in dem ANA in den Basissatz schreibt. Der Vorschlag ist ja, aber nur auf ausdrückliche Auswahl im Fenster, nie beim Rechnen.
2. **Nennleistung vs. Erg_Leistung**: Bleibt die Trennung zwischen Eingabe (Basis) und Ergebnis (ANA)? Empfehlung: ja.
3. **ANA_Leitung abspalten?** Das betrifft ATT-Beschriftungen und Anzeigethemen (Regeln auf ANA_Hydraulik/Erg_*).
4. **Medium**: am Bauteil oder nur am System bzw. Kreis?
5. **Umstellung bestehender Zeichnungen**: ANA kann alte Felder beim ersten Rechnen nach EHS_Bauteil übernehmen, so wie die Umbenennung auf Erg_ (BenenneFelderUm). Das gilt nur, wenn das Basisfeld leer ist, ohne Überschreiben, und mit Meldung.
