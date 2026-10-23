# EHS – Eichler-Hausstandard (Zeichnungsvorlage für ATT, ADM, ANA, ASG)

Auftrag des Nutzers (23.10.2026): „Mein Ziel ist es, eine in sich konsistente Vorlage zu bauen … du hast es in der
Hand, eine komplett konsistente Vorlage zu erstellen, in sich richtig stimmig.“ – „Der Master ist die derzeit geöffnete
Zeichnung und die DXF-Vorlage … Das hier ist jetzt die Basis.“ – „Wir nehmen die Version 9.1 und erstellen daraus einen
eigenen Hausstandard der Eichler GmbH.“

Ablage (Nutzer 23.10.2026): `Meine Ablage\Vorlagen\CAD\CADStandardEichlerGmbH\Schema` – hier liegt alles: Fassungen, Stammdaten, Handbuch, Prüfberichte. Gepflegt von AMK; Module ändern nur Kopien.

## Leitbild (Nutzer 23.10.2026)

„Wir denken die Struktur jetzt absolut neu. Wir lösen uns von TAGBauteil, erstellen neue Stempel, eine neue Datenbankankopplung, eine neue Vorlage. Saubere Symbole, die alle gleich sind, absolut clean, identisch, rational, konsistent.“ – „Eine absolut cleane Zeichnung ohne Altlasten aus TAGBauteil oder anderen Eigenschaftsdatensätzen.“

## Master und Ablage

