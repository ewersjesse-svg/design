# Leitfaden: Anforderungsanalyse und Anforderungsmodell

**Praxisleitfaden für Einsteiger — angewendet auf die Digitalisierung der werkseigenen Produktionskontrolle (WPK) im Holztafelbau nach DIN 1052-11**

---

## Inhaltsverzeichnis

0. [Wie du dieses Dokument benutzt](#0-wie-du-dieses-dokument-benutzt)
1. [Grundlagen: Worüber reden wir eigentlich?](#1-grundlagen-worüber-reden-wir-eigentlich)
2. [Anforderungsarten: funktional, nicht-funktional, Randbedingungen](#2-anforderungsarten-funktional-nicht-funktional-randbedingungen)
3. [Das Vorgehen: sieben Schritte zu deinem Anforderungsmodell](#3-das-vorgehen-sieben-schritte-zu-deinem-anforderungsmodell)
4. [Erhebung: wie du an belastbare Anforderungen kommst](#4-erhebung-wie-du-an-belastbare-anforderungen-kommst)
5. [Ist- und Soll-Prozess modellieren](#5-ist--und-soll-prozess-modellieren)
6. [Dokumentation: Notation, Satzschablone, Attribute](#6-dokumentation-notation-satzschablone-attribute)
7. [Qualitätssicherung und Priorisierung](#7-qualitätssicherung-und-priorisierung)
8. [Anwendung: WPK im Holztafelbau](#8-anwendung-wpk-im-holztafelbau)
9. [Aufbau im Thesis-Dokument](#9-aufbau-im-thesis-dokument)
10. [Typische Fehler in Bachelorarbeiten](#10-typische-fehler-in-bachelorarbeiten)
11. [Werkzeuge](#11-werkzeuge)
12. [Literatur und Quellen](#12-literatur-und-quellen)

---

## 0. Wie du dieses Dokument benutzt

Dieser Leitfaden hat zwei Aufgaben: Er erklärt dir die Grundlagen des Requirements Engineering (RE) von null an, und er führt dich gleichzeitig durch genau deinen Fall — ein Anforderungsmodell für eine digitale WPK-Lösung im Holztafelbau.

**Wenn du wenig Zeit hast**, lies in dieser Reihenfolge:

1. Kapitel 1.1 bis 1.4 (Grundbegriffe) — ca. 15 Minuten
2. Kapitel 2 (funktional vs. nicht-funktional) — ca. 15 Minuten
3. Kapitel 3 (das Vorgehen als Fahrplan) — ca. 15 Minuten
4. Kapitel 6.2 (die Satzschablone) und 6.4 (Attribute) — ca. 15 Minuten

Damit kannst du anfangen zu arbeiten. Kapitel 4, 5, 7 und 8 liest du dann jeweils direkt vor dem Arbeitsschritt, für den du sie brauchst.

**Die Vorlagen** im Ordner [`../vorlagen/`](../vorlagen/) sind zum Kopieren gedacht: Interviewleitfaden, Anforderungsliste, Anforderungs-Steckbrief, Stakeholder-Map, Glossar, Schwachstellenkatalog, Use-Case-Schablone und die Prüfliste für Anforderungsqualität.

**Ein Hinweis zu den Fachinhalten:** Die WPK-Beispiele in Kapitel 8 sind fachlich plausibel und für die Methodik ausreichend, aber sie ersetzen nicht den Blick in die Originalnorm. DIN 1052-11 liegt mir nicht im Volltext vor. Alle normbezogenen Aussagen sind als solche markiert und musst du vor der Abgabe an der Norm selbst verifizieren. Das ist keine Schwäche des Vorgehens: In der Praxis ist die Normanalyse ohnehin ein eigener Arbeitsschritt (siehe Kapitel 4.2).

---

## 1. Grundlagen: Worüber reden wir eigentlich?

### 1.1 Was ist eine Anforderung?

Die geläufigste Definition stammt ursprünglich aus IEEE 610.12 und wird von IREB und ISO/IEC/IEEE 29148 in dieser Form weitergeführt. Eine Anforderung ist:

> 1. eine Bedingung oder Fähigkeit, die von einem **Benutzer** zur Lösung eines Problems oder zur Erreichung eines Ziels benötigt wird;
> 2. eine Bedingung oder Fähigkeit, die ein **System** erfüllen oder besitzen muss, um einen Vertrag, eine Norm, eine Spezifikation oder ein anderes formell auferlegtes Dokument zu erfüllen;
> 3. eine **dokumentierte Repräsentation** einer Bedingung oder Fähigkeit gemäß (1) oder (2).

Diese dreiteilige Definition wirkt zunächst akademisch, aber sie enthält drei praktisch sehr nützliche Aussagen:

- **Teil 1** sagt: Anforderungen haben eine *Quelle* — einen Menschen mit einem Bedürfnis. Eine Anforderung, die niemand will, ist keine.
- **Teil 2** sagt: Anforderungen können auch aus *Dokumenten* stammen — Verträge, Gesetze, **Normen**. Für dich zentral: DIN 1052-11 ist eine legitime, sogar besonders harte Anforderungsquelle.
- **Teil 3** sagt: Eine Anforderung existiert für die Ingenieurarbeit erst, wenn sie *aufgeschrieben* ist. Was im Kopf des Produktionsleiters steckt, ist ein Bedürfnis — erst die dokumentierte Form ist eine Anforderung.

Merksatz für deine Arbeit: **Eine Anforderung beschreibt, *was* ein System leisten soll — nicht, *wie* es das technisch tut.** Sobald du „mit einer PostgreSQL-Datenbank" schreibst, hast du eine Lösungsentscheidung getroffen, keine Anforderung formuliert. Das ist einer der häufigsten Anfängerfehler und einer der leichtesten Angriffspunkte in der Verteidigung.

### 1.2 Was ist Requirements Engineering?

Requirements Engineering ist die systematische Vorgehensweise, mit der man Anforderungen ermittelt, dokumentiert, prüft und verwaltet. Nach IREB gliedert es sich in vier Kernaktivitäten, die sich nicht sauber nacheinander abarbeiten lassen, sondern sich gegenseitig immer wieder anstoßen:

| Aktivität | Leitfrage | Typische Techniken |
|---|---|---|
| **Ermittlung** (Elicitation) | Was brauchen die Beteiligten wirklich? | Interviews, Beobachtung, Dokumentenanalyse, Workshops |
| **Dokumentation** | Wie halte ich das eindeutig und nachvollziehbar fest? | Satzschablonen, Use-Cases, Modelle, Attributtabellen |
| **Prüfung und Abstimmung** (Validation) | Ist es richtig, vollständig, von allen getragen? | Reviews, Walkthroughs, Prototypen, Rückkopplung mit Experten |
| **Verwaltung** (Management) | Wie behalte ich bei Änderungen den Überblick? | IDs, Versionierung, Status, Traceability, Priorisierung |

Der entscheidende Punkt für dich: **Anforderungsanalyse ist kein Sammeln, sondern ein Konstruieren.** Stakeholder sagen dir nicht fertige Anforderungen an. Sie erzählen dir von Problemen, Gewohnheiten, Ärgernissen und Wünschen. Die Übersetzung dieser Rohdaten in präzise, prüfbare Anforderungen ist deine eigentliche wissenschaftliche Leistung — und genau das, was in der Bachelorarbeit bewertet wird.

### 1.3 Was ist ein Anforderungsmodell?

Hier gibt es keine einheitliche Lehrbuchdefinition, deshalb eine, die für deine Arbeit tragfähig ist und die du so auch begründen kannst:

> Ein **Anforderungsmodell** ist die strukturierte, in sich zusammenhängende Gesamtdarstellung aller Anforderungen an ein System — bestehend aus mehreren aufeinander verweisenden Teilmodellen (Kontext, Ziele, Stakeholder, Prozesse, Anwendungsfälle, Daten und der eigentlichen Anforderungsliste), die zusammen beschreiben, *was* das System leisten muss.

Der Unterschied zu einer bloßen **Anforderungsliste** ist die *Struktur und die Verknüpfung*. Eine Liste mit 80 Sätzen ist kein Modell. Ein Modell entsteht, wenn:

- jede Anforderung einer **Quelle** zugeordnet ist (Interview X, Schwachstelle Y, DIN 1052-11 Abschnitt Z),
- Anforderungen den **Prozessschritten** und **Anwendungsfällen** zugeordnet sind, in denen sie wirken,
- die **Begriffe** einheitlich definiert sind (Glossar) und
- die **Beziehungen** zwischen Anforderungen sichtbar sind (verfeinert, setzt voraus, steht im Konflikt mit).

Ein bewährter Aufbau für dein Anforderungsmodell — das ist zugleich die Zielstruktur deiner Arbeit:

```
Anforderungsmodell
├── Zielmodell            Warum überhaupt? (2–5 Oberziele, daraus abgeleitete Unterziele)
├── Kontextmodell         Systemgrenze: was gehört dazu, was nicht, wer/was wirkt von außen
├── Stakeholder-Modell    Wer hat ein berechtigtes Interesse, mit welchen Bedürfnissen
├── Prozessmodell         Ist-Prozess, Schwachstellen, Soll-Prozess (BPMN)
├── Anwendungsfallmodell  Use-Cases: welche Interaktionen mit dem System gibt es
├── Datenmodell (light)   Welche fachlichen Objekte gibt es (Element, Prüfung, Charge …)
└── Anforderungskatalog   Funktionale + nicht-funktionale Anforderungen + Randbedingungen
```

Nicht jede Bachelorarbeit braucht alle sieben Teile in voller Tiefe. Für deinen Umfang empfehle ich: Ziel- und Stakeholder-Modell kompakt, Kontext- und Prozessmodell sorgfältig (das ist deine Erhebungsleistung), Anwendungsfall- und Datenmodell schlank, Anforderungskatalog als Herzstück.

### 1.4 Systemgrenze und Kontext: das musst du zuerst klären

Bevor du eine einzige Anforderung formulierst, musst du wissen, *worüber* du eigentlich Anforderungen formulierst. Das klingt trivial, wird aber fast immer übersprungen — mit der Folge, dass später die halbe Arbeit an der Frage hängt, ob die Lagerverwaltung nun dazugehört oder nicht.

Drei Zonen, die du sauber trennen musst:

| Zone | Bedeutung | Beispiel aus deinem Fall |
|---|---|---|
| **System** | Das, was du gestaltest. Hier formulierst du Anforderungen. | Die digitale WPK-Anwendung |
| **Systemkontext** | Alles außerhalb, das mit dem System interagiert oder es beeinflusst. Beeinflussbar? Nein. Relevant? Ja. | Prüfer, Produktionsleiter, Fremdüberwacher, ERP-System, vorhandene Messgeräte, DIN 1052-11 |
| **Irrelevante Umgebung** | Alles Übrige. Explizit ausschließen! | Lohnbuchhaltung, Vertrieb, statische Bemessung |

Das **Kontextdiagramm** ist ein einfaches Bild: in der Mitte ein Kasten (dein System), außen herum die Akteure und Nachbarsysteme, dazwischen Pfeile mit den Informationsflüssen. Es kostet dich eine halbe Stunde und verhindert wochenlange Unschärfe. Mach das früh, zeig es in deinem ersten Experteninterview vor und lass es korrigieren.

Formuliere zusätzlich eine explizite **Abgrenzung** in Textform („Nicht Gegenstand dieser Arbeit sind …"). Betreuer lieben das, weil es zeigt, dass du den Scope bewusst kontrollierst statt ihn zu verschweigen.

### 1.5 Die drei Ebenen: Ziele, Anwendungsfälle, Anforderungen

Anforderungen hängen nicht in der Luft. Sie leiten sich aus Zielen ab und konkretisieren sich in Interaktionen. Diese Ebenenlogik solltest du in deiner Arbeit sichtbar machen, weil sie die Frage „warum steht das da?" für jede einzelne Anforderung beantwortet.

```
Ebene 1  ZIEL            "Der Nachweisaufwand gegenüber der Fremdüberwachung
                          soll deutlich sinken."
            │
            ▼
Ebene 2  ANWENDUNGSFALL  "Fremdüberwachungstermin vorbereiten:
                          Der Qualitätsbeauftragte stellt alle Nachweise
                          eines Zeitraums zusammen."
            │
            ▼
Ebene 3  ANFORDERUNG     "Das System MUSS dem Qualitätsbeauftragten die
                          Möglichkeit bieten, alle Prüfaufzeichnungen eines
                          wählbaren Zeitraums als PDF-Dokument zu exportieren."
```

Von oben nach unten wird es konkreter und prüfbarer. Von unten nach oben lässt sich jede Anforderung rechtfertigen. Wenn du für eine Anforderung keinen Weg nach oben findest, ist sie vermutlich überflüssig — ein sehr wirksamer Filter gegen Wunschlisten.

---

## 2. Anforderungsarten: funktional, nicht-funktional, Randbedingungen

Das ist die Unterscheidung, nach der du explizit gefragt hast, und zugleich die, bei der in Abschlussarbeiten am meisten schiefgeht. Die gängige Einteilung kennt drei Kategorien.

### 2.1 Funktionale Anforderungen — das *Was*

Eine funktionale Anforderung beschreibt eine **Funktion, ein Verhalten oder eine Information**, die das System bereitstellen muss. Die Prüffrage lautet: *Kann das System das, oder kann es das nicht?* Die Antwort ist immer ja oder nein.

Drei Unterarten, die dir beim Finden helfen:

| Unterart | Frage | Beispiel WPK |
|---|---|---|
| **Funktionsanforderung** | Welche Leistung erbringt das System? | Das System muss aus erfassten Messwerten die Prüfstatistik einer Charge berechnen. |
| **Verhaltensanforderung** | Wie reagiert das System auf Ereignisse? | Wenn ein Messwert außerhalb der Toleranz liegt, muss das System eine Abweichungsmeldung erzeugen. |
| **Datenanforderung** | Welche Informationen muss das System kennen und speichern? | Das System muss zu jedem Element die verwendeten Materialchargen speichern. |

Typische Signalwörter für funktionale Anforderungen: erfassen, berechnen, speichern, anzeigen, exportieren, prüfen, melden, zuordnen, freigeben, sperren, drucken, übertragen.

### 2.2 Nicht-funktionale Anforderungen — das *Wie gut*

Eine nicht-funktionale Anforderung (auch: **Qualitätsanforderung**) beschreibt nicht, *ob* das System etwas kann, sondern **in welcher Güte** es das tut. Die Prüffrage lautet nicht ja/nein, sondern: *Wie gut? Gemessen woran?*

Das ist der Knackpunkt: **Eine nicht-funktionale Anforderung ohne Messgröße ist keine Anforderung, sondern ein Wunsch.** „Das System soll benutzerfreundlich sein" ist unprüfbar und damit wertlos. Verwende deshalb immer dieses Dreierpaket:

> **Qualitätsmerkmal + Messgröße + Zielwert (+ Messverfahren/Bedingung)**

| Unbrauchbar | Brauchbar |
|---|---|
| Das System soll schnell sein. | Das System muss eine Suche über alle Prüfaufzeichnungen eines Jahres in höchstens 3 Sekunden beantworten (bei bis zu 50.000 Datensätzen). |
| Das System soll benutzerfreundlich sein. | Ein eingewiesener Prüfer muss eine Standard-Elementprüfung in höchstens 90 Sekunden vollständig erfassen können, gemessen im Test mit fünf Prüfern. |
| Das System soll zuverlässig sein. | Das System muss während der Schichtzeit (06:00–18:00 Uhr) zu mindestens 99 % verfügbar sein. |
| Das System soll sicher sein. | Das System muss jede Änderung an einer freigegebenen Prüfaufzeichnung mit Zeitstempel, Benutzer und Änderungsgrund protokollieren; die ursprüngliche Fassung muss erhalten bleiben. |

**Die Qualitätsmerkmale nach ISO/IEC 25010** sind eine hervorragende Checkliste — geh sie durch und frage bei jedem: „Ist das in meinem Fall relevant? Wenn ja, mit welchem Zielwert?" Damit vermeidest du Lücken, und du kannst die Systematik in der Arbeit sauber zitieren.

| Merkmal (ISO 25010:2023) | Früher (2011) | Bedeutung | Relevanz WPK |
|---|---|---|---|
| **Functional Suitability** | dito | Funktionale Angemessenheit, Korrektheit, Vollständigkeit | hoch — Prüfungen müssen normkonform abbildbar sein |
| **Performance Efficiency** | dito | Zeitverhalten, Ressourcenverbrauch | mittel |
| **Compatibility** | dito | Koexistenz, Interoperabilität mit anderen Systemen | hoch — ERP, Messgeräte, Maschinendaten |
| **Interaction Capability** | Usability | Erlernbarkeit, Bedienbarkeit, Fehlerschutz, Zugänglichkeit | **sehr hoch** — Bedienung in der Halle, Handschuhe, Staub |
| **Reliability** | dito | Verfügbarkeit, Fehlertoleranz, Wiederherstellbarkeit | hoch — Produktion darf nicht stehen |
| **Security** | dito | Vertraulichkeit, Integrität, **Nachweisbarkeit**, Authentizität | **sehr hoch** — Aufzeichnungen sind Rechtsnachweise |
| **Maintainability** | dito | Änderbarkeit, Testbarkeit, Modularität | mittel — Prüfpläne ändern sich mit Normrevisionen |
| **Flexibility** | Portability | Anpassbarkeit, Installierbarkeit, Skalierbarkeit | mittel — mehrere Werke, wachsende Elementzahl |
| **Safety** | (neu) | Gefahrenfreiheit, Risikominderung im Betrieb | niedrig bis mittel |

Nutze die englischen Originalbegriffe mit deutscher Erläuterung — dann bist du zitierfähig und trotzdem verständlich.

### 2.3 Randbedingungen — das *Unverhandelbare*

Randbedingungen (Constraints) sind Vorgaben, die den Lösungsraum einschränken und über die **nicht verhandelt wird**. Sie sind weder funktional noch qualitativ, sondern gesetzt. Viele Lehrbücher zählen sie zu den nicht-funktionalen Anforderungen; die saubere Trennung als dritte Kategorie ist in Abschlussarbeiten üblich und macht deine Struktur klarer.

| Art | Beispiel in deinem Kontext |
|---|---|
| **Rechtlich/normativ** | Die Lösung muss die Anforderungen an Aufzeichnungen nach DIN 1052-11 erfüllen. Personenbezogene Daten (Prüferkennung) unterliegen der DSGVO. |
| **Technisch** | In der Produktionshalle steht kein flächendeckendes WLAN zur Verfügung. Vorhandene Messgeräte haben keine digitale Schnittstelle. |
| **Organisatorisch** | Die Lösung muss ohne dedizierte IT-Abteilung betreibbar sein. Vorhandene Formblätter dürfen nicht ersatzlos entfallen. |
| **Wirtschaftlich/zeitlich** | Einführung ohne Produktionsstillstand; Budgetrahmen. |

Randbedingungen sind in deiner Arbeit besonders wertvoll, weil sie sich sehr gut aus der Normanalyse und den Interviews belegen lassen und weil sie zeigen, dass du die reale Situation verstanden hast.

### 2.4 Die typischen Abgrenzungsfehler

Hier sind die Fälle, an denen fast jeder hängenbleibt:

**Fehler 1: Eine nicht-funktionale Anforderung verkleidet sich als funktionale.**
„Das System muss Daten verschlüsselt speichern." — Klingt funktional, ist aber eine Sicherheitsanforderung. Faustregel: Wenn das Verb eine *Eigenschaft der Ausführung* beschreibt statt einer fachlichen Leistung, ist es nicht-funktional.

**Fehler 2: Aus einer nicht-funktionalen Anforderung folgt eine funktionale — und beide werden vermischt.**
„Das System muss nachweissicher sein" (NFA, Security/Nachweisbarkeit) führt zu „Das System muss jede Änderung mit Benutzer und Zeitstempel protokollieren" (FA, Datenanforderung). **Beide notieren, und die Ableitung sichtbar machen.** Genau solche Ableitungsketten sind in einer Bachelorarbeit stark.

**Fehler 3: Lösung statt Anforderung.**
„Das System muss eine Android-App mit Barcode-Scanner bereitstellen." Das ist eine Lösungsentscheidung. Die dahinterliegende Anforderung: „Das System muss dem Prüfer die Möglichkeit bieten, ein Element ohne manuelle Eingabe der Elementnummer zu identifizieren." Frag dich bei jeder Anforderung mit Technologiebezug: **Warum? Was ist das eigentliche Bedürfnis?** (Die „Fünf-mal-Warum"-Technik funktioniert hier sehr gut.)

**Fehler 4: Prozessanforderung statt Systemanforderung.**
„Der Prüfer muss die Holzfeuchte vor der Beplankung messen." Das ist eine Anforderung an den *Prozess*, nicht an das *System*. Systemseitig daraus: „Das System muss die Freigabe zur Beplankung verhindern, solange kein Holzfeuchte-Messwert erfasst ist." Achte auf das Subjekt des Satzes — steht dort „das System"?

**Fehler 5: Mehrere Anforderungen in einem Satz.**
Jedes „und", „sowie", „bzw." ist verdächtig. Anforderungen müssen **atomar** sein, sonst kannst du sie nicht einzeln priorisieren, prüfen und abnehmen.

### 2.5 Schnelltest zur Einordnung

| Formulierung | Einordnung | Warum |
|---|---|---|
| „… muss Messwerte erfassen." | funktional | Fachliche Leistung, ja/nein prüfbar |
| „… muss Messwerte innerhalb von 2 s speichern." | nicht-funktional (Performance) | Güte der Ausführung |
| „… muss offline nutzbar sein." | nicht-funktional (Reliability/Flexibility) | Betriebsbedingung |
| „… muss die Elementnummer eindeutig vergeben." | funktional (Datenanforderung) | Fachliche Regel über Daten |
| „… darf nur von geschultem Personal bedient werden." | Randbedingung (organisatorisch) | Vorgabe an die Umgebung |
| „… muss DIN 1052-11 entsprechen." | Randbedingung — **und zu unscharf** | Muss in konkrete Einzelanforderungen zerlegt werden |

Der letzte Fall ist wichtig: Ein pauschaler Normverweis ist **keine** verwertbare Anforderung. Er ist eine *Quelle*, aus der du einzelne, konkrete Anforderungen ableiten musst. Wie das geht, steht in Kapitel 4.2.

---

## 3. Das Vorgehen: sieben Schritte zu deinem Anforderungsmodell

Das ist dein Fahrplan. Die Zeitangaben beziehen sich auf eine Bachelorarbeit mit etwa 12 Wochen Bearbeitungszeit, in der die Anforderungsanalyse den Hauptteil bildet.

| # | Schritt | Ergebnis | Aufwand |
|---|---|---|---|
| 1 | **Ziele und Systemabgrenzung klären** | Zielhierarchie, Kontextdiagramm, Scope-Abgrenzung | 3–5 Tage |
| 2 | **Stakeholder identifizieren** | Stakeholder-Map mit Rollen, Interessen, Verfügbarkeit | 1–2 Tage |
| 3 | **Ist-Analyse** | Ist-Prozessmodell, Dokumentenanalyse, Schwachstellenkatalog | 1,5–2 Wochen |
| 4 | **Erhebung** | Interviewtranskripte, kodierte Aussagen, Anforderungskandidaten | 2–3 Wochen |
| 5 | **Soll-Prozess entwerfen** | Soll-Prozessmodell mit Systemunterstützung | 1 Woche |
| 6 | **Anforderungen formulieren und strukturieren** | Anforderungskatalog, Use-Cases, Glossar, Datenmodell | 2 Wochen |
| 7 | **Prüfen, priorisieren, validieren** | Geprüfter, priorisierter, rückgekoppelter Katalog | 1 Woche |

Drei Hinweise, die den Unterschied machen:

**Es ist kein Wasserfall.** Du wirst in Schritt 6 merken, dass dir Informationen fehlen, und nochmal in Schritt 4 zurückgehen. Das ist normal und richtig. Beschreibe es in der Arbeit auch so — ein iteratives Vorgehen ist methodisch sauberer als die Behauptung, es sei linear gelaufen.

**Schritt 3 vor Schritt 4.** Geh nie unvorbereitet ins Experteninterview. Wenn du das WPK-Handbuch und die Formblätter des Betriebs vorher gelesen hast, stellst du in 60 Minuten dreimal so gute Fragen — und die Experten nehmen dich ernst.

**Schritt 7 ist nicht optional.** Die Rückkopplung der fertigen Anforderungen an mindestens einen Experten ist der Schritt, der aus einer Sammlung deiner Vermutungen ein validiertes Ergebnis macht. Methodisch ist das der Unterschied zwischen „ich habe mir was ausgedacht" und „ich habe ein Ergebnis erarbeitet und abgesichert". Plane dafür einen Termin von 60–90 Minuten fest ein.

---

## 4. Erhebung: wie du an belastbare Anforderungen kommst

Die Erhebungstechniken lassen sich in drei Gruppen einteilen: **befragende** (Interview, Fragebogen, Workshop), **beobachtende** (Feldbeobachtung, Apprenticing) und **dokumentenzentrierte** (Dokumentenanalyse, Systemarchäologie, Normanalyse). Für deinen Fall brauchst du aus jeder Gruppe etwas — und genau diese Kombination ist auch methodisch gut begründbar, weil sie **Triangulation** ermöglicht: Was du aus drei unterschiedlichen Quellen übereinstimmend herausbekommst, ist belastbar.

### 4.1 Dokumenten- und Artefaktanalyse — unterschätzt, bei dir Gold wert

Beginne hiermit, nicht mit Interviews. Die WPK ist ein dokumentengetriebener Prozess; das heißt, ein erheblicher Teil deines zukünftigen Datenmodells liegt bereits in Papierform vor.

Was du dir geben lassen solltest (und wonach du konkret fragen kannst):

- das **WPK-Handbuch** bzw. die Verfahrens- und Arbeitsanweisungen
- alle **Formblätter und Prüfprotokolle** (Wareneingang, Fertigungskontrolle, Holzfeuchte, Maßkontrolle, Abweichungen)
- ausgefüllte Exemplare der letzten Wochen (das zeigt, was *wirklich* eingetragen wird — oft weniger als vorgesehen)
- **Prüfpläne** mit Prüfmerkmalen, Prüfmitteln, Prüffrequenzen, Toleranzen
- der **Fremdüberwachungsbericht** des letzten Audits (dort stehen die Schwachstellen schon drin!)
- Kennzeichnungs-/Etikettenmuster, Lieferscheine, Materialzertifikate

Was du daraus ableitest:

| Fundstelle im Dokument | Wird im Modell zu |
|---|---|
| Jedes Feld eines Formblatts | Attribut im Datenmodell |
| Jedes Pflichtfeld | Validierungs-/Pflichtfeldanforderung |
| Jede Unterschriftszeile | Freigabe-/Verantwortlichkeitsanforderung, Rollenkonzept |
| Jede Toleranzangabe | Regel für automatische Bewertung von Messwerten |
| Jede Prüffrequenz | Anforderung an Terminsteuerung/Erinnerung |
| Jeder Medienbruch (Papier → Excel → Ordner) | Schwachstelle → Anforderung |

**Praxistipp:** Fotografiere oder scanne die Formblätter (mit Erlaubnis) und lege sie anonymisiert in den Anhang deiner Arbeit. Das ist starkes Belegmaterial, und deine Ist-Analyse wird dadurch nachvollziehbar.

### 4.2 Normanalyse: von der Norm zur Systemanforderung

Eine Norm ist keine Anforderungsliste für Software. Sie richtet sich an den *Betrieb*, nicht an ein *IT-System*. Die Übersetzung musst du leisten, und zwar in drei Schritten:

```
Normstelle                →  Betriebliche Pflicht        →  Systemanforderung
"Die Ergebnisse der          "Der Betrieb muss zu jeder      "Das System MUSS zu jeder
 Eigenüberwachung             Prüfung Datum, Prüfer,          Prüfaufzeichnung Datum,
 sind aufzuzeichnen           Ergebnis und Bewertung          Prüfer, Messwert und
 und aufzubewahren."          dokumentieren und über          Bewertung speichern."
                              die Aufbewahrungsfrist        + "Das System MUSS Prüf-
                              verfügbar halten."              aufzeichnungen über
                                                              mindestens X Jahre
                                                              revisionssicher
                                                              aufbewahren."
```

Lege dafür eine **Ableitungstabelle** an — sie ist eines der überzeugendsten Artefakte, die du in die Arbeit legen kannst:

| Norm-ID | Abschnitt | Normative Pflicht (sinngemäß) | Abgeleitete Anforderung(en) | Typ |
|---|---|---|---|---|
| N-01 | DIN 1052-11, Abschn. x.y | Aufzeichnung der Eigenüberwachung | FA-023, NFA-007 | FA + NFA |
| N-02 | DIN 1052-11, Abschn. x.y | Rückverfolgbarkeit der eingesetzten Materialien | FA-031, FA-032 | FA |

Zwei Warnungen:

1. **Zitiere Normtexte nicht wörtlich in Länge.** DIN-Normen sind urheberrechtlich geschützt. Gib den Inhalt sinngemäß wieder und verweise auf Abschnitt und Ausgabestand (z. B. „DIN 1052-11:2026-03, Abschnitt 8.2"). Kurze wörtliche Zitate mit Quellenangabe sind als wissenschaftliches Zitat zulässig, ganze Tabellen oder Abschnitte nicht.
2. **Prüfe den Ausgabestand.** DIN 1052-11 liegt in der Ausgabe **2026-03** vor und hat die Ausgabe 2022-12 ersetzt. Über die **MVV TB** (Muster-Verwaltungsvorschrift Technische Baubestimmungen, Teil C) wird sie bauaufsichtlich eingeführt, und die Bundesländer übernehmen sie mit eigenen Verwaltungsvorschriften. Welcher Stand für deinen Praxispartner gilt, ist eine eigene, in der Arbeit erwähnenswerte Frage. Ergänzend relevant: **DIN 1052-10** (Ergänzende Bestimmungen zur Herstellung und Ausführung, Ausgabe 2024-12) und **DIN 18200** (Übereinstimmungsnachweis für Bauprodukte — werkseigene Produktionskontrolle, Fremdüberwachung und Zertifizierung, Ausgabe 2021-04), die den allgemeinen Rahmen für WPK und Fremdüberwachung beschreibt.

### 4.3 Experteninterviews

Das ist dein Hauptinstrument. Hier die kompakte Anleitung.

#### Wen befragen?

Nicht „drei Leute aus dem Betrieb", sondern gezielt unterschiedliche **Rollen**, weil jede Rolle andere Anforderungen hat:

| Rolle | Was du von ihr bekommst |
|---|---|
| Prüfer / Werker in der Fertigung | Realität der Erfassung, Handhabbarkeit, Störungen im Alltag |
| Produktions-/Fertigungsleiter | Prozesssteuerung, Engpässe, Kennzahlen |
| Qualitätsbeauftragter / WPK-Verantwortlicher | Normauslegung, Nachweisführung, Auditvorbereitung |
| Geschäftsführung | Ziele, Wirtschaftlichkeit, Entscheidungskriterien |
| Fremdüberwacher / Prüfstelle (extern) | Was im Audit tatsächlich verlangt wird |
| ggf. IT-Verantwortlicher | Systemlandschaft, Schnittstellen, Betriebsrandbedingungen |

**Wie viele?** Für eine Bachelorarbeit sind **5 bis 8 Interviews** ein üblicher und gut begründbarer Umfang. Das Argument, das du in der Methodik nennst, heißt **theoretische Sättigung**: Du befragst, bis neue Interviews keine wesentlich neuen Inhalte mehr liefern. Wenn du nur 3 Interviews bekommst, ist das auch vertretbar — dann musst du es als Limitation benennen und über Dokumentenanalyse und Literatur stärker absichern.

#### Interviewform

Nimm das **halbstrukturierte Leitfadeninterview**. Begründung für die Methodik: Es gibt genug Struktur für Vergleichbarkeit zwischen den Interviews, lässt aber Raum für unerwartete Erkenntnisse — genau richtig in einer Domäne, die du selbst noch nicht vollständig überblickst.

#### Aufbau des Leitfadens (Trichterprinzip)

```
1. Einstieg / Warmup        „Beschreiben Sie mir bitte Ihren Arbeitsalltag."
   → Vertrauen, Kontext, Sprache des Gegenübers lernen
2. Ist-Prozess              „Führen Sie mich einmal durch eine Prüfung —
                             vom Auftrag bis zur Ablage."
   → das Rückgrat deiner Ist-Analyse
3. Schwachstellen           „Was ärgert Sie daran am meisten?"
                            „Wo passieren Fehler? Was dauert zu lange?"
   → Quelle für Ziele und Priorisierung
4. Anforderungen / Soll     „Wenn Sie frei wünschen dürften — was müsste
                             ein System können?"
   → Anforderungskandidaten (kritisch prüfen, oft Lösungen statt Bedürfnisse)
5. Randbedingungen          „Was darf auf keinen Fall passieren?"
                            „Was muss aus Normsicht zwingend erhalten bleiben?"
   → Constraints, Ausschlusskriterien
6. Abschluss                „Habe ich etwas Wichtiges nicht gefragt?"
                            „Wen sollte ich noch sprechen?"
   → oft die ergiebigste Frage des ganzen Interviews
```

Eine fertige, ausformulierte Version findest du in [`../vorlagen/interviewleitfaden.md`](../vorlagen/interviewleitfaden.md).

#### Fragetechnik: das Wichtigste in Kürze

| Tu das | Vermeide das |
|---|---|
| Offene Fragen („Wie läuft …?") | Suggestivfragen („Wäre eine App nicht praktisch?") |
| Nach konkreten Beispielen fragen („Wann ist das zuletzt passiert?") | Ja/Nein-Fragen in der Hauptphase |
| Pausen aushalten — Menschen füllen Stille mit Inhalt | Ins Wort fallen, eigene Lösungen anbieten |
| Nachhaken: „Und was passiert dann?" | Mehrere Fragen auf einmal |
| Zurückspiegeln: „Habe ich richtig verstanden, dass …?" | Fachjargon, den du selbst nicht sicher beherrschst |
| Nach Ausnahmen fragen („Was, wenn das Element nicht in Ordnung ist?") | Nur den Normalfall erfassen — Sonderfälle erzeugen die meisten Anforderungen |

Besonders ergiebig für Anforderungen sind **Ausnahme- und Fehlerfälle**. Der Normalfall ist schnell erzählt; die interessanten Anforderungen stecken in „und wenn der Messwert zu hoch ist, dann …".

#### Organisation und Formalia

- **Dauer:** 45–75 Minuten. Länger hält niemand konzentriert durch.
- **Ort:** wenn möglich im Betrieb, mit anschließendem Rundgang durch die Fertigung. Eine halbe Stunde Werksbegehung ersetzt zwei Stunden Erklärung.
- **Aufzeichnung:** Tonaufnahme nur mit schriftlicher **Einwilligung**. Kläre Anonymisierung („Experte A, Qualitätsbeauftragter, Betrieb mit ca. X Mitarbeitern") und Umgang mit Betriebsgeheimnissen. Eine Einwilligungserklärung gehört in den Anhang.
- **Protokoll:** Innerhalb von 24 Stunden nachbereiten, solange du den Kontext noch im Kopf hast.

#### Auswertung: von der Aussage zur Anforderung

Für eine Bachelorarbeit reicht eine **zusammenfassende qualitative Inhaltsanalyse** in Anlehnung an Mayring. Volltranskription aller Interviews ist aufwendig; üblich und vertretbar ist:

1. **Transkribieren** — entweder vollständig oder als inhaltlich-selektives Transkript der relevanten Passagen (automatische Transkription, danach manuelle Korrektur).
2. **Paraphrasieren und kodieren** — jede relevante Aussage bekommt einen Code. Kategorien bildest du teils vorab (deduktiv, z. B. aus den Prozessschritten), teils aus dem Material heraus (induktiv).
3. **Bündeln** — gleichartige Aussagen verschiedener Interviews zusammenfassen. Mehrfachnennungen sind ein starkes Priorisierungsargument.
4. **Übersetzen** — aus jeder gebündelten Aussage eine oder mehrere Anforderungen nach Satzschablone formulieren.

Führe das in einer **Ableitungstabelle** mit, sonst verlierst du die Nachvollziehbarkeit:

| Aussagen-ID | Interview | Paraphrasierte Aussage | Kategorie | Abgeleitete Anforderung |
|---|---|---|---|---|
| A-014 | I-02 (QMB) | „Vor dem Audit suche ich zwei Tage lang Protokolle zusammen." | Nachweisführung | FA-041, FA-042 |
| A-015 | I-01 (Prüfer) | „Mit Handschuhen tippt man sich auf dem Handy die Finger wund." | Bedienbarkeit | NFA-003 |

Diese Tabelle ist das Herzstück deiner **Traceability** und beantwortet die wahrscheinlichste Prüfungsfrage überhaupt: *„Woher wissen Sie das?"*

### 4.4 Beobachtung und Werksbegehung

Menschen beschreiben ihre Arbeit anders, als sie sie tun — nicht aus Unehrlichkeit, sondern weil Routinen unbewusst ablaufen. Eine strukturierte Beobachtung deckt genau die Dinge auf, die niemand erwähnt:

- Wo wird wirklich geschrieben? (Klemmbrett, Handrücken, Zettel in der Hosentasche?)
- Wann wird geschrieben — sofort oder gesammelt am Schichtende?
- Wo steht der Rechner, und wie weit ist der Weg dorthin?
- Welche Lichtverhältnisse, welcher Lärm, welche Handschuhe, wie viel Staub?
- Wie oft wird etwas gesucht?

Diese Beobachtungen liefern dir fast alle wichtigen nicht-funktionalen Anforderungen. Notiere sie in einem Beobachtungsprotokoll mit Zeitstempel — auch das ist zitierfähiges Material.

### 4.5 Weitere Techniken (kurz)

- **Workshop / Fokusgruppe:** effizient, wenn du mehrere Rollen gleichzeitig zusammenbekommst, und gut zur *Validierung* in Schritt 7. Nachteil: Hierarchie kann Aussagen verzerren.
- **Fragebogen:** nur sinnvoll, wenn du viele gleichartige Befragte hast (z. B. 30 Werker). Bei 5 Experten lohnt er nicht.
- **Prototyping:** ein einfacher Klickdummy oder auch nur eine Bildschirmskizze auf Papier erzeugt in der Validierungsrunde mehr konkrete Rückmeldung als jede Textliste. Sehr empfehlenswert, wenn Zeit bleibt.
- **Benchmark/Marktanalyse:** Da es nach deiner Einschätzung keine dedizierte digitale WPK-Lösung für den Holztafelbau gibt, ist eine kurze Analyse angrenzender Systeme (allgemeine QM-/CAQ-Software, Bautagebuch-Apps, MES im Fertigteilbau) wertvoll — sie belegt die Forschungslücke und liefert Anforderungsideen.

### 4.6 Traceability: der rote Faden

**Verfolgbarkeit** bedeutet: Zu jeder Anforderung ist bekannt, woher sie kommt und wohin sie führt. Praktisch brauchst du zwei Richtungen:

- **Rückwärts (Pre-Traceability):** Anforderung → Quelle (Interviewaussage, Normstelle, Schwachstelle, Dokument). Belegt, dass du nichts erfunden hast.
- **Vorwärts (Post-Traceability):** Anforderung → Use-Case → Prozessschritt (und später: → Implementierung, → Test). Belegt Vollständigkeit und Abdeckung.

Für eine Bachelorarbeit reichen dafür zwei zusätzliche Spalten in der Anforderungstabelle („Quelle" und „Anwendungsfall"). Kein Werkzeug nötig, aber unbedingt konsequent führen — nachträglich rekonstruieren ist die Hölle.

---

## 5. Ist- und Soll-Prozess modellieren

Du hast Ist-/Soll-Prozesse bereits eingeplant — sehr gut, denn sie sind in deinem Fall die natürliche Brücke von der Erhebung zu den Anforderungen: **Jede Schwachstelle im Ist-Prozess erzeugt eine Anforderung an das System, das sie beseitigen soll.** Diese Argumentationskette ist sauber, prüfbar und macht deine Anforderungsherleitung nachvollziehbar.

### 5.1 Welche Notation?

**Empfehlung: BPMN 2.0**, beschränkt auf eine kleine Symbolmenge. Gründe: Standardisiert (ISO/IEC 19510), weit verbreitet, kostenlose Werkzeuge, für Praktiker ohne Vorkenntnisse gut lesbar. Die Alternative **EPK** (Ereignisgesteuerte Prozesskette) ist im deutschsprachigen betriebswirtschaftlichen Umfeld ebenfalls verbreitet und etwas einfacher; wenn dein Lehrstuhl EPK lehrt, nimm EPK. **UML-Aktivitätsdiagramme** tun es auch, wirken aber eher technisch.

Du brauchst realistisch nur diese Elemente:

| Symbol | Bedeutung | Verwendung |
|---|---|---|
| Abgerundetes Rechteck | **Aktivität / Aufgabe** | „Holzfeuchte messen" |
| Kreis dünn / dick | **Start- / Endereignis** | „Fertigungsauftrag liegt vor" |
| Raute mit × | **Exklusives Gateway** (entweder/oder) | „Messwert in Toleranz?" |
| Raute mit + | **Paralleles Gateway** (und) | zwei Prüfungen gleichzeitig |
| Pfeil | **Sequenzfluss** | Reihenfolge |
| Pool / Lane | **Beteiligte Rolle** | Prüfer, Fertigungsleiter, QMB |
| Dokumentsymbol | **Datenobjekt** | „Prüfprotokoll (Papier)" |
| Gestrichelter Pfeil | **Nachrichtenfluss** | Übergabe an Fremdüberwacher |

Zeichne mit **Lanes pro Rolle** — dann werden Übergaben zwischen Personen sichtbar, und genau an den Übergaben liegen die Schwachstellen.

### 5.2 Vom Ist zum Soll

**Schritt 1 — Ist-Prozess aufnehmen.** Zeichne, was *tatsächlich* passiert, nicht was im Handbuch steht. Der Unterschied zwischen beidem ist übrigens selbst ein Ergebnis, das du in der Arbeit benennen solltest.

**Schritt 2 — Schwachstellen markieren.** Geh den Ist-Prozess systematisch nach folgenden Kategorien durch:

| Kategorie | Leitfrage | Typisch bei Papier-WPK |
|---|---|---|
| **Medienbruch** | Wo wechselt das Medium? | Papier → Excel → Scan → Ordner |
| **Doppelerfassung** | Wo wird dasselbe zweimal erfasst? | Elementnummer auf 4 Formblättern |
| **Suchaufwand** | Wo wird gesucht? | Protokoll zu Element X vom März |
| **Fehleranfälligkeit** | Wo entstehen Fehler? | Handschrift, Zahlendreher, fehlende Felder |
| **Verzögerung** | Wo entstehen Wartezeiten? | Freigabe erst am Schichtende |
| **Fehlende Transparenz** | Wer weiß etwas nicht rechtzeitig? | Offene Prüfungen, überfällige Kalibrierung |
| **Nachweislücke** | Was ist im Audit schwer nachweisbar? | Vollständigkeit, Unveränderbarkeit |
| **Personenabhängigkeit** | Was weiß nur eine Person? | Auslegung von Prüfregeln |

Trage die Funde in den [Schwachstellenkatalog](../vorlagen/schwachstellenkatalog.md) ein — mit ID, Prozessschritt, Kategorie, Beschreibung, Auswirkung und Quelle.

**Schritt 3 — Soll-Prozess entwerfen.** Der Soll-Prozess zeigt denselben Ablauf mit Systemunterstützung: Welche Schritte entfallen, welche werden automatisiert, welche bleiben manuell, aber werden systemgestützt? Kennzeichne dabei die **Systemunterstützung** explizit (z. B. eigene Lane „WPK-System" oder farbliche Markierung). Das Soll-Modell ist selbst ein Erhebungsinstrument: Leg es einem Experten vor, und du bekommst sofort qualifizierte Kritik.

**Schritt 4 — Anforderungen ableiten.** Jetzt wird die Kette geschlossen:

```
Schwachstelle SW-07                Soll-Prozessschritt            Anforderung
"Prüfergebnisse werden      →      "System bewertet Messwert   →  FA-018: Das System MUSS
 händisch mit der Toleranz-         automatisch gegen den          einen erfassten Messwert
 tabelle verglichen; bei            hinterlegten Toleranz-         automatisch gegen den im
 Zeitdruck wird der Abgleich        bereich."                      Prüfplan hinterlegten
 übersprungen."                                                    Toleranzbereich bewerten.
                                                                FA-019: Wenn ein Messwert
                                                                   außerhalb liegt, MUSS das
                                                                   System eine Abweichung
                                                                   anlegen.
```

Diese dreispaltige Darstellung (Schwachstelle → Soll → Anforderung) ist ein exzellentes Element für deinen Ergebnisteil, weil sie in einem Bild zeigt, dass deine Anforderungen aus der Empirie stammen und nicht aus dem Bauch.

---

## 6. Dokumentation: Notation, Satzschablone, Attribute

### 6.1 Welche Notation? — Empfehlung mit Begründung

Du hast die Wahl mir überlassen. Hier die drei gängigen Optionen und meine Empfehlung.

| Ansatz | Stärken | Schwächen | Passt für dich? |
|---|---|---|---|
| **Natürlichsprachlich mit Satzschablone** (SOPHIST/MASTeR) + Use-Cases | Für Praktiker ohne Vorkenntnisse lesbar; erzwingt Präzision; rechtlich saubere Verbindlichkeitsstufen; im deutschsprachigen RE Standard; gut zitierbar | Bei sehr großen Systemen unübersichtlich | **Ja** |
| **User Stories** + Akzeptanzkriterien (Gherkin) | Nah an agiler Praxis; nutzerzentriert; schnell zu schreiben | Bewusst unpräzise („Platzhalter für ein Gespräch"); schwach bei normativen Pflichten und nicht-funktionalen Anforderungen; ohne Backlog-Kontext wenig aussagekräftig | Nur ergänzend |
| **Modellbasiert** (UML/SysML: Use-Case-, Aktivitäts-, Klassendiagramme als Primärartefakt) | Formal präzise; gut für Struktur und Zusammenhänge | Hohe Einarbeitung; Fachexperten können es nicht gegenlesen → Validierung wird schwierig; Detailanforderungen lassen sich schlecht rein grafisch ausdrücken | Nur als Ergänzung |

**Meine Empfehlung: ein hybrides Modell mit natürlichsprachlichem Kern.**

```
Kern:       Anforderungskatalog in Satzschablone, tabellarisch mit Attributen
Ergänzung:  Kontextdiagramm            (Systemabgrenzung)
            BPMN Ist- und Soll-Prozess (Erhebungs- und Argumentationsgrundlage)
            UML-Use-Case-Diagramm      (Überblick: wer nutzt was)
            5–8 ausformulierte Use-Cases (die wichtigsten Abläufe im Detail)
            Fachliches Datenmodell/ERD light (welche Objekte, welche Beziehungen)
            Glossar                    (einheitliche Fachsprache)
```

Begründung, die du in der Arbeit so verwenden kannst: Der natürlichsprachliche Kern ist für die Fachexperten **validierbar** — sie können ihn lesen und korrigieren, was bei einem reinen UML-Modell nicht gegeben wäre. Die Satzschablone kompensiert die bekannte Schwäche natürlicher Sprache (Mehrdeutigkeit) durch eine feste Syntax. Die Modelle ergänzen die Aspekte, die sich in Prosa schlecht darstellen lassen: Systemgrenze, Ablauflogik und Datenstruktur. Diese Kombination entspricht der in ISO/IEC/IEEE 29148 und bei Pohl/Rupp beschriebenen Praxis, Anforderungen sowohl sprachlich als auch modellbasiert zu dokumentieren.

Die Einordnung der Alternativen gehört trotzdem in die Arbeit — ein kurzer Absatz „Warum nicht User Stories?" zeigt Methodenbewusstsein und beugt genau dieser Prüfungsfrage vor.

### 6.2 Die Satzschablone — das wichtigste Werkzeug überhaupt

Wenn du aus diesem Leitfaden nur eine Sache mitnimmst, dann diese. Die Satzschablone (bekannt als MASTeR der SOPHIST GmbH) gibt jeder Anforderung eine feste Satzstruktur:

```
 <Bedingung>   <SYSTEMNAME>   <Verbindlichkeit>   <Objekt + Ergänzung>   <Prozesswort>
  optional                      MUSS/SOLLTE/WIRD
```

**Die drei Verbindlichkeitsstufen** — verwende sie konsequent und erkläre sie einmal in der Arbeit:

| Wort | Bedeutung |
|---|---|
| **MUSS** | rechtlich/vertraglich verbindlich, zwingend erforderlich |
| **SOLLTE** | dringend empfohlen, aber verzichtbar |
| **WIRD** | in Zukunft vorgesehen, für die aktuelle Version nicht verbindlich |

Schreib sie in Großbuchstaben (oder fett) — das macht die Verbindlichkeit auf einen Blick sichtbar und ist in der Praxis so üblich.

**Die drei Anforderungstypen** und ihre Satzmuster:

**Typ 1 — Selbstständige Systemaktivität** (das System tut etwas von sich aus):
> `<Bedingung>` Das System MUSS `<Objekt>` `<Prozesswort>`.
>
> *Beispiel:* Das System **MUSS** bei Überschreitung des zulässigen Holzfeuchtewerts eine Abweichungsmeldung **erzeugen**.

**Typ 2 — Benutzerinteraktion** (das System ermöglicht dem Nutzer etwas):
> Das System MUSS `<Akteur>` **die Möglichkeit bieten**, `<Objekt>` zu `<Prozesswort>`.
>
> *Beispiel:* Das System **MUSS** dem Prüfer **die Möglichkeit bieten**, zu einem Element mehrere Holzfeuchte-Messwerte mit Messstelle zu **erfassen**.

**Typ 3 — Schnittstellenanforderung** (das System reagiert auf etwas von außen):
> Das System MUSS **fähig sein**, `<Objekt>` zu `<Prozesswort>`.
>
> *Beispiel:* Das System **MUSS fähig sein**, Auftrags- und Elementdaten aus dem vorhandenen ERP-System zu **übernehmen**.

**Bedingungen** stellst du voran — logische („Wenn der Messwert außerhalb der Toleranz liegt, …") oder zeitliche („Sobald die letzte Prüfung eines Elements freigegeben ist, …").

**Für nicht-funktionale Anforderungen** ergänzt du das Qualitätsmerkmal und die Messgröße:

> Das System MUSS `<Leistung>` `<Messgröße mit Zielwert>` `<unter Bedingung>`.
>
> *Beispiel:* Das System **MUSS** die Suche nach Prüfaufzeichnungen eines Elements in **höchstens 3 Sekunden** beantworten, **bei bis zu 50.000 gespeicherten Aufzeichnungen**.

**Warum das Ganze?** Die Schablone zwingt dich, drei Dinge explizit zu machen, die man in freier Prosa gern verschluckt: *Wer* handelt (das System), *wie verbindlich* ist es, und *was genau* passiert. Nebenbei eliminiert sie Passivkonstruktionen, die häufigste Ursache unklarer Anforderungen. („Die Messwerte werden gespeichert" — von wem? wann? wo?)

### 6.3 Attribute: was zu jeder Anforderung gehört

Eine Anforderung ist mehr als ihr Satz. Diese Attribute solltest du führen (die mit ★ sind Pflicht, der Rest ist wertvoll):

| Attribut | Zweck | Beispiel |
|---|---|---|
| ★ **ID** | Eindeutige Referenzierbarkeit | FA-018 |
| ★ **Titel** | Kurzbezeichnung für Übersichten | Automatische Toleranzbewertung |
| ★ **Beschreibung** | Die Anforderung nach Satzschablone | Das System MUSS … |
| ★ **Typ** | FA / NFA / RB | NFA |
| ★ **Quelle** | Woher stammt sie? (Traceability) | I-02, A-014; DIN 1052-11 Abschn. x.y |
| ★ **Priorität** | Muss/Soll/Kann (MoSCoW) | Must |
| **Kategorie** | Fachliche Gruppierung | Prüfdurchführung |
| **Akzeptanzkriterium** | Woran erkennt man die Erfüllung? | Messwert 19,5 % bei Grenze 18 % → Abweichung wird angelegt |
| **Stakeholder** | Wer will sie? | Qualitätsbeauftragter |
| **Anwendungsfall** | Zugehöriger Use-Case | UC-04 |
| **Abhängigkeit** | Beziehung zu anderen Anforderungen | setzt FA-012 voraus |
| **Begründung (Rationale)** | Warum? | Schwachstelle SW-07, Fehlervermeidung |
| **Status** | Vorschlag / geprüft / validiert | validiert |

Die Spalte **Akzeptanzkriterium** ist die wirksamste Qualitätskontrolle, die es gibt: Wenn dir kein Kriterium einfällt, mit dem man die Erfüllung überprüfen könnte, ist die Anforderung nicht verifizierbar — und muss umformuliert werden. Mach das zur Routine.

Eine fertige Tabellenstruktur liegt in [`../vorlagen/anforderungsliste.csv`](../vorlagen/anforderungsliste.csv), ein ausführlicher Steckbrief für die wichtigsten Anforderungen in [`../vorlagen/anforderungs-steckbrief.md`](../vorlagen/anforderungs-steckbrief.md).

### 6.4 ID-Schema

Halte es simpel und sprechend, und **vergib IDs nie neu**, auch wenn eine Anforderung entfällt (sonst brechen alle Querverweise):

```
FA-001 … FA-nnn     Funktionale Anforderungen
NFA-001 … NFA-nnn   Nicht-funktionale Anforderungen
RB-001 … RB-nnn     Randbedingungen
UC-01 … UC-nn       Anwendungsfälle
SW-01 … SW-nn       Schwachstellen (Ist-Analyse)
Z-01 … Z-nn         Ziele
S-01 … S-nn         Stakeholder
A-001 … A-nnn       Interviewaussagen
N-01 … N-nn         Normstellen
```

Optional mit Fachbereichspräfix, wenn es viele Anforderungen werden: `FA-PRF-001` (Prüfung), `FA-NAW-001` (Nachweisführung) usw. Für 60–100 Anforderungen ist die einfache Nummerierung aber übersichtlicher.

### 6.5 Use-Cases (Anwendungsfälle)

Ein Use-Case beschreibt eine vollständige Interaktion zwischen einem Akteur und dem System, die für den Akteur ein **fachlich sinnvolles Ergebnis** liefert. Zwei Detailstufen:

**Kurzbeschreibung** (für alle Use-Cases, 2–3 Sätze):
> **UC-04 Elementprüfung durchführen** — Der Prüfer identifiziert ein Element, erfasst die im Prüfplan vorgesehenen Merkmale, das System bewertet die Messwerte und legt bei Abweichungen eine Abweichungsmeldung an. Ergebnis: eine vollständige, bewertete Prüfaufzeichnung.

**Ausführliche Beschreibung** (nur für die 5–8 wichtigsten) mit Vorbedingung, Nachbedingung, Standardablauf, Alternativ- und Ausnahmeabläufen. Die Schablone dafür liegt in [`../vorlagen/use-case-schablone.md`](../vorlagen/use-case-schablone.md), ein vollständig ausgefülltes Beispiel steht in Kapitel 8.6.

Der **größte Nutzen** ausführlicher Use-Cases: Die Ausnahmeabläufe zwingen dich, über Fälle nachzudenken, die im Interview nie zur Sprache kamen („Was, wenn der Prüfer die Prüfung abbricht?", „Was, wenn das Element schon geprüft wurde?"). Erfahrungsgemäß entstehen dabei 20–30 % zusätzliche, wichtige Anforderungen.

Ein **Use-Case-Diagramm** (UML) fasst alle Use-Cases mit ihren Akteuren auf einer Seite zusammen — gut als Überblicksgrafik am Anfang des Ergebniskapitels, aber kein Ersatz für die Textbeschreibungen.

### 6.6 Glossar

Unterschätzt, aber in einer Domäne wie deiner entscheidend. Ein Begriff, drei Bedeutungen — das ist der Normalfall in Betrieben:

- Ist ein „Element" die Wandtafel oder auch das Raummodul?
- Ist eine „Prüfung" der einzelne Messvorgang oder die Gesamtprüfung eines Elements?
- Heißt „Freigabe" die Freigabe zur Weiterbearbeitung oder zur Auslieferung?
- Ist „Charge" die Materiallieferung oder das Fertigungslos?

Lege das Glossar **ab dem ersten Interview** an und pflege es laufend. Es kommt in den Anhang der Arbeit und wird bei der Anforderungsformulierung konsequent benutzt: Jeder Begriff, der im Glossar steht, wird in den Anforderungen genau so verwendet — nicht mal so, mal anders. Vorlage: [`../vorlagen/glossar.md`](../vorlagen/glossar.md).

---

## 7. Qualitätssicherung und Priorisierung

### 7.1 Qualitätskriterien für einzelne Anforderungen

ISO/IEC/IEEE 29148 nennt Kriterien, an denen sich jede einzelne Anforderung messen lassen muss:

| Kriterium | Frage | Typischer Verstoß |
|---|---|---|
| **Notwendig** | Würde das Fehlen ein Problem verursachen? | „Nice to have"-Wünsche ohne Zielbezug |
| **Eindeutig** | Kann man das nur auf eine Weise verstehen? | „zeitnah", „geeignet", „intuitiv" |
| **Vollständig** | Steht alles Nötige drin? | Bedingung fehlt, Akteur fehlt |
| **Einzeln (atomar)** | Nur eine Anforderung pro Satz? | „und" als Aufzählung |
| **Konsistent** | Kein Widerspruch zu anderen? | FA-012 fordert Sperre, FA-030 erlaubt Umgehung |
| **Verifizierbar** | Ist die Erfüllung überprüfbar? | „benutzerfreundlich" ohne Messgröße |
| **Realisierbar** | Technisch und wirtschaftlich machbar? | „fehlerfrei unter allen Umständen" |
| **Verfolgbar** | Quelle bekannt und dokumentiert? | Anforderung ohne Herkunft |

Und für den **Katalog als Ganzes**: vollständig (alle Prozessschritte abgedeckt), widerspruchsfrei, verständlich, angemessen strukturiert.

### 7.2 Sprachliche Defekte — die Prüfliste

Natürliche Sprache ist mehrdeutig. Diese sechs Fehlertypen erwischen fast alle Anforderungen beim ersten Entwurf:

| Defekt | Beispiel | Problem | Besser |
|---|---|---|---|
| **Passiv ohne Akteur** | „Die Werte werden geprüft." | Wer prüft? System oder Mensch? | „Das System MUSS die Werte … prüfen." |
| **Nominalisierung** | „Die Erfassung erfolgt digital." | Der Vorgang ist verdeckt, Details fehlen | „Das System MUSS dem Prüfer die Möglichkeit bieten, … zu erfassen." |
| **Unvollständiger Vergleich** | „Die Suche muss schneller sein." | Schneller als was? | „… in höchstens 3 Sekunden." |
| **Universalquantor** | „Alle Prüfungen müssen jederzeit …" | Wirklich alle? Wirklich jederzeit? | Präzisieren oder Ausnahmen benennen |
| **Unklares Substantiv** | „Die Daten werden archiviert." | Welche Daten? | „Prüfaufzeichnungen einschließlich Messwerten und Bewertung" |
| **Modaler Weichmacher** | „möglichst", „in der Regel", „soweit möglich" | Nicht prüfbar | Streichen oder als SOLLTE deklarieren |

Geh deinen fertigen Katalog einmal komplett mit dieser Liste durch (Suchfunktion nach „werden", „möglichst", „und", „alle", „schnell", „einfach"). Das dauert zwei Stunden und hebt die Qualität deiner Arbeit spürbar. Als Checkliste: [`../vorlagen/pruefliste-anforderungsqualitaet.md`](../vorlagen/pruefliste-anforderungsqualitaet.md).

### 7.3 Validierung mit den Experten

Prüfung (*Verifikation*: „ist es richtig gebaut?") und Abstimmung (*Validierung*: „ist es das Richtige?") sind zwei verschiedene Dinge. Die Validierung brauchst du zwingend, und dafür gibt es drei praktikable Formate:

1. **Review per Dokument:** Katalog verschicken, Kommentare einsammeln. Günstig, aber die Rücklaufquote ist erfahrungsgemäß niedrig und die Rückmeldungen oberflächlich.
2. **Walkthrough im Termin (empfohlen):** Du gehst mit einem oder zwei Experten die Anforderungen durch und lässt sie kommentieren. 60–90 Minuten reichen für 60–80 Anforderungen, wenn du sie nach Anwendungsfällen gruppierst und nicht jeden Satz vorliest.
3. **Szenariobasierte Validierung:** Du erzählst einen konkreten Ablauf („Montag früh, Element 4711, Holzfeuchte 19,5 %, Fremdüberwachung nächste Woche …") und prüfst gemeinsam, ob die Anforderungen diesen Fall vollständig abdecken. Findet Lücken am zuverlässigsten.

**Dokumentiere die Validierung** — wer, wann, wie lange, welche Änderungen wurden vorgenommen. Eine kleine Tabelle „Ergebnisse der Validierung" mit Änderungshistorie ist ein Qualitätsmerkmal deiner Arbeit und beantwortet die Frage nach der Güte deines Ergebnisses.

### 7.4 Priorisierung

**Empfehlung: MoSCoW.** Einfach, verbreitet, für den Umfang deiner Arbeit völlig ausreichend.

| Stufe | Bedeutung | Faustregel für den Anteil |
|---|---|---|
| **Must have** | Ohne diese Anforderung ist die Lösung nutzlos oder nicht normkonform | ca. 40–60 % |
| **Should have** | Wichtig, aber die Lösung funktioniert zunächst auch ohne | ca. 20–30 % |
| **Could have** | Wünschenswert, wenn Aufwand und Zeit es zulassen | ca. 10–20 % |
| **Won't have (this time)** | Bewusst zurückgestellt — aber dokumentiert | Rest |

Zwei Hinweise: Erstens, **normativ zwingende Anforderungen sind immer „Must"** — hier gibt es keinen Verhandlungsspielraum, und das ist ein gutes Argument für die Kategorisierung. Zweitens: Lass die Priorisierung **nicht allein von dir** vorgenommen werden, sondern von den Stakeholdern (im Validierungstermin, oder per kurzer Abfrage). Priorisierung ist eine fachliche Entscheidung, keine analytische.

Ergänzend möglich, wenn du es methodisch aufwerten willst:

- **Kano-Modell:** unterscheidet Basis-, Leistungs- und Begeisterungsmerkmale. Nett für die Diskussion, aber Erhebungsaufwand (eigener Fragebogen).
- **Aufwand-Nutzen-Matrix:** Vier Quadranten, Anforderungen einsortieren. Gut als Grafik, wenn du Aufwandsschätzungen bekommst.
- **Gewichtete Punktvergabe:** Stakeholder verteilen je 100 Punkte. Schnell, quantitativ auswertbar, wirkt in der Arbeit sauber.

**Won't have nicht wegwerfen!** Ein dokumentierter Ausschluss („bewusst nicht berücksichtigt, weil …") ist wissenschaftlich wertvoller als Stillschweigen und liefert dir zugleich den Ausblick am Ende der Arbeit.

### 7.5 Akzeptanzkriterien

Zu jeder Must-have-Anforderung gehört ein Akzeptanzkriterium: ein konkreter, überprüfbarer Fall, an dem sich die Erfüllung zeigt. Zwei brauchbare Formate:

**Einfach (empfohlen):**
> Erfüllt, wenn: Bei Eingabe eines Holzfeuchtewerts von 19,5 % (zulässig ≤ 18 %) erzeugt das System automatisch eine Abweichungsmeldung mit Bezug zu Element und Messwert.

**Given-When-Then (Gherkin), falls du es formaler magst:**
> **Gegeben** ein Prüfplan mit Grenzwert Holzfeuchte ≤ 18 %
> **wenn** der Prüfer den Wert 19,5 % erfasst,
> **dann** erzeugt das System eine Abweichungsmeldung und sperrt die Freigabe des Elements.

Beides ist in Ordnung. Wichtig ist nur, dass es **einen konkreten Fall mit konkreten Werten** beschreibt und nicht die Anforderung nochmal in anderen Worten wiederholt.

---

## 8. Anwendung: WPK im Holztafelbau

Ab hier wird es fachlich. **Wichtig:** Die folgenden Inhalte sind fachlich plausible Arbeitshypothesen, die dir als Startpunkt und Strukturierungshilfe dienen. Sie ersetzen nicht die Analyse der Originalnorm und die Erhebung im konkreten Betrieb. Prüfe jede normbezogene Aussage an DIN 1052-11 in der für deinen Praxispartner geltenden Ausgabe.

### 8.1 Die Domäne in Kürze

**Werkseigene Produktionskontrolle (WPK)** ist die ständige, vom Hersteller selbst durchgeführte und dokumentierte Überwachung der Produktion mit dem Ziel, dass die hergestellten Bauprodukte dauerhaft den erklärten Eigenschaften und den technischen Spezifikationen entsprechen. Sie ist kein einmaliger Nachweis, sondern ein laufender Prozess. Den allgemeinen Rahmen — WPK, Fremdüberwachung und Zertifizierung als Verfahren des Übereinstimmungsnachweises — beschreibt **DIN 18200**.

Für deinen Gegenstand gilt speziell **DIN 1052-11 „Holzbauwerke — Herstellung und Ausführung von Holzbauwerken — Teil 11: Vorgefertigte Wand-, Decken- und Dachelemente und Raummodule — Anforderungen an die Herstellung"** (Ausgabe **2026-03**, ersetzt 2022-12). Die Norm legt Anforderungen an Bauteile und Herstellung vorgefertigter tragender und/oder raumabschließender Wand-, Decken- und Dachelemente sowie Raummodule fest und enthält Festlegungen zu Eigenüberwachung, Fremdüberwachung und Herstellerzertifizierung. Bauaufsichtlich eingeführt wird sie über die **MVV TB** (Teil C) und deren Umsetzung in den Ländern. Ergänzend relevant ist **DIN 1052-10** (Ausgabe 2024-12) mit ergänzenden Bestimmungen zur Herstellung und Ausführung von Holzbauwerken.

Zwei Begriffe, die du sauber trennen musst — sie sind der Kern deines Systemzwecks:

| | **Eigenüberwachung (WPK)** | **Fremdüberwachung** |
|---|---|---|
| Wer | der Hersteller selbst | eine anerkannte, unabhängige Überwachungsstelle |
| Wann | laufend, in jeder Produktion | in regelmäßigen Abständen, stichprobenartig |
| Gegenstand | Material, Fertigung, Produkt, Prüfmittel, Personal, Dokumentation | Wirksamkeit der WPK und Stichproben am Produkt |
| Ergebnis | Aufzeichnungen im Betrieb | Überwachungsbericht, Grundlage für Zertifikat/Kennzeichnung |

Daraus folgt unmittelbar die wichtigste **Zielsetzung** für dein System: Die WPK erzeugt kontinuierlich Nachweise, die **später gegenüber Dritten belegbar** sein müssen. Das ist der entscheidende Unterschied zu einer beliebigen betrieblichen App — und die Quelle fast aller harten nicht-funktionalen Anforderungen (Vollständigkeit, Unveränderbarkeit, Nachvollziehbarkeit, Aufbewahrung).

### 8.2 Kandidaten für dein Anforderungsmodell: die Kernprozesse

Diese Liste ist dein **Suchraster für die Interviews** und zugleich die Gliederung deines Anforderungskatalogs. Geh sie im Betrieb durch und kläre für jeden Punkt: Gibt es das? Wie läuft es? Wo klemmt es?

| # | Prozessbereich | Typische Inhalte | Digitalisierungspotenzial |
|---|---|---|---|
| 1 | **Wareneingangskontrolle** | Holz (Festigkeits-/Sortierklasse, Kennzeichnung, Holzfeuchte bei Anlieferung), Holzwerkstoffplatten, Dämmstoffe, Folien, Verbindungsmittel; Lieferschein, Leistungserklärung, CE-/Ü-Kennzeichnung, Zertifikate | hoch — Chargenerfassung, Dokumentenablage, Prüfnachweis |
| 2 | **Materialverwaltung / Chargen** | Zuordnung von Lieferchargen zu Fertigungsaufträgen | hoch — Grundlage der Rückverfolgbarkeit |
| 3 | **Prüfplanung** | Welches Merkmal wird womit, wie oft, gegen welche Toleranz geprüft | hoch — digitale Prüfpläne statt Papiertabellen |
| 4 | **Fertigungsbegleitende Prüfung am Element** | Maßhaltigkeit (Länge, Höhe, Diagonalen/Rechtwinkligkeit, Ebenheit), Rippen-/Ständerabstände, Beplankung (Material, Dicke, Plattenstöße), Verbindungsmittel (Typ, Abstände, Randabstände, Eindringtiefe, Klammerbild), Öffnungen und Einbauteile, Luftdichtheitsebene und Anschlüsse | **sehr hoch** — Kern der mobilen Erfassung |
| 5 | **Holzfeuchtemessung** | Messstellen, Messgerät, Grenzwert, Zeitpunkt | hoch — Messwerte, automatische Bewertung |
| 6 | **Bewertung / Freigabe** | Vergleich gegen Toleranz, Freigabe zum nächsten Arbeitsschritt bzw. zur Auslieferung, Vier-Augen-Prinzip | hoch — Regelwerk, Sperrlogik |
| 7 | **Abweichungsmanagement** | Nichtkonformität erfassen, Element sperren, Ursache, Korrekturmaßnahme, Sonderfreigabe, Wirksamkeitskontrolle | **sehr hoch** — heute oft der schwächste Punkt |
| 8 | **Prüfmittelüberwachung** | Bestand, Kalibrier-/Prüffristen, Kalibrierscheine, Sperrung abgelaufener Mittel | hoch — Fristenüberwachung, Erinnerung |
| 9 | **Rückverfolgbarkeit** | Element ↔ Auftrag ↔ Materialchargen ↔ Prüfungen ↔ Personal ↔ Bauvorhaben | **sehr hoch** — zentraler Nutzen |
| 10 | **Kennzeichnung** | Element-Identifikation, Herstellerangaben, Herstelldatum, ggf. Ü-Zeichen/Kennzeichnung nach Norm | mittel — Etikettendruck, ID-Vergabe |
| 11 | **Personal und Qualifikation** | Verantwortlichkeiten, Schulungsnachweise, Berechtigung zur Prüfung/Freigabe | mittel — Rollen- und Berechtigungskonzept |
| 12 | **Dokumentenlenkung** | Gültige Fassungen von Prüfplänen, Zeichnungen, Arbeitsanweisungen; Freigabe; Änderungsverfolgung | hoch — Versionierung, gültige Fassung erzwingen |
| 13 | **Nachweisführung / Fremdüberwachung** | Zusammenstellung aller Nachweise eines Zeitraums, Auditvorbereitung, Überwachungsberichte, Maßnahmenverfolgung | **sehr hoch** — größter spürbarer Zeitgewinn |
| 14 | **Archivierung** | Aufbewahrungsfristen, revisionssichere Ablage, Auffindbarkeit | hoch |
| 15 | **Auswertung / Kennzahlen** | Fehlerquoten, Abweichungen nach Ursache, Prüfabdeckung | mittel — für die Geschäftsführung oft das Kaufargument |

Die Bereiche mit „sehr hoch" sind deine wahrscheinlichen Schwerpunkte. Für eine Bachelorarbeit ist es völlig legitim — und empfehlenswert —, den Scope auf einige dieser Bereiche zu begrenzen und die übrigen explizit auszuschließen. **Lieber vier Bereiche in guter Tiefe als fünfzehn oberflächlich.**

### 8.3 Stakeholder-Map (Beispiel)

| ID | Stakeholder | Rolle im System | Kerninteresse | Einfluss |
|---|---|---|---|---|
| S-01 | Prüfer / Werker | Hauptnutzer, erfasst Prüfungen | schnelle, störungsfreie Erfassung im Fertigungstakt | mittel |
| S-02 | Fertigungs-/Produktionsleiter | Nutzer, steuert Ablauf | Transparenz über offene Prüfungen und gesperrte Elemente | hoch |
| S-03 | WPK-/Qualitätsbeauftragter | Hauptnutzer, verantwortet Nachweise | Vollständigkeit, Normkonformität, Auditsicherheit | **sehr hoch** |
| S-04 | Geschäftsführung | Entscheider | Wirtschaftlichkeit, Haftungsminimierung | hoch |
| S-05 | Fremdüberwachungsstelle | externer Prüfer der Nachweise | Nachvollziehbarkeit, Unveränderbarkeit, Stichprobenfähigkeit | hoch (indirekt) |
| S-06 | IT-Verantwortlicher / Dienstleister | Betrieb, Schnittstellen | Betreibbarkeit, Datensicherheit | mittel |
| S-07 | Arbeitsvorbereitung / Konstruktion | liefert Auftrags- und Elementdaten | keine Doppelerfassung | mittel |
| S-08 | Bauherr / Auftraggeber | Empfänger der Nachweise | Nachweis der Qualität | niedrig |

Die Fremdüberwachungsstelle ist der interessanteste Stakeholder: Sie nutzt das System **nicht**, bestimmt aber über die Nachweisanforderungen maßgeblich mit, was es können muss. Ein Interview dort ist besonders wertvoll — und in der Arbeit ein Pluspunkt, weil es über die Betriebsperspektive hinausgeht.

### 8.4 Kontextdiagramm (Skizze)

```
        Arbeitsvorbereitung            Fremdüberwachungs-
         / ERP-System                       stelle
              │  Auftrags- und                  ▲  Nachweise,
              │  Elementdaten                   │  Berichte
              ▼                                 │
    ┌─────────────────────────────────────────────────────┐
    │                                                     │
    │              WPK-SYSTEM (Systemgrenze)              │
    │                                                     │
    │   Prüfplanung · Prüfdurchführung · Bewertung ·      │
    │   Abweichungen · Rückverfolgbarkeit · Nachweise     │
    │                                                     │
    └─────────────────────────────────────────────────────┘
        ▲              ▲               ▲              ▲
        │ Messwerte,   │ Freigaben,    │ Prüfpläne,   │ Messwerte
        │ Prüfungen    │ Steuerung     │ Auswertung   │ (ggf. digital)
        │              │               │              │
     Prüfer      Fertigungs-      WPK-/Qualitäts-   Prüfmittel
                   leitung         beauftragter    (Messgeräte)

    Nicht im Scope: Lohnabrechnung, Vertrieb, statische Bemessung,
                    Materialdisposition, Transportlogistik
```

Zeichne das sauber in draw.io oder Visio nach — es gehört an den Anfang deines Ergebniskapitels.

### 8.5 Beispielanforderungen

20 formulierte Anforderungen als Muster. Sie zeigen die Satzschablone in Anwendung und decken alle drei Typen ab. **Nicht abschreiben, sondern als Formulierungsvorlage nutzen** — deine eigenen müssen aus deiner Erhebung stammen.

#### Funktionale Anforderungen

| ID | Anforderung | Quelle (Beispiel) | Prio |
|---|---|---|---|
| FA-001 | Das System **MUSS** dem Prüfer die Möglichkeit bieten, ein Element anhand seiner eindeutigen Elementnummer zu identifizieren. | I-01, SW-02 | Must |
| FA-002 | Das System **MUSS** zu jedem Element den zugehörigen Fertigungsauftrag, das Bauvorhaben und den Elementtyp speichern. | I-03, N-02 | Must |
| FA-003 | Das System **MUSS** dem WPK-Beauftragten die Möglichkeit bieten, je Elementtyp einen Prüfplan mit Prüfmerkmalen, Prüfmitteln, Prüffrequenzen und Toleranzbereichen anzulegen und zu ändern. | I-02, SW-05 | Must |
| FA-004 | Das System **MUSS** bei der Prüfung eines Elements die im gültigen Prüfplan festgelegten Prüfmerkmale anzeigen. | I-02 | Must |
| FA-005 | Das System **MUSS** dem Prüfer die Möglichkeit bieten, zu jedem Prüfmerkmal einen Messwert einschließlich Einheit, Messstelle und Prüfmittel zu erfassen. | I-01, N-01 | Must |
| FA-006 | Das System **MUSS** einen erfassten Messwert automatisch gegen den im Prüfplan hinterlegten Toleranzbereich bewerten und das Ergebnis als „in Ordnung" oder „nicht in Ordnung" kennzeichnen. | SW-07 | Must |
| FA-007 | Wenn ein Messwert außerhalb des zulässigen Toleranzbereichs liegt, **MUSS** das System eine Abweichungsmeldung mit Bezug zu Element, Prüfmerkmal und Messwert erzeugen. | SW-07, I-02 | Must |
| FA-008 | Solange zu einem Element eine offene Abweichung besteht, **MUSS** das System die Freigabe dieses Elements zur Auslieferung verhindern. | I-02, I-03 | Must |
| FA-009 | Das System **MUSS** dem WPK-Beauftragten die Möglichkeit bieten, zu einer Abweichung Ursache, Korrekturmaßnahme, verantwortliche Person und Erledigungsdatum zu erfassen. | I-02, N-04 | Must |
| FA-010 | Das System **MUSS** zu jeder Prüfaufzeichnung den Zeitpunkt der Erfassung und die erfassende Person speichern. | N-01 | Must |
| FA-011 | Das System **MUSS** dem Prüfer die Möglichkeit bieten, einer Prüfaufzeichnung Fotos als Nachweis beizufügen. | I-01 | Should |
| FA-012 | Das System **MUSS** zu jedem Element die eingesetzten Materialchargen unter Angabe von Material, Lieferant, Lieferschein- oder Chargennummer speichern. | N-02, I-03 | Must |
| FA-013 | Das System **MUSS** dem WPK-Beauftragten die Möglichkeit bieten, zu einem Element alle zugehörigen Prüfaufzeichnungen, Materialchargen, Abweichungen und Freigaben in einer Übersicht anzuzeigen. | I-02, SW-01 | Must |
| FA-014 | Das System **MUSS** dem WPK-Beauftragten die Möglichkeit bieten, alle Prüfaufzeichnungen eines wählbaren Zeitraums als vollständiges, druckbares Nachweisdokument zu exportieren. | I-02, SW-01 | Must |
| FA-015 | Das System **MUSS** den Bestand der Prüfmittel mit Kalibrier- bzw. Prüffrist verwalten. | N-03, I-02 | Should |
| FA-016 | Wenn die Kalibrierfrist eines Prüfmittels abgelaufen ist, **MUSS** das System die Auswahl dieses Prüfmittels bei der Prüferfassung verhindern. | N-03 | Should |
| FA-017 | Das System **MUSS fähig sein**, Auftrags- und Elementstammdaten aus dem vorhandenen ERP-/Konstruktionssystem zu übernehmen. | I-06, SW-03 | Should |
| FA-018 | Das System **MUSS** der Fertigungsleitung die Möglichkeit bieten, alle Elemente mit offenen oder überfälligen Prüfungen anzuzeigen. | I-03 | Should |

#### Nicht-funktionale Anforderungen

| ID | Anforderung | Merkmal (ISO 25010) | Prio |
|---|---|---|---|
| NFA-001 | Das System **MUSS** eine Prüfaufzeichnung nach ihrer Freigabe gegen Veränderung schützen; nachträgliche Korrekturen **MÜSSEN** als neue Version mit Begründung, Zeitpunkt und Person gespeichert werden, wobei die ursprüngliche Fassung erhalten bleibt. | Security (Integrität, Nachweisbarkeit) | Must |
| NFA-002 | Das System **MUSS** Prüfaufzeichnungen über die geltende Aufbewahrungsfrist von mindestens *X* Jahren verfügbar halten. *(Fristdauer aus DIN 1052-11 bzw. betrieblicher Vorgabe zu konkretisieren.)* | Reliability / Security | Must |
| NFA-003 | Das System **MUSS** die Erfassung einer Standard-Elementprüfung durch einen eingewiesenen Prüfer in höchstens 90 Sekunden ermöglichen. | Interaction Capability | Must |
| NFA-004 | Das System **MUSS** mit Arbeitshandschuhen bedienbar sein; alle Bedienelemente der Prüferfassung **MÜSSEN** eine Mindestgröße von 10 × 10 mm aufweisen. | Interaction Capability | Should |
| NFA-005 | Das System **MUSS** die Erfassung von Prüfungen auch ohne Netzwerkverbindung ermöglichen und erfasste Daten bei erneuter Verbindung automatisch übertragen. | Reliability / Flexibility | Must |
| NFA-006 | Das System **MUSS** die Suche nach den Prüfaufzeichnungen eines Elements in höchstens 3 Sekunden beantworten, bei bis zu 50.000 gespeicherten Aufzeichnungen. | Performance Efficiency | Should |
| NFA-007 | Das System **MUSS** sicherstellen, dass die Freigabe eines Elements nur durch Personen erfolgen kann, denen die Rolle „Freigabeberechtigter" zugewiesen ist. | Security (Zugriffsschutz) | Must |

#### Randbedingungen

| ID | Randbedingung | Art |
|---|---|---|
| RB-001 | Die Lösung **MUSS** die Anforderungen an Aufzeichnung und Nachweisführung der Eigenüberwachung nach DIN 1052-11 in der geltenden Fassung erfüllen. | normativ |
| RB-002 | Die Verarbeitung personenbezogener Daten (Prüferkennung, Freigaben) **MUSS** den Anforderungen der DSGVO entsprechen; eine Leistungs- oder Verhaltenskontrolle der Mitarbeiter ist ausgeschlossen. | rechtlich |
| RB-003 | In den Fertigungsbereichen steht keine flächendeckende WLAN-Abdeckung zur Verfügung. | technisch |
| RB-004 | Die Lösung **MUSS** ohne eigene IT-Abteilung durch eine geschulte Person im Betrieb administrierbar sein. | organisatorisch |
| RB-005 | Die bestehenden Fertigungsabläufe dürfen durch die Einführung nicht unterbrochen werden; ein Parallelbetrieb mit den bisherigen Papieraufzeichnungen **MUSS** für eine Übergangszeit möglich sein. | organisatorisch |

Achte auf das Muster: Jede NFA hat eine Messgröße oder ein prüfbares Kriterium. NFA-002 zeigt außerdem, wie man mit offenen Punkten korrekt umgeht — **Platzhalter mit Klärungsvermerk** statt einer erfundenen Zahl. So etwas in der Arbeit stehen zu lassen ist kein Mangel, sondern Redlichkeit, solange du es als offenen Punkt kennzeichnest.

### 8.6 Beispiel-Use-Case (ausformuliert)

| Feld | Inhalt |
|---|---|
| **ID / Name** | UC-04 — Elementprüfung durchführen |
| **Ziel** | Der Prüfer dokumentiert die fertigungsbegleitende Prüfung eines Elements vollständig und normkonform. |
| **Primärer Akteur** | Prüfer (S-01) |
| **Weitere Beteiligte** | WPK-Beauftragter (S-03), Fertigungsleitung (S-02) |
| **Auslöser** | Ein Element hat einen Fertigungsschritt erreicht, für den der Prüfplan eine Prüfung vorsieht. |
| **Vorbedingungen** | Element ist im System angelegt; ein gültiger Prüfplan für den Elementtyp liegt vor; der Prüfer ist angemeldet und berechtigt. |
| **Nachbedingung (Erfolg)** | Eine vollständige, bewertete Prüfaufzeichnung ist gespeichert und dem Element zugeordnet. |
| **Nachbedingung (Misserfolg)** | Keine unvollständige Aufzeichnung wird als abgeschlossen gespeichert. |
| **Standardablauf** | 1. Prüfer identifiziert das Element.<br>2. System zeigt Element, Auftrag und die fälligen Prüfmerkmale des gültigen Prüfplans.<br>3. Prüfer wählt das verwendete Prüfmittel.<br>4. Prüfer erfasst je Merkmal den Messwert.<br>5. System bewertet jeden Wert gegen den Toleranzbereich.<br>6. Prüfer schließt die Prüfung ab.<br>7. System speichert die Aufzeichnung mit Zeitpunkt und Prüferkennung und setzt den Prüfstatus des Elements. |
| **Alternativabläufe** | 3a. Kein Prüfmittel erforderlich (Sichtprüfung) → System überspringt Schritt 3.<br>4a. Prüfer erfasst zu einem Merkmal mehrere Messstellen → System speichert alle Werte und wertet den ungünstigsten. |
| **Ausnahmeabläufe** | 5a. Messwert außerhalb der Toleranz → System erzeugt eine Abweichung (FA-007), sperrt die Freigabe (FA-008) und informiert den WPK-Beauftragten.<br>2a. Kein gültiger Prüfplan vorhanden → System verweigert die Prüfung und weist auf den fehlenden Prüfplan hin.<br>3b. Kalibrierfrist des gewählten Prüfmittels abgelaufen → System lässt die Auswahl nicht zu (FA-016).<br>6a. Prüfer bricht ab → System speichert den Zwischenstand als „in Bearbeitung", nicht als abgeschlossene Aufzeichnung.<br>\*. Keine Netzverbindung → System erfasst lokal und überträgt später (NFA-005). |
| **Beteiligte Anforderungen** | FA-001, FA-004, FA-005, FA-006, FA-007, FA-008, FA-010, FA-016, NFA-003, NFA-005 |

Beachte, wie viele Anforderungen erst durch die **Ausnahmeabläufe** sichtbar werden. Genau deshalb lohnt sich der Aufwand.

### 8.7 Besonderheiten, die du nicht übersehen solltest

**Nachweischarakter der Daten.** Deine Aufzeichnungen sind keine Betriebsdaten, sondern Belege gegenüber einer Überwachungsstelle und potenziell in einem Haftungsfall. Daraus folgen: Unveränderbarkeit nach Freigabe, Versionierung statt Überschreiben, lückenlose Zuordnung zu Person und Zeit, Vollständigkeitsprüfung und definierte Aufbewahrung. Das ist das wichtigste Thema deiner nicht-funktionalen Anforderungen.

**Erfassung im Takt.** Der Prüfer steht an der Fertigungsstraße. Jede Sekunde Bedienzeit konkurriert mit der Taktzeit. Wenn die digitale Erfassung langsamer ist als der Zettel, wird sie umgangen — dann ist die Lösung nicht nur nutzlos, sondern erzeugt Nachweislücken. Erhebe die realen Taktzeiten und leite daraus eine harte Zeitanforderung ab.

**Physische Umgebung.** Staub, Holzspäne, Feuchtigkeit, Lärm, wechselndes Licht, Handschuhe, Leitern, Gerüste. Das erzeugt Anforderungen an Geräteklasse, Bedienelementgröße, Kontrast, Ein-Hand-Bedienung und akustische Rückmeldung.

**Offline-Fähigkeit.** Holzbauhallen sind funktechnisch oft schwierig. Offline-Erfassung mit späterer Synchronisation ist fast immer eine Muss-Anforderung — und sie hat erhebliche Folgen für das Datenmodell (Konfliktbehandlung, eindeutige IDs ohne Server).

**Übergang und Koexistenz.** Ein Betrieb kann seine WPK nicht an einem Montag umstellen. Anforderungen an Parallelbetrieb, Migration der Altdaten und schrittweise Einführung sind real und werden in Arbeiten gern vergessen.

**Mehrsprachigkeit.** In der Produktion arbeiten häufig Beschäftigte mit unterschiedlichen Muttersprachen. Symbolgestützte Bedienung und ggf. mehrsprachige Oberfläche können echte Anforderungen sein — frag danach.

**Der Fremdüberwacher als Nutzer.** Überlege, ob die Überwachungsstelle einen eigenen, lesenden Zugang bekommen soll. Das ist eine spannende, in der Arbeit gut diskutierbare Gestaltungsfrage mit Anforderungen zu Zugriffsschutz, Datensparsamkeit und Nachweisumfang.

---

## 9. Aufbau im Thesis-Dokument

Ein bewährter Kapitelaufbau für eine Bachelorarbeit mit Anforderungsmodell als Ergebnis:

| Kapitel | Inhalt | Umfang (ca.) |
|---|---|---|
| 1 Einleitung | Problemstellung, Zielsetzung, Forschungsfrage, Aufbau der Arbeit | 4–6 S. |
| 2 Grundlagen | 2.1 WPK und normativer Rahmen (DIN 1052-11, MVV TB, Eigen-/Fremdüberwachung)<br>2.2 Requirements Engineering (Begriffe, Anforderungsarten, Vorgehen)<br>2.3 Stand der Technik / verfügbare Lösungen | 12–18 S. |
| 3 Methodisches Vorgehen | Forschungsdesign, Auswahl und Begründung der Erhebungsmethoden, Interviewdesign, Auswertungsverfahren, Gütekriterien | 8–12 S. |
| 4 Ist-Analyse | Betriebskontext, Ist-Prozess (BPMN), Dokumentenanalyse, Schwachstellenkatalog | 10–15 S. |
| 5 Ergebnisse der Erhebung | Auswertung der Interviews, Kategorien, zentrale Erkenntnisse, Ableitung der Ziele | 8–12 S. |
| 6 Anforderungsmodell | Kontext, Stakeholder, Soll-Prozess, Use-Cases, Anforderungskatalog, Priorisierung | 15–25 S. |
| 7 Validierung | Vorgehen, Rückmeldungen, vorgenommene Änderungen | 4–6 S. |
| 8 Diskussion und Fazit | Beantwortung der Forschungsfrage, Limitationen, Ausblick auf die Umsetzung | 5–8 S. |
| Anhang | Interviewleitfaden, Einwilligungserklärung, Transkripte/Auswertungstabellen, vollständiger Anforderungskatalog, Glossar, Formblätter | — |

Drei Empfehlungen dazu:

**Der vollständige Anforderungskatalog gehört in den Anhang**, im Hauptteil stehen die Struktur, die Herleitung, die Kategorien und eine repräsentative Auswahl. 80 Anforderungen als Tabelle im Fließtext erschlägt jeden Leser.

**Die Herleitungslogik ist wichtiger als die Anzahl.** Eine Arbeit mit 45 sauber hergeleiteten, validierten und priorisierten Anforderungen ist deutlich besser als eine mit 150 zusammengetragenen. Zeige die Kette Interview → Aussage → Schwachstelle → Anforderung an mehreren Beispielen ausführlich.

**Benenne Limitationen offensiv.** Ein Betrieb statt mehrerer, fünf Interviews statt zwanzig, keine prototypische Umsetzung, Norm nur in einer Ausgabe berücksichtigt — das alles ist für eine Bachelorarbeit völlig in Ordnung, *wenn du es benennst und einordnest*. Verschwiegene Limitationen kosten in der Verteidigung mehr Punkte als offen genannte.

---

## 10. Typische Fehler in Bachelorarbeiten

| Fehler | Warum problematisch | Gegenmittel |
|---|---|---|
| Anforderungen ohne Quelle | Nicht nachvollziehbar, wirkt erfunden | Quellenspalte konsequent führen |
| Lösungen statt Anforderungen | Schränkt den Lösungsraum unbegründet ein | „Warum?" fragen, bis das Bedürfnis dasteht |
| Nicht-funktionale Anforderungen ohne Messgröße | Nicht prüfbar → wertlos | Messgröße + Zielwert erzwingen |
| Scope nie abgegrenzt | Arbeit franst aus, Vollständigkeit unbewertbar | Kontextdiagramm + „Nicht Gegenstand"-Absatz |
| Keine Validierung | Ergebnis bleibt unbestätigte Behauptung | Walkthrough-Termin fest einplanen |
| Methodenkapitel als Lehrbuchreferat | Keine eigene Leistung erkennbar | Jede Methodenwahl **begründen**, Alternativen abwägen |
| Ist-Prozess aus dem Handbuch statt aus der Realität | Falsche Basis, Schwachstellen bleiben unsichtbar | Beobachten, nicht nur lesen |
| Glossar fehlt | Begriffe driften durch die Arbeit | Ab Interview 1 pflegen |
| Priorisierung vom Autor allein | Fachliche Entscheidung ohne fachliche Legitimation | Stakeholder priorisieren lassen |
| Keine Ausnahmefälle betrachtet | 20–30 % der Anforderungen fehlen | Use-Cases mit Ausnahmeabläufen schreiben |
| Zu viele Anforderungen, zu wenig Tiefe | Oberflächlichkeit sichtbar | Scope bewusst reduzieren und das begründen |
| Normtexte ausführlich wörtlich zitiert | Urheberrechtlich heikel | Sinngemäß wiedergeben, Abschnitt zitieren |

---

## 11. Werkzeuge

Für den Umfang einer Bachelorarbeit brauchst du **kein** RE-Werkzeug. Diese Kombination reicht vollständig aus und funktioniert gut:

| Zweck | Empfehlung | Alternativen |
|---|---|---|
| Anforderungskatalog | Excel / LibreOffice Calc / Google Sheets mit festen Spalten | Notion, Airtable, Jira |
| Prozessmodelle (BPMN) | [Camunda Modeler](https://camunda.com/download/modeler/) (kostenlos, BPMN-konform) | draw.io, bpmn.io, Signavio Academic |
| Diagramme (Kontext, Use-Case) | [draw.io / diagrams.net](https://www.drawio.com/) (kostenlos) | Visio, Lucidchart, PlantUML |
| UML | PlantUML (textbasiert, gut versionierbar), Visual Paradigm Community | StarUML |
| Interviewtranskription | Automatische Transkription mit manueller Nachkorrektur | f4transkript, manuelle Transkription |
| Qualitative Auswertung | Excel-Tabelle mit Spalten für Code/Kategorie/Paraphrase | MAXQDA, ATLAS.ti (oft über die Hochschule verfügbar) |
| Literaturverwaltung | Zotero (kostenlos) | Citavi, EndNote |

Ein Hinweis zu Excel: Nimm **eine** Datei mit mehreren Blättern (Anforderungen, Interviewaussagen, Schwachstellen, Normstellen, Glossar, Stakeholder) und verlinke über die IDs. Das ist dein Anforderungsmodell in Arbeitsform; für die Arbeit exportierst du daraus die Tabellen.

---

## 12. Literatur und Quellen

Prüfe Auflage und Jahr vor dem Zitieren — die Angaben hier sind Orientierung, keine geprüften bibliografischen Daten.

**Requirements Engineering — Einstieg (fang hier an)**

- **Pohl, K.; Rupp, C.: *Basiswissen Requirements Engineering.*** dpunkt.verlag. — Das offizielle Lehrbuch zur IREB-Zertifizierung, rund 180 Seiten, kompakt und präzise. **Wenn du nur ein Buch liest, dann dieses.**
- **IREB e.V.: *CPRE Foundation Level Handbook* / Glossar.** Über [ireb.org](https://www.ireb.org) kostenlos verfügbar. Das Glossar ist für saubere Definitionen in der Arbeit sehr nützlich.

**Requirements Engineering — Vertiefung**

- **Rupp, C. und die SOPHISTen: *Requirements-Engineering und -Management.*** Hanser. — Die Quelle für die Satzschablone (MASTeR) und die sprachlichen Qualitätskriterien. Für Kapitel 6 und 7 deiner Arbeit die zentrale Referenz.
- **Pohl, K.: *Requirements Engineering — Grundlagen, Prinzipien, Techniken.*** dpunkt.verlag. — Das umfassende Standardwerk, gut für theoretische Fundierung (Drei-Dimensionen-Modell, Kontextabgrenzung).
- **Ebert, C.: *Systematisches Requirements Engineering.*** dpunkt.verlag. — Praxisnah, viele Vorlagen.
- **Balzert, H.: *Lehrbuch der Softwaretechnik — Basiskonzepte und Requirements Engineering.*** Springer Spektrum. — Klassiker, im deutschen Hochschulkontext viel zitiert.
- **Robertson, S.; Robertson, J.: *Mastering the Requirements Process.*** Addison-Wesley. — Quelle der Volere-Schablone, gute Checklisten.
- **Cockburn, A.: *Writing Effective Use Cases.*** Addison-Wesley. — Wenn du Use-Cases ernsthaft schreiben willst.

**Normen und Standards (Methodik)**

- **ISO/IEC/IEEE 29148:2018** — *Systems and software engineering — Life cycle processes — Requirements engineering.* Der internationale Standard; enthält die Qualitätskriterien für Anforderungen und eine Spezifikationsstruktur. Über die Hochschulbibliothek meist zugänglich.
- **ISO/IEC 25010:2023** — *Systems and software Quality Requirements and Evaluation (SQuaRE) — Product quality model.* Die Referenz für nicht-funktionale Anforderungen.
- **ISO/IEC 19510:2013** — BPMN 2.0 als ISO-Standard.

**Normen und Regelwerke (Fachdomäne)**

- **DIN 1052-11:2026-03** — *Holzbauwerke — Herstellung und Ausführung von Holzbauwerken — Teil 11: Vorgefertigte Wand-, Decken- und Dachelemente und Raummodule — Anforderungen an die Herstellung.* Ersetzt DIN 1052-11:2022-12. **Deine zentrale Fachquelle — unbedingt im Volltext beschaffen** (Hochschulbibliothek, DIN-Normenportal, ZDB-Normenportal für Mitgliedsbetriebe).
- **DIN 1052-10:2024-12** — Ergänzende Bestimmungen zur Herstellung und Ausführung von Holzbauwerken.
- **DIN 18200:2021-04** — *Übereinstimmungsnachweis für Bauprodukte — Werkseigene Produktionskontrolle, Fremdüberwachung und Zertifizierung.*
- **MVV TB** (Muster-Verwaltungsvorschrift Technische Baubestimmungen) in der aktuellen Fassung, insbesondere Teil C — über das DIBt verfügbar; dort ist die bauaufsichtliche Einführung geregelt.
- Verbandsveröffentlichungen von **Holzbau Deutschland** / Bund Deutscher Zimmermeister (u. a. ein Merkblatt zu DIN 1052-11 für vorgefertigte Holztafelelemente) — praxisnahe Erläuterungen, gute Ergänzung zur Norm.

**Empirische Methodik (für dein Methodenkapitel)**

- **Mayring, P.: *Qualitative Inhaltsanalyse — Grundlagen und Techniken.*** Beltz. — Die Standardreferenz für die Auswertung deiner Interviews.
- **Gläser, J.; Laudel, G.: *Experteninterviews und qualitative Inhaltsanalyse.*** Springer VS. — Speziell auf Experteninterviews zugeschnitten, sehr praxisnah. **Für dich besonders passend.**
- **Meuser, M.; Nagel, U.: *Das Experteninterview — konzeptionelle Grundlagen und methodische Anlage.*** — Der klassische Aufsatz zur Begründung, warum Experteninterviews ein eigenständiges Verfahren sind.
- **Kuckartz, U.: *Qualitative Inhaltsanalyse — Methoden, Praxis, Computerunterstützung.*** Beltz Juventa.

**Prozessmodellierung**

- **Freund, J.; Rücker, B.: *Praxishandbuch BPMN.*** Hanser. — Der deutschsprachige Standard, pragmatisch und gut lesbar.
- **Allweyer, T.: *BPMN 2.0 — Business Process Model and Notation.*** — Kompakte Einführung.

---

## Anhang: Checkliste „Bin ich fertig?"

Geh diese Liste durch, bevor du das Anforderungskapitel abgibst.

**Abgrenzung und Kontext**
- [ ] Systemgrenze ist definiert und grafisch dargestellt
- [ ] Explizite Aussage, was *nicht* Gegenstand ist
- [ ] Alle Akteure und Nachbarsysteme benannt

**Stakeholder und Ziele**
- [ ] Stakeholder-Map mit Rollen, Interessen und Einfluss
- [ ] Ziele formuliert, Anforderungen lassen sich auf Ziele zurückführen

**Erhebung**
- [ ] Methodenwahl begründet, nicht nur beschrieben
- [ ] Interviewleitfaden im Anhang
- [ ] Einwilligungen eingeholt und dokumentiert
- [ ] Auswertung nachvollziehbar (Kategorien, Ableitungstabelle)
- [ ] Mindestens zwei unabhängige Quellenarten genutzt (Triangulation)

**Anforderungen**
- [ ] Jede Anforderung hat ID, Typ, Quelle und Priorität
- [ ] Alle Anforderungen nach einheitlicher Satzschablone formuliert
- [ ] Verbindlichkeitsstufen (MUSS/SOLLTE/WIRD) konsequent verwendet
- [ ] Funktional, nicht-funktional und Randbedingungen sauber getrennt
- [ ] Jede nicht-funktionale Anforderung hat eine Messgröße
- [ ] Keine Anforderung enthält eine Lösungsvorgabe
- [ ] Keine Anforderung enthält mehrere Anforderungen („und")
- [ ] Sprachliche Prüfliste angewendet (Passiv, Nominalisierung, Weichmacher)
- [ ] Must-have-Anforderungen haben Akzeptanzkriterien

**Modell**
- [ ] Ist- und Soll-Prozess modelliert, Schwachstellen dokumentiert
- [ ] Use-Cases für die zentralen Abläufe, mit Ausnahmeabläufen
- [ ] Glossar vollständig, Begriffe in den Anforderungen konsistent verwendet
- [ ] Traceability nachvollziehbar (Quelle ↔ Anforderung ↔ Use-Case)

**Validierung**
- [ ] Katalog mit mindestens einem Experten durchgesprochen
- [ ] Rückmeldungen und Änderungen dokumentiert
- [ ] Priorisierung durch Stakeholder, nicht nur durch dich

**Arbeit insgesamt**
- [ ] Limitationen benannt
- [ ] Ausblick auf Umsetzung/nächste Schritte
- [ ] Normen mit Ausgabestand zitiert, keine langen wörtlichen Normzitate

---

*Erstellt als Arbeitsgrundlage für eine Bachelorarbeit zur Digitalisierung der werkseigenen Produktionskontrolle im Holztafelbau. Fachliche Aussagen zu DIN 1052-11 sind an der Originalnorm zu verifizieren.*
