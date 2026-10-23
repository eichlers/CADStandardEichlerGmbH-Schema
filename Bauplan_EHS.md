# Bauplan EHS – Eichler-Hausstandard „grüne Wiese“

Stand 23.10.2026 · AMK · vom Nutzer bestätigt (23.10.: „Deine Frage beantworte ich mit ja“ – Basis, Ablage, Versionen,
Profile, Arbeitsweise, Prüfung durch ASG).

Auftrag des Nutzers (23.10.2026): „Wir fangen jetzt auf der grünen Wiese an, wir bauen uns eine eigene cleane Vorlage in
AVT … so, dass wir für die Zukunft sicher sind, revisionssicher und maximal flexibel.“ – „Bei ASG werden Symbole
verwaltet.“ – „ASG muss das Bauteil einer Prüfung unterziehen, bevor es sinnlos Bauteile einfügt. Es muss einen
Kürzelvorschlag geben, der Redundanzen ausschließt. Die Grafik muss stimmen, die Farbe, die Linienart.“

## 1 Grundsatz: Vorlage als Bauplan, nicht als Zeichnung

- **Eine Quelle:** Stammdaten (CSV, in Excel lesbar) und die Symbolbibliothek in diesem Ordner, versioniert mit Git.
  Die Vorlage wird daraus **erzeugt** (AVT), nie von Hand geändert. Gleiche Stammdaten → gleiche Vorlage.
- **Basis**: unveränderte Autodesk-MEP-Leervorlage (metrisch), nur für die Anzeigekonfiguration;
  Version und Prüfsumme der Basis werden festgehalten. Alles andere kommt aus den Stammdaten.
- **RI 9.1 ist nur noch Quelle** (Bestandsaufnahme 23.10.). EHS 0.0–0.2 sind Entwürfe/Belege, keine Grundlage mehr.

## 2 Zuständigkeiten

| Wer | Aufgabe |
|---|---|
| ASG | **verwaltet die Symbole**: Register, Bibliothek, Prüfung, Kürzelvorschlag, parametrische Generatoren, Einfügen, „Bauteil aus Linien“, „In Bibliothek aufnehmen“. Einziger Schreiber in `Symbole\`. |
| AVT | baut die Vorlage aus Stammdaten + freigegebener Symbolfassung, prüft Zeichnungen gegen ihre Fassung, Release, Umstellen alter Zeichnungen, Bereinigen (Altlasten, liNear-Reste), Testderivate. Zeichnet keine Symbole. |
| ATT | Kürzel- und Medienlisten aus dem AKS, Stempel |
| ADM | Tabellen und Listen, Datenbank-Anbindung |
| ANA | Rechnen; Erkennung über die Kürzel-Tabelle der Stammdaten |
| AMK | Stammdaten pflegen (außer `Symbole\`), Änderungen abstimmen, Testplan |
| Nutzer | gibt neue Symbole und jede Fassung frei |

## 3 Ablage

```
Schema\
  Stammdaten\     Systeme.csv, Kuerzel.csv, Feldkatalog.csv, Themen.csv, Layer.csv, Textstile.csv,
                  Umbenennung.csv (alt → neu), Profile\<Kunde>\… (z. B. Roche)
  Symbole\        Register.csv + je festem Symbol eine DXF, flach: Symbole\<ID>_v<n>.dxf (Kategorie nur im
                  Register, damit der Git-Verlauf beim Umsortieren nicht reißt) – nur ASG schreibt
  Versionen\      freigegebene Fassungen EHS_<x.y.z>.dwt, schreibgeschützt, mit Prüfbericht
  Testzeichnungen\ Derivate „Fassung + Testinhalt“ je Modul
  Pruefung\, Handbuch\, Bestandsaufnahme_2026-10-23\
