# EHS – Eichler-Hausstandard (Zeichnungsvorlage für ATT, ADM, ANA, ASG)

Auftrag des Nutzers (23.10.2026): „Mein Ziel ist es, eine in sich konsistente Vorlage zu bauen … du hast es in der
Hand, eine komplett konsistente Vorlage zu erstellen, in sich richtig stimmig.“ – „Der Master ist die derzeit geöffnete
Zeichnung und die DXF-Vorlage … Das hier ist jetzt die Basis.“ – „Wir nehmen die Version 9.1 und erstellen daraus einen
eigenen Hausstandard der Eichler GmbH.“

Ablage (Nutzer 23.10.2026): `Meine Ablage\Vorlagen\CAD\CADStandardEichlerGmbH\Schema` – hier liegt alles: Fassungen, Stammdaten, Handbuch, Prüfberichte. Gepflegt von AMK; Module ändern nur Kopien.

## Master und Ablage

| Was | Wo |
|---|---|
| Master-Zeichnung (Ausgangsstand) | `ANA AutoCADNetzAnalyse\Testzeichnungen\ANA_Test_2_CAD-Zeichnungsvorlage_RI_9.1.dwg` (Nutzer) |
| Master-Symbole (vom Nutzer selbst erstellt) | `Vorlagen\CAD\Roche\R+I Pharma\CAD-Vorlage fuer R+I_V9.1\SymboleVorlage_DXF` (20 DXF) |
| EHS-Fassungen (DWG) | `Versionen\EHS_<x.y>_….dwg` – jede Fassung neu, alte schreibgeschützt |
| Kopie der Symbol-DXF | `Symbole_DXF\` |
| Regeln, Stammdaten, Prüfberichte, Handbuch | `README.md`, `Stammdaten\`, `Pruefung\`, `Handbuch\`, `Bestandsaufnahme_2026-10-23\` |

`EHS_0.0` = unveränderte Kopie der Master-Zeichnung (Stand 23.10.2026 09:35). Die Zeichnung des Nutzers wird nie
geändert; gearbeitet wird nur an EHS-Fassungen.

## Grundsätze

1. **Eine Quelle:** Stammdaten (`stammdaten/*.csv`) werden aus EHS_0.0 + DXF erzeugt; ab EHS 0.1 ist die
   Stammdatenliste führend, die Vorlage wird daraus abgeleitet bzw. gegen sie geprüft. Anzeigethema „Medien“ ist führend
   für Systemfarben; der AKS-Konfigurator wird daran angeglichen (Nutzer 23.10.).
2. **Nur eigene Symbole:** MEP-eigene Stile bleiben außen vor bzw. werden aus der Vorlage entfernt, wenn ungenutzt.
3. **`TAGBauteil` bleibt unverändert** (Nutzer 20.10.) – keine Felder entfernen oder umbenennen, auch nicht den
   Tippfehler „CustomUserFied“.
4. **Zuständigkeit je Teil:** Symbolstile, Systeme, Anzeigethemen „Medien/Stoffgruppen“: ASG · Beschriftungsstempel,
   Kürzel-/Medienlisten, TAG*-Sätze: ATT · Bauteiltabellenstile, Plankopf: ADM · ANA-Sätze, ANA-Themen: ANA ·
   Stammdaten, Regeln, Freigabe: AMK. Jede Änderung an einer EHS-Fassung macht genau ein Modul, mit Prüfbericht.
5. **Jede Fassung prüfbar:** Prüfprogramm vergleicht Fassung ↔ Stammdaten ↔ Regeln, Ergebnis `pruefung/EHS_<x.y>.md`.

## Regeln (Entwurf – Nutzer bestätigt)

- **Symbolstil:** Name = Benennung aus den Stammdaten (eine Schreibweise, keine Tippfehler); Beschreibung
  „Benennung (KÜRZEL)“; Kürzel in `TAGBauteil:KurzZeichenSymbol` wie bisher.
- **Grafik:** Farbe, Linientyp, Linienstärke VonBlock (Farbe kommt vom System/Anzeigethema); Layer 0 im Block.
- **Einfügepunkt:** Mitte des Symbols auf der Leitungsachse.
- **Anschlüsse (Nutzer 23.10.):** „Immer die gleiche Vorgehensweise: von links nach rechts im Uhrzeigersinn benennen und Anschlüsse vergeben.“ Gilt auch für parametrische ASG-Bauteile (Genaufassung: Startpunkt, Namensschema – Vorschlag ASG folgt). Bisheriger Entwurf: in Leitungsrichtung, feste Namen (`Ein`, `Aus`, bei mehr: `Ein`, `Aus`, `Abzweig1` …), Verbinderstil
  einheitlich; Durchgangsbauteile (Armaturen, Reduzierung) 2 Anschlüsse; Materialwechsel bleibt bei 1 (Nutzer 22.10.).
- **Systeme:** Kürzel = LabelName der Systemdefinition = Kürzel in ATT-Listen = AKS; Benennung einheitlich.
- **Tagging:** Kennzeichen aus Anlagennummer + Kürzel + laufender Nummer (z. B. `01VDV01`) – Regel aus ATT übernommen,
  in den Stammdaten dokumentiert.
- **Beschriftungsstempel und Tabellen werden komplett neu erstellt** (Nutzer 23.10.: „Wir erstellen komplett neue
  Beschriftungsstempel und Tabellen“) – die alten TAG*-Stempel und Bauteiltabellenstile werden nicht bereinigt, sondern
  ersetzt; neue Stempel unabhängig von `TAGBauteil` gestaltet (siehe `AMK_Konzept.md` Punkt 1/2). Stempel: ATT,
  Tabellen: ADM.
- **Aufräumen:** ungenutzte Property Sets, Stempel, Tabellenstile, MEP-Fremdstile nur nach Liste und Freigabe entfernen;
  Testreste (ADM-Marken) entfernen.

## Ablauf

1. Bestandsaufnahme (Berichte `C:\Temp\AMK_Vorlage\Bericht_<Modul>.md`) – läuft.
2. Stammdaten aus EHS_0.0 + DXF erzeugen, Widersprüche als **eine** Entscheidungsliste (mit Vorschlag) an den Nutzer.
3. Regeln bestätigen.
4. EHS 0.1: Bereinigung je Modul an der Fassung (nur Kopie), Prüfbericht.
5. ASG: „In ASG überführen“ (Linienzeichnung → Symbolstil nach Regeln, Eintrag in Stammdaten).
6. Vorlage aus Stammdaten erzeugen bzw. prüfen; Umstellbefehl für alte Zeichnungen.
