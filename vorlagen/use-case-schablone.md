# Vorlage: Use-Case-Beschreibung

| Feld | Inhalt |
|---|---|
| **ID / Name** | UC-__ — «Verb + Objekt», z. B. „Elementprüfung durchführen" |
| **Ziel** | Was erreicht der Akteur? Ein Satz. |
| **Primärer Akteur** | Wer startet den Anwendungsfall? |
| **Weitere Beteiligte** | Andere Akteure oder Nachbarsysteme |
| **Auslöser** | Welches Ereignis startet den Ablauf? |
| **Vorbedingungen** | Was muss vorher gelten? |
| **Nachbedingung (Erfolg)** | Welcher Zustand gilt nach erfolgreichem Abschluss? |
| **Nachbedingung (Misserfolg)** | Was gilt, wenn es schiefgeht? |
| **Häufigkeit** | z. B. ca. 40× pro Schicht |
| **Priorität** | Must / Should / Could |

### Standardablauf

| # | Akteur | Systemreaktion |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

### Alternativabläufe

*(Andere Wege zum selben Ziel. Nummerierung nach dem Schritt, bei dem sie abzweigen.)*

- **3a.** … → weiter bei Schritt 4
- **5a.** …

### Ausnahmeabläufe

*(Das Ziel wird nicht erreicht. Hier stecken die meisten übersehenen Anforderungen —
geh jeden Schritt durch und frag: „Was, wenn das hier nicht klappt?")*

- **2a.** … → Abbruch mit Meldung
- **4a.** …
- **\*.** Gilt in jedem Schritt: z. B. Verbindungsverlust, Abbruch durch Nutzer

### Beteiligte Anforderungen

FA-___, FA-___, NFA-___

### Offene Fragen

- [ ] …

---

## Checkliste für gute Use-Cases

- [ ] Name ist „Verb + Objekt" aus Sicht des Akteurs
- [ ] Das Ziel ist für den Akteur fachlich sinnvoll (kein technischer Teilschritt wie „Daten speichern")
- [ ] Der Standardablauf hat 3–9 Schritte (mehr → aufteilen)
- [ ] Jeder Schritt nennt, wer handelt
- [ ] Keine Bedienoberfläche beschrieben („klickt auf Button X") — das ist Lösungsdesign
- [ ] Mindestens zwei Ausnahmeabläufe betrachtet
- [ ] Alle im Ablauf sichtbaren Anforderungen sind im Katalog erfasst
