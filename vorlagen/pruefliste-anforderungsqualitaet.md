# Prüfliste: Qualität der Anforderungen

> Einmal komplett durch den fertigen Katalog gehen. Dauert ein bis zwei Stunden
> und hebt die Qualität der Arbeit spürbar.

## A. Je Anforderung (Kriterien nach ISO/IEC/IEEE 29148)

| # | Kriterium | Prüffrage | ✓ |
|---|---|---|---|
| 1 | Notwendig | Würde das Fehlen ein echtes Problem verursachen? | ☐ |
| 2 | Eindeutig | Kann man den Satz nur auf eine Weise verstehen? | ☐ |
| 3 | Vollständig | Sind Akteur, Bedingung, Objekt und Ergebnis genannt? | ☐ |
| 4 | Atomar | Genau eine Anforderung pro Satz? | ☐ |
| 5 | Konsistent | Kein Widerspruch zu anderen Anforderungen? | ☐ |
| 6 | Verifizierbar | Gibt es ein Akzeptanzkriterium? | ☐ |
| 7 | Realisierbar | Technisch und wirtschaftlich machbar? | ☐ |
| 8 | Verfolgbar | Quelle dokumentiert? | ☐ |
| 9 | Lösungsneutral | Keine Technologie- oder Oberflächenvorgabe? | ☐ |
| 10 | Systembezogen | Subjekt ist das System, nicht ein Mensch oder ein Prozess? | ☐ |

## B. Sprachliche Defekte — per Suchfunktion prüfen

| Suchbegriff | Verdacht | Korrektur |
|---|---|---|
| „wird", „werden" | Passiv ohne Akteur | „Das System MUSS …" |
| „-ung", „-erfassung", „-prüfung" am Satzanfang | Nominalisierung | In ein Verb auflösen |
| „und", „sowie", „bzw.", „oder" | Mehrere Anforderungen in einem Satz | Aufteilen |
| „alle", „jeder", „immer", „nie", „jederzeit" | Universalquantor — stimmt das wirklich? | Präzisieren oder Ausnahmen benennen |
| „schnell", „einfach", „intuitiv", „benutzerfreundlich", „modern", „performant", „sicher" | Unprüfbares Adjektiv | Messgröße + Zielwert ergänzen |
| „möglichst", „in der Regel", „soweit möglich", „zeitnah", „gegebenenfalls" | Weichmacher | Streichen oder als SOLLTE deklarieren |
| „besser", „mehr", „schneller als" | Unvollständiger Vergleich | Vergleichsgröße nennen |
| „Daten", „Informationen", „System" (unspezifisch) | Unklares Substantiv | Konkret benennen |
| „soll", „sollte", „muss", „kann" (klein, gemischt) | Uneinheitliche Verbindlichkeit | Auf MUSS/SOLLTE/WIRD vereinheitlichen |
| „z. B.", „usw.", „etc.", „..." | Unvollständige Aufzählung | Vollständig auflisten oder Regel formulieren |

## C. Katalog als Ganzes

| # | Prüffrage | ✓ |
|---|---|---|
| 1 | Ist jeder Prozessschritt des Soll-Prozesses durch mindestens eine Anforderung abgedeckt? | ☐ |
| 2 | Hat jede Schwachstelle aus der Ist-Analyse eine zugehörige Anforderung? | ☐ |
| 3 | Hat jede erhobene Normpflicht eine zugehörige Anforderung? | ☐ |
| 4 | Gibt es Anforderungen ohne Quelle? (→ streichen oder belegen) | ☐ |
| 5 | Sind alle drei Typen (FA, NFA, RB) vertreten und getrennt? | ☐ |
| 6 | Wurden die ISO-25010-Merkmale systematisch durchgegangen? | ☐ |
| 7 | Sind Konflikte zwischen Anforderungen identifiziert und aufgelöst? | ☐ |
| 8 | Werden die Glossarbegriffe durchgängig einheitlich verwendet? | ☐ |
| 9 | Ist die Priorisierung von Stakeholdern bestätigt? | ☐ |
| 10 | Sind IDs lückenlos, eindeutig und nirgends doppelt vergeben? | ☐ |

## D. Konflikte dokumentieren

| Konflikt-ID | Anforderung A | Anforderung B | Art des Konflikts | Auflösung | Entschieden von |
|---|---|---|---|---|---|
| K-01 | | | Ziel- / Ressourcen- / Wertkonflikt | | |

*Dokumentierte und aufgelöste Konflikte sind ein Qualitätsmerkmal deiner Arbeit — sie zeigen, dass du die Anforderungen wirklich gegeneinander geprüft hast.*
