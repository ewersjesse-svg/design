# Kompakt-Fahrplan für die letzten 4½ Wochen

> Der ausführliche Leitfaden bleibt als Nachschlagewerk. **Dieser Fahrplan ist das, was du tatsächlich abarbeitest.** Er ist auf deine Situation zugeschnitten: 4½ Wochen Restzeit, ca. 20 von maximal 50 Seiten geschrieben, Norm und Soll-Prozess fertig, Interviews noch offen.

## Ausgangslage in Zahlen

| | |
|---|---|
| Restzeit | ca. 4½ Wochen ≈ 22 Arbeitstage |
| Geschrieben | ca. 20 Seiten (Einleitung, Recherche) |
| Zielumfang | 30–50 Seiten → **realistisch 40–45 Seiten gesamt, also 20–25 neue Seiten** |
| Erledigt | DIN 1052-11 durchgearbeitet, Soll-Prozess nach DIN modelliert |
| Offen | Interviews (Termin unklar), Ist-Situation, Anforderungskatalog, Use-Cases, Priorisierung, Validierung, Fazit |

## Die wichtigste Entscheidung: zwei Schichten statt einer

Dein Anforderungsmodell entsteht in **zwei Schichten**, und die erste kannst du komplett ohne Interviews bauen:

| Schicht | Quelle | Wann | Liefert |
|---|---|---|---|
| **1 — normativ-deduktiv** | DIN 1052-11 + dein Soll-Prozess | **jetzt** | 60–70 % des Katalogs: alle normativ zwingenden Anforderungen, Systemabgrenzung, Akteure, Use-Cases |
| **2 — empirisch** | Experteninterviews | sobald Termine stehen | Ist-Situation und Schwachstellen, Ergänzungen, Zielwerte für NFA, Priorisierung, Validierung |

In der Methodik heißt das: **„normativ-deduktive Ableitung der Anforderungen mit empirischer Ergänzung, Priorisierung und Validierung durch Experteninterviews."** Das ist ein sauberes, verteidigbares Design — und es entkoppelt dich vom Interviewtermin. Wenn die Interviews spät kommen, steht der Katalog trotzdem; sie machen ihn dann besser statt ihn erst zu ermöglichen.

## Reduziertes Anforderungsmodell: was bleibt, was fliegt

**Behalten (das ist dein Ergebniskapitel):**

| Artefakt | Umfang | Woher |
|---|---|---|
| Kontextdiagramm + Abgrenzungsabsatz | 1 Abbildung, ½ Seite | aus dem Soll-Prozess ableitbar |
| Stakeholder-Tabelle | ½ Seite | Rollen aus Soll-Prozess und Norm |
| Soll-Prozess | hast du — ggf. Lane „WPK-System" ergänzen, damit sichtbar wird, wo das System eingreift | fertig |
| Use-Case-Diagramm + 3–4 Kurzbeschreibungen | 1 Abbildung + 1 Seite | aus Soll-Prozess |
| **Anforderungskatalog** | 30–50 Anforderungen (FA / NFA / RB) mit ID, Quelle, Priorität; Auszug im Hauptteil, komplett im Anhang | Schicht 1 + 2 |
| Ist-Situation + Schwachstellentabelle | 2–3 Seiten Text + 1 Tabelle | Interviews |
| Glossar | Anhang | laufend |

**Streichen — bewusst, und in einem Satz im Ausblick erwähnen:**

