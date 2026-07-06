# 11 — LLM Spell Compiler

Dieses Dokument beschreibt die frühe Idee, ein LLM als Übersetzungsschicht zwischen natürlicher Sprache und formaler Zaubersyntax zu verwenden.

**Status:** Feature-Idee / Architekturhypothese

---

## Grundidee

Das Magie-System selbst bleibt hart regelgebunden. Ein LLM darf keine Grundregeln brechen, sondern übersetzt natürlichsprachige Beschreibungen in erlaubte semantische Komponenten.

```text
Nutzerbeschreibung
    ↓
LLM-Interpretation
    ↓
Semantische Zauberbausteine
    ↓
Regelvalidierung
    ↓
Kostenberechnung
    ↓
Simulation
```

## Autoritative Regelengine

Die Regelengine entscheidet, ob ein vorgeschlagener Zauber gültig ist.

Das LLM darf:

- Absicht interpretieren
- fehlende Parameter vorschlagen
- passende Komponenten aus einer Bibliothek wählen
- mehrere Varianten anbieten
- die Zaubersyntax ästhetisch darstellen

Das LLM darf nicht:

- Erhaltungssätze ignorieren
- Kosten umgehen
- nicht existierende Komponenten erfinden
- ungültige Zielauswahl erzwingen
- Simulationsergebnisse direkt bestimmen

## Genie-Slider

Der Genie-Slider steuert, wie stark unausgesprochene Details ergänzt werden.

| Stufe | Bedeutung |
|---|---|
| Minimal | Nur explizit beschriebene Effekte werden umgesetzt. |
| Moderat | Naheliegende Lücken werden ergänzt und sichtbar gemacht. |
| Stark | Popkulturell/intuitiv Gemeintes wird aktiv interpretiert. |

## Offene Fragen

1. Ist der Genie-Slider ein Gameplay-System oder nur ein Editorwerkzeug?
2. Wie werden LLM-Vorschläge sichtbar validiert?
3. Wie wird verhindert, dass natürlichsprachige Bequemlichkeit die formale Zaubersprache entwertet?
4. Muss jeder generierte Zauber in eine sichtbare Formel/Glyphe rückübersetzt werden?