```

## 4 Arbeitsweise des Nutzers

1. In MEP über „Neu“ mit der Vorlage `EHS_<x.y.z>.dwt` eine Zeichnung anlegen (die Vorlage ist schreibgeschützt und
   wird so nie überschrieben). Enthalten: alle Symbole, Anzeigethemen, Stempel, Tabellen.
2. Im Projekt arbeiten. Ein mit ASG neu erzeugtes Bauteil steckt **nur in dieser Zeichnung**.
3. Soll es in den Hausstandard: ASG „**In Bibliothek aufnehmen**“ → Prüfung (Abschnitt 6) → Vorschlag mit neuer ID →
   Freigabe Nutzer → nächste Fassung (AVT) enthält es → laufende Projekte holen es auf Wunsch über ASG nach, nie
   automatisch.
4. Parametrische Bauteile (Verteiler, Behälter, Wärmetauscher …): eine neue **Größe** kommt nicht in die Bibliothek
   (ASG erzeugt sie jederzeit neu), nur eine neue **Bauart**.

## 5 Symbolregister (ASG)

Je Symbol eine Zeile: **ID** (ändert sich nie), Benennung, Kürzel, Kategorie, Bauteilart/Armaturart, Bauart
(fest/parametrisch), Quelle (DXF bzw. Generator + Parameter), Anschlüsse (A0, A1 … An mit Lage und Richtung),
Symbolversion, Status (Vorschlag/freigegeben/abgekündigt/ersetzt durch ID), Prüfbericht, Freigabe (wer, wann).
Gelöscht wird nie. Geometrie- oder Anschlussänderung = neue Symbolversion. Erste Fassung: `Symbole_ASG.csv`
(23.10., 416 Stile + 76 DXF-Blöcke).

## 6 Prüfung vor jeder Aufnahme (ASG) – ohne bestandene Prüfung keine Aufnahme

Ergebnis je Punkt: **Fehler** (blockiert) oder **Hinweis**; ASG zeigt, was nicht passt, und korrigiert auf Wunsch.
Der Prüfbericht wird mit dem Vorschlag abgelegt.

**Doppelt / Redundanz**
- Gleiche Geometrie schon im Register? Vergleich der normierten Grafik (unabhängig von Name, Drehung, Spiegelung,
  Lage) → „gibt es schon als <ID>“ (Fehler).
- Benennung schon vergeben, auch in anderer Schreibweise (Umlaut/ae, ß/ss, Leerzeichen/Bindestrich, groß/klein) (Fehler).

**Kürzelvorschlag**
- ASG schlägt ein Kürzel nach dem AKS-Schema vor (Gruppenbuchstabe + Kennung, wie die vorhandenen).
- Eindeutig: nie ein Kürzel, das schon für eine **andere** Bauteilart steht (Lehre aus VDV: PICV/2-Wege/3-Wege) –
  geprüft gegen Register, AKS und ATT-Liste. Gleiche Bauteilart, andere Ausführung → dasselbe Kürzel erlaubt (Hinweis).
- Reihenfolge bleibt AKS → ATT-Liste → ASG: Nach der Freigabe trägt ATT das Kürzel ins AKS ein (Sicherung vorher).

**Grafik**
- Alle Objekte auf Layer 0; Farbe, Linientyp, Linienstärke **VonBlock** (keine feste Farbe, keine feste Linienstärke) (Fehler).
- Nur Linientypen aus der Liste der Stammdaten (Fehler).
- Keine Fremdobjekte: keine Proxys, keine liNear-/Add-on-Objekte, keine Bemaßung, keine Bilder, keine verschachtelten
  fremden Blöcke (Fehler); Texte/Attribute nur, wo die Bauart es vorsieht (Hinweis).
- Füllung nur nach den ASG-Füllregeln (Hinweis).
- Größe im üblichen Rahmen der Kategorie (Hinweis, Maß legt AMK in den Stammdaten fest).

**Anschlüsse**
- A0 = Punkt ohne Verbindungsrichtung auf 0,0 (Fehler).
- A1 … An ab 9 Uhr im Uhrzeigersinn, benannt, Richtung nach außen, Bezug ungedrehter Stil (Fehler); Seitenrolle nur an
  Weiche (Erzeuger/Verbraucher) und Wärmetauscher (Primär/Sekundär).
- Anzahl passend zur Bauteilart laut Pflichttabelle ANA (A6) (Fehler).
- Durchgangsbauteile: Einfügepunkt auf der Leitungsachse; Fließrichtung +X bei Pumpe, Rückschlagarmatur, Pfeil,
  Reduzierung (sobald A7 entschieden) (Fehler).

**Angaben**
- Benennung nach Regel (Art vorn, mit Umlauten, ohne ß und ohne ae/oe/ue), Kategorie, Bauteilart/Armaturart gesetzt
  (für ANA) (Fehler).
- **Stilbeschreibung (Description) = nur das Kürzel** (Korrektur ASG 23.10.): MEP bildet daraus automatisch
  `StilSchemaSymbol.KurzZeichenSymbol`, so lesen ANA und ATT das Kürzel. Benennung, ID und Symbolversion stehen im
  Register und in einem Satz am Stil (ID, Version) – daran prüft ASG beim Nachholen in Projekte die Version, statt
  gleichnamige Stile ungefragt zu überschreiben.
- **Füllung:** Ausnahme von „VonBlock“ für Füllungen nach der ASG-Füllregel (einfarbig/Verlauf, Nutzer 19.10.); vorher in
  MEP an einer Kopie belegen, dass die Themenfarbe bei VonBlock wirkt (A5).
- **Eindeutige Kürzel** brauchen eine Spalte „Bauteilart“ in der Kürzelliste (heute nur Kürzel → Klartext).
- **Parametrische Stilnamen:** Namensregel im neutralen Kern (Art vorn, Maße als Zusatz, Umlaute, kein Modulname);
  erkannt wird über die Formdaten am Objekt, nicht über den Namen.
- **Prüfgrundlagen als Stammdaten:** Linientypliste, Größenrahmen je Kategorie, Pflichttabelle Anschlüsse (ANA A6),
  Füllregeln – Dateien unter `Stammdaten\`, Eigentümer je Datei.
- **Bestand zuerst:** Die ASG-eigenen Bauteile erfüllen A0/A1…An heute selbst nicht (Namen „oben 1“, „Erzeuger VL“).
  Erst Formversion + Migration (ASGAENDERN kennt alt und neu, Weiche mit ANA), dann zählt der Punkt als Fehler; bis
  dahin und für offene Entscheidungen (A3, A7) nur Hinweis.
- **Gleiche Geometrie** (ASG-Verfahren): in Grundelemente zerlegen, normieren (Mitte der Ausdehnung, Maßstab 1,
  Rundung 1/1000), alle 8 Lagen (Drehung 0/90/180/270, gespiegelt); „identisch“ (Fingerabdruck) = Fehler, „sehr ähnlich“
  (Abstandsmaß) = Hinweis mit den 3 nächsten IDs; gleiche Grafik mit anderen Anschlüssen = Hinweis. Schwelle erst nach
  Eichung an den Bestandsstilen (Paarliste an den Nutzer).
- **Kürzelvorschlag** nur aus vorhandenen Daten: Gruppenbuchstabe aus Kategorie/Bauteilart im Register, Kennung aus der
  Benennung, 3 Kandidaten, je Kandidat geprüft gegen Register, Kern und Profil (inkl. Schreibvarianten); unklar →
  ASG fragt. Vorher die 53 Bestandskürzel klären, die in keiner Liste stehen (LVS, PVE, LFI …).

## 7 Versionen und Freigabe (revisionssicher)

- Nummer `x.y.z`: x = etwas wird umbenannt/fällt weg (Umbenennungsliste nötig), y = etwas kommt dazu, z = Korrektur.
- Freigabe nur durch den Nutzer; danach ist die Fassung schreibgeschützt und wird nie mehr geändert.
- Jede Fassung: Prüfbericht AVT, Änderungsliste, Git-Markierung, Stand der Stammdaten und der Symbolfassung.
- Jede Zeichnung trägt Fassung und Stand in sich (Wörterbuch `EHS_Zeichnung`); Module melden fremde oder ältere Fassungen.
- Jedes Element hat eine feste interne ID; Anzeigenamen dürfen sich ändern, ohne dass Zeichnungen, Datenbank oder Listen brechen.

## 8 Flexibel: Kern + Büro-Profil + Kunden-Profil

Ziel des Nutzers (23.10.): „Später aus diesem Master auch Vorlagen für andere Ing-Büros entwickeln – das ist aber in
der Zukunft.“ Gebaut wird das später; die **Aufteilung gilt ab jetzt**, damit nichts wieder auseinandergenommen werden muss:

| Schicht | Inhalt | Beispiel |
|---|---|---|
| Kern | neutraler TGA-Standard: Symbole, Systeme, Kürzel, Feldkatalog, Themen, Regeln – ohne Firmennamen | `EHS_Bauteil`, Thema „Medien“ |
| Büro-Profil | was ein Ingenieurbüro ausmacht: Plankopf, Logo, Textstile/Schrift, Stempelgestaltung, Copyright, Kennzeichen-Grundregel | Profil „Eichler“ (erstes und vorerst einziges) |
| Kunden-/Projekt-Profil | Wünsche des Bauherrn: zusätzliche Systeme, Felder in `EHS_Projekt`, Kennzeichen-Syntax | Profil „Roche“ |

AVT baut „Kern + Büro + Kunde“, ohne eine untere Schicht zu ändern. Regel ab sofort: Firmenbezogenes (Name Eichler,
Logo, Plankopf) steht nie im Kern. Namen von Sätzen und Stilen im Kern bleiben neutral (`EHS_…` = Kürzel des
Standards, kein Firmenname im Feld- oder Stilnamen).

## 9 Testzeichnungen

Getestet wird nur in Derivaten der Vorlage (Nutzer 23.10.). Derivat = Fassung + Testinhalt je Modul, per Skript
erzeugt (AVT, Vorschlag 23.10.). Bis dahin werden keine Derivate auf EHS 0.2 gebaut.

## 10 Ergänzungen nach Gegenprüfung (Architektur-Review + AVT, 23.10.)

**Technisch (übernommen):**
- **Anzeigethemen** haben keine .NET-Schnittstelle (Befund ASG 0.9.7). Darum gibt es neben CSV und Symbolen eine dritte
  Quelle: kleine **Bausteine** (je Thema bzw. je Objektart, die die API nicht erzeugen kann, eine DWG mit nur diesem
  Inhalt) unter `Stammdaten\Bausteine\` mit Prüfsumme. AVT klont sie; das Prüfen vergleicht die Regeln mit `Themen.csv`
  (CSV = Soll, Baustein = Ist). Bausteine klein halten, nur wo die API nicht reicht.
- **Machbarkeit zuerst:** AVT 0.2.0 versucht je Objektart das Anlegen headless (3 Läufe) und meldet „erzeugen / klonen /
  nur aus Basis“. Erst danach werden Feldkatalog und Register festgeschrieben. Unsicher sind besonders
  Systemdefinitionen, Mehransichtsblöcke, Bauteiltabellenstile, Schemalinien in Derivaten.
- **Reproduzierbar:** kein Byte-Vergleich der DWG, sondern ein **kanonischer Inhaltsauszug** (sortierter Text aller
  Definitionen ohne Handles/Zeiten) mit Prüfsumme, in Git neben der Fassung. Zweimal bauen → gleiche Prüfsumme.
  Manifest: MEP-Build, AVT-Version, Basis-Prüfsumme, Commit der Stammdaten, Symbolfassung.
- **Feste IDs:** XData unter der RegApp der Vorlage an Stilen, Tabelleneinträgen, Satzdefinitionen; Feld-IDs als
  Zuordnung im Erweiterungswörterbuch der Satzdefinition; Fassung im NOD-Wörterbuch `…_Zeichnung` und zusätzlich in den
  Zeichnungseigenschaften (ohne Plugin sichtbar). „Erstellt aus“ und „umgestellt auf“ getrennt.
- **Umstellen nie blind:** Trockenlauf mit Bericht (Vergleich über ID + Version, Liste der Anschlüsse, die sich
  verschieben würden), Sicherungskopie, Protokoll in der Zeichnung. Zurück nur über die Sicherung. Eine Fassung kann
  „zurückgezogen“ werden, gelöscht wird sie nie. Geometrie-/Anschlussänderung an eingesetzten Symbolen = Hauptnummer.
- **Schichtenregeln:** Profile fügen nur hinzu; Überschreiben nur über eine Override-Liste mit ID; der Kern verweist auf
  Büro-Inhalte nur über Rollen (z. B. Textstil-Rolle „Text 2,5“, das Büro setzt die Schrift); jedes Profil nennt den
  Kern-Bereich, den es verträgt; Fassungsname aus allen Schichten (z. B. `<Kern>_1.3.0+EIC_1.0+ROC_1.1`); Kern-Update
  baut jedes Profil neu und prüft es.
- **Fehlte im Ablageplan:** Layer-Schlüsselstile, Schemalinienstile/Rohrklassen, Verbinderstil, Einheiten und
  AEC-Zeichnungseinstellungen, Beschriftungsmaßstäbe, Bemaßungsstile, Layouts/Seiteneinrichtung, Systemvariablen der
  Vorlage, mitzuversionierende Dateien (CTB/STB, PC3, .lin, .pat, Schriften). Schriftlizenz: keine Kundenschrift
  (ROCHL__.TTF) in Kern oder Büro.
- **Migration TAGBauteil → `…_Bauteil`:** Eigentümer AVT („Umstellen“), Zuordnung `Stammdaten\Migration_TAGBauteil.csv`
  (Pflege AMK, Abnahme ATT/ADM).
- **Je Stammdatei ein Eigentümer und ein Freigeber** (Kopfzeile der Datei). Auch Definitionen, die Module zur Laufzeit
  anlegen (ANA-Themen, ANA-Sätze), kommen aus den Stammdaten und tragen eine ID – sonst meldet die Prüfung sie als fremd.
  README Grundsatz 4 (alte Zuständigkeiten) ist durch Abschnitt 2 abgelöst.
- **Doppelprüfung Symbole:** zuerst „exakt gleich“ (normierte Objektliste mit Toleranz) als Fehler, „ähnlich“ als Hinweis
  mit Prüfung durch den Nutzer.

**Entscheidung Nutzer nötig:**
- (E-a) ✔ **Entschieden 23.10.** (Nutzer: „AKS ist ein Abfallprodukt … wird aus den Zeichnungen bzw. der Vorlage erstellt“). **Eine Wahrheit je Datenart:** `Stammdaten\*.csv` führend, AKS-Tab und ATT-Listen werden daraus erzeugt – löst
  die Regel „AKS-Konfigurator → ATT → ASG“ ab. Dazu (ASG 23.10.): Das AKS (`Roche\R+I Pharma\…\AKS-Konfigurator_v3.1`)
  ist Kundenstandard und gehört ins Profil „Roche“; der Kern hat eigene neutrale Kürzel, das Profil bildet sie auf das
  AKS ab (meist 1:1). Die Kette AKS → ATT → ASG gilt dann nur noch im Profil.
- (E-d) **Füllung als Ausnahme von VonBlock** (siehe Abschnitt 6) – Empfehlung ja.
- (E-e) **Go Formversion der ASG-Bauteile** auf A0/A1…An mit Migration (ASG 0.12, mit ANA) – Empfehlung ja, nach
  Register und Prüfbefehl.
- (E-b) ✔ **Entschieden 23.10.:** „Für das Projekt ist EHS super. Wir müssen nur später in der Lage sein, es irgendwie umzuschwenken.“ → Name bleibt **EHS**; umschwenkbar halten (Abschnitt 12). Ursprünglicher Vorschlag: **Neutrales Präfix** statt „EHS“ (= Eichler-Hausstandard) für Kern-Sätze/-Stile, damit der Kern ohne Firmennamen
  auch für andere Büros taugt. Jetzt umstellen ist billig, später nicht.
- (E-c) ✔ **Entschieden 23.10.:** „Der Ablageort ist auch in Ordnung.“ → Schema-Ordner bleibt, Rollen siehe Abschnitt 12. Ursprünglicher Hinweis: **Ablage im Google-Drive-Ordner:** Git-Repos und schreibgeschützte DWT in einem synchronisierten Ordner können
  durch Sperr-/Sync-Konflikte beschädigt werden. Vorschlag: Arbeitskopie lokal (z. B. `C:\EHS`), Drive nur als
  Verteilziel; Schreibschutz über Prüfsumme/Manifest absichern.

## 11 Reihenfolge

0. AVT 0.2.0: Machbarkeit je Objektart + kanonischer Inhaltsauszug (läuft, braucht keine Entscheidung).
1. ~~Nutzer bestätigt Basis, Ablage, Versionen, Profile~~ – erledigt 23.10.; offen E-a, E-b, E-c (Abschnitt 10).
2. Stammdaten-Entwürfe zusammenführen (ATT Systeme, ASG Symbole, ANA Kürzel, ADM Spaltenmatrix) → **eine**
   Entscheidungsliste an den Nutzer (ersetzt die offenen Punkte der Entscheidungsliste EHS 0.1).
3. Feldkatalog entscheiden.
4. ASG: Register + Prüfung (Abschnitt 6) + „In Bibliothek aufnehmen“ + „Bauteil aus Linien“; DXF je Symbol aufteilen.
5. AVT: Erzeugen aus Stammdaten + Prüfen; erste Fassung EHS 1.0.0 nach Freigabe.
6. Derivate, gemeinsamer Testplan, danach alte Testzeichnungen löschen (je Modul mit Freigabe).

## 12 Entwicklung in AVT, Live-System im EHS-Ordner (Nutzer 23.10.)

Nutzer: „In AVT wird das Tool zur Pflege des Projekts abgelegt. Fertige Versionen werden dann immer in den EHS-Ordner
gepusht. Wir testen jetzt in AVT, und wenn es einen Stand der Vorlage gibt, pushen wir ihn in den EHS als derzeitiges
Live-System Schema.“

| Ort | Rolle |
|---|---|
| AVT-Repo (`ClaudeProjekte\AVT-AutoCADVorlagenTool`) + `C:\Temp\AVT\…` | **Werkstatt:** Werkzeug, Bauläufe, Entwürfe `1.0.0-e<n>`, Tests, Derivate im Bau. Nichts davon ist „live“. |
| EHS-Ordner (`Vorlagen\CAD\CADStandardEichlerGmbH\Schema`) | **Live-System:** nur freigegebene Fassungen (`Versionen\`), die Stammdaten und Symbole, aus denen sie gebaut sind, Prüfberichte, Versionshistorie. |

**Ablauf einer Freigabe:** AVT baut und prüft in der Werkstatt → Nutzer gibt frei → AVT schreibt die DWGPROPS (unten),
legt die Fassung schreibgeschützt in `Versionen\` ab, ergänzt `Versionshistorie.md`, committet und pusht, setzt die
Git-Markierung → AMK prüft das Paket (Prüfbericht, Kette, Felder) und meldet „live“ an alle Module.

**Name umschwenkbar halten (E-b):** Der Name „EHS“ (Satz-, Stil-, Wörterbuch-, RegApp-Vorsilbe) steht an **einer**
Stelle in den Stammdaten (`Stammdaten\Standard.csv`: Kürzel, Langname, Vorsilbe). AVT baut daraus; die Module lesen
Satz- und Feldnamen aus dem Feldkatalog bzw. einer Konstante je Modul, nie verstreut im Code. Umschwenken = neue
Hauptnummer + Umbenennungsliste (alt → neu) + AVT „Umstellen“.

### DWGPROPS vor jeder Fassung (Nutzer 23.10.: „hier immer die entsprechenden Werte eintragen, bevor eine Version in EHS
angelegt wird“)

AutoCAD hält in jeder Zeichnung Standardfelder und benutzerdefinierte Felder (Befehl `DWGPROPS`); AVT erreicht beide
per Programm (`SummaryInfo`, auch headless). Ohne vollständige Felder keine Ablage im EHS-Ordner (Fehler im Prüfbericht).

| Feld | Inhalt in der Vorlage (Vorschlag) |
|---|---|
| Titel | `EHS – Eichler-Hausstandard · Schema-Vorlage` |
| Thema | `TGA-Schema, AutoCAD MEP 2026 · Kern + Büro Eichler (+ Kunde, falls Profil)` |
| Autor | `S. Eichler · Eichler-GmbH` |
| Schlüsselwörter | `EHS; <x.y.z>; Kern <x.y.z>; Büro Eichler <v>; Kunde <Name v>; MEP 2026` |
| Kommentare | Kurzfassung der Änderungen gegenüber der Vorgängerfassung + Verweis auf `Versionshistorie.md` |
| Revisionsnummer | `<x.y.z>` |
| Hyperlink-Basis | **leer lassen** (wirkt auf alle relativen Hyperlinks der späteren Projektzeichnung) |
| `EHS_Fassung` (benutzerdef.) | `<x.y.z>` |
| `EHS_Vorgaenger` | Fassung davor (Kette, siehe unten) |
| `EHS_Freigabe` | Datum, „S. Eichler“ |
| `EHS_Profile` | Kern `<v>` · Büro `<v>` · Kunde `<v>` |
| `EHS_Stammdaten` | Git-Commit der Stammdaten |
| `EHS_Symbolfassung` | Fassung der ASG-Bibliothek |
| `EHS_Basis` | Autodesk-Leervorlage + Prüfsumme |
| `EHS_Inhaltspruefsumme` | Prüfsumme des kanonischen Inhaltsauszugs |
| `EHS_AVT` | AVT-Version, mit der gebaut wurde |

Hinweis: Eine Projektzeichnung, die aus der Vorlage entsteht, erbt diese Felder. Titel/Thema/Kommentare darf der
Planer für sein Projekt überschreiben; die `EHS_…`-Felder bleiben als Herkunft („erstellt aus Fassung“) stehen, AVT
„Umstellen“ ergänzt `EHS_UmgestelltAuf`.

### Versionskette (Nutzer 23.10.: „bei der Ablage auch die Versionskette einhalten und immer dokumentieren“)

- Jede Fassung nennt ihren Vorgänger (`EHS_Vorgaenger`, Versionshistorie, Git); keine Nummer wird übersprungen oder
  doppelt vergeben, keine Fassung überschrieben oder gelöscht (höchstens „zurückgezogen“ mit Grund).
- Entwürfe heißen `<x.y.z>-e<n>` und bleiben in der Werkstatt (AVT); erst die Freigabe macht `<x.y.z>` im EHS-Ordner.
- Je Fassung in `Versionshistorie.md`: Nummer, Vorgänger, Datum, Freigabe, Änderungen (aus dem Text-Diff der
  Inhaltsauszüge), Prüfbericht, Bruch ja/nein (Hauptnummer → Umbenennungsliste).
- AVT prüft vor der Ablage: Vorgänger vorhanden und freigegeben, Nummer folgt der Regel, Historie und DWGPROPS gefüllt.
- Die bisherigen Entwürfe EHS 0.0–0.2 bleiben als Belege; die erste Live-Fassung ist EHS 1.0.0.

## 13 Bereinigen und Hinweis auf Fremdinhalte (Nutzer 23.10.)

Nutzer: „Es kann passieren, dass man aus Versehen eine Schemazeichnung mit dem MEP-liNear-Profil öffnet …“ – „Das
Bereinigen betrifft nicht nur liNear, auch wenn andere Blöcke gefunden werden. Leise darauf hinweisen und ggf. bereinigen.“

AVT vergleicht die offene Zeichnung im Leerlauf mit ihrer EHS-Fassung und meldet leise (eine Zeile in der Palette bzw.
einmal in der Befehlszeile, kein Dialog). „Bereinigen“ in der Palette: Vorschau → Bestätigung → automatische
Sicherungskopie → bereinigen → Nachprüfung → Bericht; AVT speichert nie.

| Fund | Angebot | Vorgabe |
|---|---|---|
| a) fremd, unbenutzt (Blöcke, Stile, Sätze, Layer, Textstile, Linientypen, RegApps, Wörterbücher, Dubletten) | entfernen | angehakt |
| b) fremd, benutzt (Fremdblöcke, alte Symbole, TAGBauteil an Objekten) | ersetzen durch EHS-Symbol (nur mit Zuordnung) · an ASG „In Bibliothek aufnehmen“ · behalten (Ausnahme mit Grund merken) | nicht angehakt |
| c) Projektinhalt (eigene Blöcke ohne Fremdspuren, Plankopf, Details) | nur Info | nie |

## 14 Symbolnamen und Gruppen (Nutzer 23.10., im Gespräch mit ASG)

- **Stilnamen maximal konsistent**, eine Syntax für alles, mit Gruppen. Entwurf ASG:
  `<Kürzel> <Benennung> [- <Betätigung>] [- <Ausführung>] [- <Maße>]`, Trenner „ - “ nur zwischen Bausteinen,
  Begriffsliste mit Synonymen in den Stammdaten, feste ID im Register, Umbenennungsliste alt → neu.
- **Gewerkeneutral:** „Sortierung nach Gewerk möchte ich ausschließen … Symbole sind übergeordnet zu betrachten.“
  Gruppiert wird nach **Familie = erster Buchstabe des Kürzels**. Gewerk erst wieder für eine spätere Medienpalette.
- **Stilname = Ablage** (lesbar, weil MEP-Stil-Manager, Eigenschaften und ADM ihn zeigen); ASG zeigt den Klartext aus dem
  Register als Baum Familie → Bauteilart → Variante.
- **Elektro-Symbole entfallen** („können wir rausschmeißen“: 18 Stile, 20 DXF-Blöcke). Geschirrspüler und Waschmaschine
  **bleiben** als Sanitär (Nutzer 23.10.).
- **Kürzelschema** (Nutzer 23.10. an ASG): „Bei der Liste gebe ich dir freie Hand. Wichtig ist, Redundanzen
  auszuschließen.“ Ein 4. Zeichen ist erlaubt, Orientierung an DIN 6779 / DIN EN IEC 81346-2:2020-10; der TAG darf nicht zu lang
  werden (Textüberschneidung im Plan). Ein Kürzel = genau eine Bauteilart (VDV wird getrennt in 2-Wege, 3-Wege, PICV).
- **Prüfung des Entwurfs (23.10.):** ATT – 4 doppelte neue Namen (= Zusammenlegungen kennzeichnen), Kollisionen DRK→VDB,
  DMG→MMS; ANA – NER/NKU-Umbenennung bricht die heutige Kürzel-Erkennung (erst nach ANA-Kürzeltabelle); ADM – Code
  unabhängig, 4 gespeicherte Filter brauchen ein Umschreibewerkzeug; „Familie“ = Gruppe, nicht Netzfunktion.
- Befund AKS: Doppel-Kürzel für dieselbe Sache (ERH/HLE, KUE/HLK, BEF/HBF, FIL/TFA, FKU/XKU, FHA/XHA, VAA/VAB, TAA/TAB) –
  in den Stammdaten auf eins festlegen.
- Betroffen beim Umbenennen: ATT (Listen), ANA (Erkennung über Kürzel/Namen – Umstellung auf die Kürzel-Tabelle zuerst),
  ADM (Listen, gespeicherte Filter). Umbenannt wird erst mit Umbenennungsliste und neuer Fassung, nie vorher.

## 15 Kürzel nach DIN EN IEC 81346-2:2020-10 (Nutzer 23.10., im Gespräch mit ASG)

Nutzer: Benennung in Anlehnung an **DIN EN IEC 81346-2:2020-10** („scheint besser geeignet“ als DIN 6779-12), „dass man eine Rationale
hat, warum die Bauteile so heißen“; Beispiele GP = Pumpe, HQ = Filter.

- Vorschlag ASG (Bestätigung Nutzer offen): **Kürzel = 2 Kennbuchstaben der Norm + 1 Bauart-Zeichen nur wo nötig**
  (GP Pumpe, GPD Doppelpumpe, GPT Tauchpumpe …); **Familie = Hauptklasse der Norm** (ersetzt die 15 Familien aus
  Abschnitt 14).
- TAG-Länge: heute `01PUM03` = 7 Zeichen → `01GP03` = 6 bzw. `01GPD03` = 7; mit 4. Zeichen 8 – nie länger als heute,
  außer im Ausnahmefall.
- Passt zur Schichtung: Der **Kern** nutzt die genormten Kennbuchstaben (neutral, auch für andere Büros); das AKS mit
  seinen bisherigen Kürzeln wird im Profil „Roche“ abgebildet.
- Klassentabelle nur aus dem Normtext (Nutzer liefert ihn), nicht aus Sekundärquellen (dort Doppelbelegungen).
- Übergang: ANA erkennt weiter über PUM/NER/VDV …, bis die Kürzel-Tabelle (E1) umgestellt ist; die Liste alt → neu ist
  die Brücke. Fertige TAGs in alten Zeichnungen: Entscheidung Nutzer (behalten oder neu taggen).

### 15a Entschieden (Nutzer 23.10., an ASG)

DIN EN IEC 81346-2:2020-10, Tabelle des Nutzers `Desktop\DIN_EN_81346-2_3_Ebene_HLK_Bibliothek.xlsx` (Filter = ND).
**TAG = Anlage 2 Ziffern + Kürzel genau 2 Kennbuchstaben + Zählnummer 3 Ziffern = 7 Zeichen, ohne Trennstriche**
(`01GP999`). Keine Bauart im Kürzel (TAG bleibt stabil beim Tausch Kugelhahn ↔ Klappe). Vorschlag ASG (Bestätigung
offen): 3. Ebene (GPA, QMA, QMB …) = Angabe „Unterklasse“ am Symbol, Armaturart = Angabe „Bauart“ am Symbol; ANA
erkennt daran. Der Vorschlag „2 Buchstaben + Bauart-Zeichen“ in Abschnitt 15 ist damit überholt. Alte und neue Kürzel
nie gemischt in einer Zeichnung; Umstellen nur über die Liste alt → neu.

### 15b Basis und Machbarkeit (AVT 0.2.0, 23.10.)

Empfohlene Basis: `Aecb Model (D A CH Ctb) mm.dwt` (MEP 2026 deu), Entscheidung Nutzer (Entscheidungsliste B1).
Per API belegt: Layer, Linientypen, Text-/Bemaßungsstile, Layouts, Satzdefinitionen mit Formel- und automatischen
Feldern, Layer-Schlüsselstil, Schemasysteme, Mehransichtsblöcke mit Ansichtsblock, Bauteiltabellenstile, DWGPROPS,
Fassungsstempel. AutoCAD-Tabellenstil nur als Kopie von „Standard“. **Anzeigethemen:** neu anlegbar, aber ohne
Darstellungseigenschaften (Farbe nicht setzbar) → aus einem kleinen Baustein-Thema klonen und Satz/Feld/Bedingung/Farbe
per Programm setzen (Abschnitt 10 bleibt so). Anzeigekonfiguration aus der Basis. Inhaltsauszug: 7 Bauten = gleiche
Prüfsumme.

### 15c Ort von Unterklasse und Bauart (Vorschlag ASG + ANA, 23.10., hängt an N1)

- Stilbasierter Satz `EHS_Symbol` am Symbolstil: SymbolID, Symbolversion, Unterklasse, Bauart – ASG schreibt ihn aus dem
  Register; Vorsilbe als Konstante an einer Stelle. Am einzelnen Objekt nichts; Ausnahme je Objekt bleibt
  `ANA_Armatur.ArmaturArt`.
- Gemeinsame Stammdatei `Stammdaten\Bauarten.csv` mit Spalten ANA-Rolle und ANA-Armaturart (Grundlage: 30 Armaturarten
  von ANA + Rollen) – kein fester Text im ANA-Code.
- Erkennung ANA (nach Go): Eintrag am Objekt > `EHS_Symbol.Bauart` > Unterklasse (wo eindeutig) > Kürzel (nur Rolle) >
  Stilwörter (alte Zeichnungen). Widerspruch Klasse ↔ Bauart = gelbe Meldung, gerechnet wird mit der Bauart.
- ANA liest auch `EHS_Symbol (n)` (Einklon-Dublette) und meldet sie als Hinweis; zusammengeführt wird sie von AVT
  „Bereinigen“.

**Festgelegt (AMK, 23.10.):** eigener Satz `EHS_Symbol` (nicht Felder in `StilSchemaSymbol`, das MEP vorgibt und aus dem
ATT/ANA heute das Kürzel lesen). Stammdateien `Stammdaten\Bauarten.csv` (fachlicher Eigentümer ANA) und
`Stammdaten\Unterklassen.csv` (aus der Tabelle des Nutzers nach DIN EN IEC 81346-2:2020-10, Entwurf ASG); Module liefern Entwürfe nach
`C:\Temp\AMK_Vorlage\Stammdaten_Entwurf`, AMK legt sie ab. Stilname bestätigt: `<Unterklasse> <Benennung> [- Betätigung]
[- Ausführung]`.

### 15d TAG-Form geprüft (ATT, 23.10.)

`01GP999` geht in ATT ohne Umbau (Syntax `{System}{Kürzel}{Zähler 3-stellig}` im Profil; Zurücklesen über bekanntes
Präfix, keine Verwechslung mit `01GPD…` oder alten `01PUM03`). Platz: in BF18 (181 Stempel), RI 9.1 (66), ANA-Test (618)
entsteht auch mit 7–8 Zeichen keine neue Überdeckung (Grenze: nur gegen Stempel und Symbole geprüft, nicht gegen Leitungen
und DN-Stempel). Höchstzahl gleicher Kürzel je Anlage in echten Projekten < 100 (BF18 max. 90) – 3 Ziffern reichen.
Alte 3-Buchstaben-TAGs passen nicht in die neue Form und erscheinen als „fremde PosNr“ – keine Verwechslung alt/neu.
Offen: Raum-Syntax (T5), Listensatz an die Zeichnung binden (T6).

### 15e Stilname ist nicht der TAG (Nutzer 23.10.)

Nutzer: „Hier geht es erst mal nur um die Stilnamen der Symbole. Das Tagging ist wieder etwas anderes. Da ziehen wir ja
dann die Gewerkenummer plus das Kurzzeichen aus dem Stil mit einer laufenden Nummer zusammen. Also Achtung: Name eines
Symbols ist nicht gleich das Tagging, sondern nur ein Teil davon. Das Tagging erfolgt dann in ATT.“

| Teil | Wer | Inhalt |
|---|---|---|
| Stilname | ASG | `<Unterklasse> <Benennung> [- Betätigung] [- Ausführung]` – Ablage/Lesbarkeit |
| Stilbeschreibung | ASG | Kurzzeichen (2 Kennbuchstaben nach DIN EN IEC 81346-2:2020-10) |
| `EHS_Symbol` | ASG | SymbolID, Symbolversion, Unterklasse, Bauart |
| TAG | **ATT** | Gewerkenummer + Kurzzeichen aus dem Stil + laufende Nummer (z. B. `01GP001`); ob ein Stil getaggt wird, entscheidet ATT |
- **Rückfall über die Unterklasse (ANA, v6-Prüfung 23.10.):** nur bei eindeutigen Unterklassen (42 von 62); bei gemischten
  nimmt ANA die hydraulische Hauptart als Annahme mit gelber Meldung „Bauart fehlt – angenommen …“ (GPA → Pumpe,
  TAA → Systemtrennung, TAB → Verbraucher, QMA → Absperrarmatur, QMB → Regelventil 2-Wege, RMA → Rückschlagventil,
  NDB → Schmutzfänger). Die Bauart am Stil bleibt Pflicht (in v6 an jedem Stil gesetzt).

### 15f Zeichen ohne Normklasse: Vorsilbe Z (Nutzer 23.10.: „ja, super Idee!“)

Pfeile, Strangsymbole und Kennzeichen sind nach DIN EN IEC 81346-2:2020-10 keine Objekte und werden im Normalfall nicht
getaggt. Sie bekommen die Vorsilbe **Z = Zeichen** (Z ist in der Norm keine Hauptklasse): `Z<Gruppe><Nr> <Benennung>
[- Ausführung]`. ZPA Pfeil Fließrichtung · ZPB Pfeil Luftrichtung · ZPC Pfeil Gefälle · ZPD Pfeil allgemein · ZSA
Strangsymbole · ZKA Kennzeichen an der Leitung · ZAA Zusatzzeichen am Bauteil. Auch Z-Zeichen haben eine Stilbeschreibung (Nutzer: „Eine Stilbeschreibung braucht auch ein Pfeil. Sie werden nur
nicht getaggt.“): ZP, ZS, ZK, ZA. Nicht getaggt werden sie über ATTs Liste „taggen: nie“ für die Familie Z; Bauart
„Kennzeichnung“ (→ ANA rechnet nicht). Neue Zeichen = neue Z-Gruppe.

## 16 Komplett neues System – keine Rücksicht auf alte Zeichnungen (Nutzer 23.10.)

Nutzer: „Also alte Zeichnungen müssen nicht gelesen werden können, wir fangen hier mit einem kompletten neuen System an.“

- Die Module müssen im EHS-System **keine** RI-9.1-Zeichnungen lesen oder rechnen: keine Rückfallketten über Stilwörter
  oder alte Kürzel, keine Rücksicht auf `TAGBauteil`, keine Umstellung alter Zeichnungen (AVT „Umstellen“ entfällt bzw.
  ruht). Getestet wird nur in Derivaten der EHS-Vorlage.
- Bleibt: AVT „Bereinigen“ für Fremdinhalte, die in eine EHS-Zeichnung hineinkopiert werden (liNear, Fremdblöcke).
- **Altstand RI 9.1:** Die heute installierten Stände (ATT 0.15.9 · ADM 0.9.24 · ANA 0.9.29 · ASG 0.9.17) werden in Git
  als `altstand-ri91` markiert und bleiben für laufende Projekte (z. B. BF18) nutzbar, bis sie abgelöst sind. Neue
  EHS-Versionen dürfen alte Zeichnungen ablehnen bzw. mit Hinweis „keine EHS-Zeichnung“ eingeschränkt arbeiten.
- Damit überholt: Rückfall über Unterklasse/Stilwörter (15c/15d, nur noch Unterklasse als Rückfall für fehlende Bauart
  in EHS-Zeichnungen), Umbenennungsliste als Migrationswerkzeug (bleibt als Dokumentation alt → neu), Migration
  `TAGBauteil` (Abschnitt 10).
