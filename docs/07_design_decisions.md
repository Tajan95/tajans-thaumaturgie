# 07 — Design Decisions

Dieses Dokument hält getroffene Designentscheidungen fest.

Ziel ist, spätere Änderungen nachvollziehbar zu machen und nicht dieselben Grundfragen mehrfach neu zu diskutieren.

## Format

```md
## DD-000 — Titel

**Datum:** YYYY-MM-DD  
**Status:** Festgelegt / Ersetzt / Verworfen  
**Kontext:** Warum stand die Entscheidung an?  
**Entscheidung:** Was wurde entschieden?  
**Begründung:** Warum wurde so entschieden?  
**Folgen:** Was ergibt sich daraus?
```

## Entscheidungen

### DD-001 — Projektstruktur wird modular dokumentiert

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Das Projekt soll nicht in einer chaotischen Sammeldatei wachsen, sondern versionierbar und logisch gegliedert sein.

**Entscheidung:**  
Das Repository verwendet eine modulare Struktur mit `docs/`, `notes/`, `prototype/` und `issues/`.

**Begründung:**  
Theorie, Rohnotizen, technische Experimente und Arbeitsaufgaben müssen getrennt bleiben, damit das System langfristig wartbar bleibt.

**Folgen:**  
Neue stabile Inhalte werden in passende `docs/`-Dateien überführt. Unsortierte Gedanken bleiben zunächst in `notes/raw_notes.md`.

### DD-002 — Zauber müssen ableitbar sein

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Das System soll sich von klassischer Fantasy-Magie unterscheiden, in der Zauber oft als feste Einzelaktionen existieren.

**Entscheidung:**  
Ein Zauber darf nicht einfach existieren, sondern muss aus kleineren Komponenten logisch ableitbar sein.

**Begründung:**  
Nur dadurch wird Magie programmierbar, simulierbar und systematisch erweiterbar.

**Folgen:**  
Konkrete Zauber wie Feuerball, Barriere oder Heilung gelten zunächst nur als Beispiele. Sie müssen später aus Ontologie, Syntax, Operatoren, Modifiern und Kostenmodell konstruiert werden.
