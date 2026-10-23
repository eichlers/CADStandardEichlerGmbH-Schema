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
  Symbole\        Register.csv + je festem Symbol eine DXF (Symbole\<Kategorie>\<ID>.dxf) – nur ASG schreibt
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
  (für ANA), Beschreibung „Benennung (Kürzel)“ (Fehler).

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

## 10 Reihenfolge

1. ~~Nutzer bestätigt Basis, Ablage, Versionen, Profile~~ – erledigt 23.10.
2. Stammdaten-Entwürfe zusammenführen (ATT Systeme, ASG Symbole, ANA Kürzel, ADM Spaltenmatrix) → **eine**
   Entscheidungsliste an den Nutzer (ersetzt die offenen Punkte der Entscheidungsliste EHS 0.1).
3. Feldkatalog entscheiden.
4. ASG: Register + Prüfung (Abschnitt 6) + „In Bibliothek aufnehmen“ + „Bauteil aus Linien“; DXF je Symbol aufteilen.
5. AVT: Erzeugen aus Stammdaten + Prüfen; erste Fassung EHS 1.0.0 nach Freigabe.
6. Derivate, gemeinsamer Testplan, danach alte Testzeichnungen löschen (je Modul mit Freigabe).