- Zielhierarchie als eigenes Modell (2–3 Ziele im Fließtext reichen)
- Datenmodell / ERD
- Ausführliche Use-Case-Beschreibungen mit allen Ausnahmeabläufen (höchstens **einer** als Beispiel)
- Ist-Prozess als vollständiges BPMN (Text + Schwachstellentabelle genügt; wenn Zeit bleibt, ein reduziertes Diagramm)
- Kano, Aufwand-Nutzen-Matrix — nur MoSCoW
- Vollständige sprachliche Qualitätsprüfung — Kurzcheck (Passiv, „und", Weichmacher) reicht

## Was du jetzt machen kannst — in dieser Reihenfolge

| # | Aufgabe | Aufwand | Ergebnis |
|---|---|---|---|
| 1 | **Katalogdatei anlegen** (Excel, Spalten aus `vorlagen/anforderungsliste.csv`), ID-Schema festlegen (FA/NFA/RB, N-xx für Normstellen, SP-xx für Soll-Prozessschritte, I-xx für Interviews) | ½ Tag | Arbeitsstruktur |
| 2 | **Systemabgrenzung + Kontextdiagramm** aus dem Soll-Prozess: Was ist System, was Akteur, was Nachbarsystem, was raus? | ½ Tag | 1 Abbildung + Absatz |
| 3 | **Normableitungstabelle** — Normstelle → betriebliche Pflicht → Systemanforderung. Ziel: 20–30 Kandidaten. Das ist dein größter Hebel, weil du die Norm schon im Kopf hast. | 2 Tage | Kern des Katalogs |
| 4 | **Soll-Prozess durchgehen** — jeder Schritt mit Systembeteiligung erzeugt 1–3 Anforderungen (Quelle SP-xx) | 1 Tag | +10–15 Kandidaten |
| 5 | **NFA-Kandidaten** über die ISO-25010-Checkliste + Randbedingungen; Zielwerte als Platzhalter markieren („Zielwert: im Interview zu klären") | ½ Tag | 8–12 NFA/RB |
| 6 | **Use-Case-Diagramm** aus Soll-Prozess und Akteuren, 3–4 Kurzbeschreibungen (je 3 Sätze) | 1 Tag | 1 Abbildung + 1 Seite |
| 7 | **Interviewleitfaden anpassen** — siehe unten | ½ Tag | fertiger Leitfaden |
| 8 | **Methodikkapitel schreiben** — geht jetzt komplett | 2 Tage | 4–5 Seiten |
| 9 | **Ergebniskapitel vorschreiben** — Kontext, Stakeholder, Katalogstruktur, Herleitungslogik, normative Kandidaten; Lücken für Interviewergebnisse markieren | 2 Tage | 6–8 Seiten Gerüst |
| 10 | Glossar nebenbei füllen | laufend | Anhang |

**Summe: rund 10 Arbeitstage — passt in zwei Wochen, auch wenn die Interviews noch nicht stattgefunden haben.**

## Interviews: kürzer, gezielter, doppelt genutzt

Weil du bereits Kandidaten hast, sind die Interviews keine Erhebung bei null mehr. Baue sie in **drei Blöcken à 15–20 Minuten**:

1. **Ist und Schwachstellen** — „Führen Sie mich durch eine Prüfung, wie sie heute wirklich läuft. Was ärgert, was fehlt, was dauert?" → Ist-Situation, Schwachstellentabelle, neue Anforderungen (Quelle I-xx)
2. **Walkthrough der Kandidatenliste** — Katalog gruppiert nach Prozessschritt vorlegen: „Fehlt etwas? Ist etwas falsch oder unrealistisch? Welche Zielwerte sind realistisch (Zeit pro Prüfung, Offline-Dauer, Aufbewahrung)?" → Ergänzung, Korrektur, NFA-Zielwerte
3. **Priorisierung** — jede Anforderung Must / Should / Could; bei Widerspruch zwischen Experten dokumentieren → Priorisierung durch Stakeholder

Das ist methodisch ein **kombiniertes Erhebungs- und Validierungsinterview** — so nennst du es auch. Vorteil: Ein Termin pro Experte reicht, und du sparst die separate Validierungsrunde. Wenn du zwei Experten bekommst, ist das ausreichend; drei sind gut; mehr brauchst du bei dieser Anlage nicht.

**Deadline setzen:** Wenn bis Ende Woche 2 kein Termin steht, wechsle auf Plan B: zwei 30-Minuten-Gespräche per Telefon/Teams oder eine schriftliche Rückmeldung zur Kandidatenliste. Beides ist als Limitation benennbar, und der normativ hergeleitete Katalog trägt die Arbeit auch allein.

## Wochenplan

| Woche | Schwerpunkt |
|---|---|
| **1** | Aufgaben 1–5 und 7. Interviewtermine fixieren — täglich nachfassen. |
| **2** | Aufgaben 6, 8, 9. Interviews möglichst hier. Deadline Plan B am Wochenende. |
| **3** | Interviews auswerten (Paraphrase → Kategorie → Anforderung, keine Volltranskription), Katalog ergänzen und priorisieren, Kapitel „Ist-Situation und Ergebnisse" schreiben. |
| **4** | Diskussion, Limitationen, Fazit, Ausblick. Anhang zusammenstellen. |
| **½** | Korrekturlesen, Formatierung, Abbildungen prüfen, Puffer. |

## Seitenbudget für den Rest (Ziel ca. 42 Seiten)

| Kapitel | Seiten |
|---|---|
| Methodisches Vorgehen | 4–5 |
| Anforderungsmodell (Kontext, Stakeholder, Soll-Prozess-Verweis, Use-Cases, Herleitung, Katalogauszug) | 9–11 |
| Ist-Situation und Interviewergebnisse (Schwachstellen, Ergänzungen, Priorisierung) | 3–4 |
| Diskussion, Limitationen, Fazit, Ausblick | 3–4 |
| **Summe neu** | **19–24** |

Der Anhang (vollständiger Katalog, Leitfaden, Auswertungstabellen, Glossar) zählt in der Regel nicht zum Umfang — prüfe das in deiner Prüfungsordnung.

## Was aus dem großen Leitfaden du wirklich brauchst

| Jetzt lesen | Wofür |
|---|---|
| Kap. 2 (Anforderungsarten) | damit die Kandidaten sauber sortiert sind |
| Kap. 4.2 (Normanalyse) | Vorlage für die Ableitungstabelle |
| Kap. 6.2–6.3 (Satzschablone, Attribute) | Formulierung der Kandidaten |
| Kap. 8.2 (Kernprozesse) | Suchraster, ob du im Katalog etwas übersehen hast |
| Vorlage Interviewleitfaden | Blöcke 2–4 und 6 auf die Drei-Block-Struktur oben eindampfen |

Alles andere: bei Bedarf nachschlagen, nicht durcharbeiten.