| Was | Wo |
|---|---|
| Master-Zeichnung (Ausgangsstand) | `ANA AutoCADNetzAnalyse\Testzeichnungen\ANA_Test_2_CAD-Zeichnungsvorlage_RI_9.1.dwg` (Nutzer) |
| Master-Symbole (vom Nutzer selbst erstellt) | `Vorlagen\CAD\Roche\R+I Pharma\CAD-Vorlage fuer R+I_V9.1\SymboleVorlage_DXF` (20 DXF) |
| EHS-Fassungen (DWG) | `Versionen\EHS_<x.y>_….dwg` – jede Fassung neu, alte schreibgeschützt |
| Kopie der Symbol-DXF | `Symbole_DXF\` |
| Testzeichnungen der Module (Derivate der EHS-Fassung) | `Testzeichnungen\EHS_<Fassung>_Test_<Modul>_<Inhalt>.dwg` – Nutzer 23.10.: alle Module testen nur noch in Derivaten der Vorlage; getestet wird an Kopien in `C:\Temp`; neue Fassung → Derivate neu |
| Regeln, Stammdaten, Prüfberichte, Handbuch | `README.md`, `Stammdaten\`, `Pruefung\`, `Handbuch\`, `Bestandsaufnahme_2026-10-23\` |

`EHS_0.0` = unveränderte Kopie der Master-Zeichnung (Stand 23.10.2026 09:35). Die Zeichnung des Nutzers wird nie
geändert; gearbeitet wird nur an EHS-Fassungen.

## Grundsätze

1. **Eine Quelle:** Stammdaten (`stammdaten/*.csv`) werden aus EHS_0.0 + DXF erzeugt; ab EHS 0.1 ist die
   Stammdatenliste führend, die Vorlage wird daraus abgeleitet bzw. gegen sie geprüft. Anzeigethema „Medien“ ist führend
   für Systemfarben; der AKS-Konfigurator wird daran angeglichen (Nutzer 23.10.).
2. **Nur eigene Symbole:** MEP-eigene Stile bleiben außen vor bzw. werden aus der Vorlage entfernt, wenn ungenutzt.
3. **Neuer Basis-Satz `EHS_Bauteil` statt `TAGBauteil`** (Nutzer 23.10.: TAGBauteil soll nicht Grundlage bleiben; „wir sind gerade dabei, die Datenbanken auch umzuschreiben“ – alte Datenbanken brauchen ihn nicht mehr). `TAGBauteil` entfällt in der EHS-Vorlage; alte Zeichnungen behalten ihn, ein Befehl übernimmt die Werte einmal. Feldkatalog `EHS_Bauteil` mit Zuständigkeit je Feld folgt (Stammdaten); die neuen Datenbanken richten sich danach. **Freie Felder (Nutzer 23.10.):** keine CustomUser 1–20 in `EHS_Bauteil` – die bleiben im alten `TAGBauteil` der alten Zeichnungen. Neues Konzept: `EHS_Bauteil` nur Felder mit fester Bedeutung (+ „Bemerkung“); Projektwünsche im optionalen Satz `EHS_Projekt` mit sprechenden Feldnamen aus dem Projektprofil; wiederkehrende Projektfelder wandern in `EHS_Bauteil`. Die CustomUser-Felder dienten den Datenbanken; die Datenbank-Anbindung wird künftig anders gelöst, die Vorlage löst sich davon.
4. **Zuständigkeit je Teil:** Symbolstile, Systeme, Anzeigethemen „Medien/Stoffgruppen“: ASG · Beschriftungsstempel,
   Kürzel-/Medienlisten, TAG*-Sätze: ATT · Bauteiltabellenstile, Plankopf: ADM · ANA-Sätze, ANA-Themen: ANA ·
   Stammdaten, Regeln, Freigabe: AMK. Jede Änderung an einer EHS-Fassung macht genau ein Modul, mit Prüfbericht.
5. **Jede Fassung prüfbar:** Prüfprogramm vergleicht Fassung ↔ Stammdaten ↔ Regeln, Ergebnis `pruefung/EHS_<x.y>.md`.

## Regeln (Entwurf – Nutzer bestätigt)

- **Normgrundlage (Nutzer 23.10.2026):** Symbolstile und Tagging sind auf **DIN EN IEC 81346-2:2020-10**
  (Industrielle Systeme, Anlagen und Ausrüstungen und Industrieprodukte – Strukturierungsprinzipien und
  Referenzkennzeichnung – Teil 2: Klassifizierung von Objekten und Kennbuchstaben für Klassen) aufgebaut bzw. daran
  angelehnt: Kurzzeichen = Unterklasse (3 Buchstaben) im TAG `01QMA01` (Gewerkenummer 2 + Unterklasse 3 + Zähler 2), Unterklasse und Bauart am Symbolstil, Stilname
  `<Unterklasse> <Benennung> [- Betätigung] [- Ausführung]`. Einzelheiten im `Bauplan_EHS.md` Abschnitt 15.

- **Symbolstil:** Name = Benennung aus den Stammdaten (eine Schreibweise, keine Tippfehler); Beschreibung
  „Benennung (KÜRZEL)“; Kürzel in der Stilbeschreibung (Description); daraus automatisch `StilSchemaSymbol:KurzZeichenSymbol` (geklärt 23.10.).
- **Grafik:** Farbe, Linientyp, Linienstärke VonBlock (Farbe kommt vom System/Anzeigethema); Layer 0 im Block.
- **Einfügepunkt:** Mitte des Symbols auf der Leitungsachse.
- **Anschlüsse (Nutzer 23.10.):** „Immer die gleiche Vorgehensweise: von links nach rechts im Uhrzeigersinn benennen und Anschlüsse vergeben.“ Gilt auch für parametrische ASG-Bauteile. **Entschieden:** „links 9 Uhr, dann im Uhrzeigersinn herumlaufen. Die Anschlüsse auch benennen.“ Bezug ist die ungedrehte Stildefinition. **Entschieden:** „A0 Mittelpunkt und dann fortlaufend“ – A0 = Mittelanschluss, A1…An ab 9 Uhr im Uhrzeigersinn, neutral ohne VL/RL; Seitenrolle nur an Weiche (Erzeuger/Verbraucher) und Wärmetauscher (Primär/Sekundär). **Nutzer 23.10.:** „Alle Bauteile auf A0 setzen … Über TAB können wir beim Einfügen über ASG einfach zwischen den Anschlüssen umschalten“ (Beispiel MAG: A0 + Rohranschluss). → A0 = Mittelpunkt = 0,0 bei jedem Bauteil. Prüfung ASG: 0,0 liegt bei 346 Stilen schon auf einem Anschluss, bei 214 auf der Achse, 12 weder noch; bestehende Stile nicht pauschal verschieben (eingesetzte Symbole springen) – neue Stilversion + Umstellung. Bewertung ASG/ANA (TAB-Jig, A0 als echter Anschluss in Behältermitte) läuft. Bisheriger Entwurf: in Leitungsrichtung, feste Namen (`Ein`, `Aus`, bei mehr: `Ein`, `Aus`, `Abzweig1` …), Verbinderstil
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

## Für später (Nutzer 23.10.)

- **Stempel wie Symbole anlegen (ATT):** Block zeichnen, Variablen (Felder) einfügen, „Block erstellen“ – mit Auswahl Rahmen ja/nein, gestrichelt usw. Gehört zum Tagging (ATT). Erst nach der konsistenten Vorlage.

## A0 – Handtest Nutzer 23.10.2026 (Erhitzer Zone)

A0 = Punkt ohne Verbindungsrichtung auf 0,0 (Muster des Nutzers, schon in 288 von 393 Stilen). Test in MEP: (1) am A0 erscheinen **keine Griffe**; (2) eine auf die Mitte gezeichnete Schemalinie **wird verbunden** (zieht beim Verschieben mit); (3) am Außenanschluss ebenso. → A0 ist kein sichtbarer Anschluss, aber gezielt verbindbar – nötig für Reduzierung/Materialwechsel (Leitungen enden in der Mitte). Bei Behältern/Geräten soll keine Leitung an A0 hängen: der Prüfbefehl warnt dort. **Regel:** jedes Bauteil hat A0 = Punkt ohne Verbindungsrichtung auf 0,0 (Basis); A1…An ab 9 Uhr im Uhrzeigersinn mit Verbindungsrichtung.
- **Bereinigungs-Knopf / eigenes Modul Vorlagenpflege** (Nutzer 23.10.): ein Knopf „Bereinigen“, der Altlasten (TAGBauteil & Co., fremde PSets, liNear-Einträge, „ANA_Hydraulik (2)“) aus einer Zeichnung entfernt und brauchbare Werte nach EHS_Bauteil übernimmt. Vorschlag AMK: dafür das ruhende Modul **AVT – AutoCAD-Vorlagen-Tool** (Ordner existiert, leer) aufbauen: Bereinigen, Prüfen gegen den Hausstandard, Vorlage aus Stammdaten erzeugen, Umstellen alter Zeichnungen, Release. ASG bleibt für Symbole zuständig; das EHS-Skript aus ASG (tools/ehs) wäre der Startpunkt.
