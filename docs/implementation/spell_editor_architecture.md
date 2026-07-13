# Spell Editor Architecture

**Stand:** 2026-07-14, 01:44 Europe/Berlin  
**Status:** Feature-Hypothese / früher Prototypkandidat

Dieses Dokument skizziert einen ausführbaren Zauber-Editor als mögliche erste konkrete Softwarekomponente des Projekts.

Der Editor soll nicht nur ein externes Entwicklerwerkzeug sein, sondern perspektivisch als Spielkomponente wiederverwendbar bleiben.

---

## 1. Zweck

Der Editor dient als Brücke zwischen:

- visueller Zaubersprache,
- formaler Zauber-Syntax,
- natürlicher Sprache,
- Regelvalidierung,
- Kosten- und Erhaltungsprüfung,
- späterer Simulation.

```text
visuelle Zauberstruktur
    ↔ SpellIR
    ↔ textuelle Zauber-Syntax
    ↔ Regelengine
    ↔ Simulation / Testumgebung
```

Er soll bereits während der Theorieentwicklung prüfen, ob Datenstruktur, visuelle Sprache und Code-Syntax wechselseitig übersetzbar sind.

---

## 2. Grundaufbau

```text
+--------------------------------------------------------------+
| Visuelle Programmierfläche        | Code-/IDE-Fenster         |
|                                   |                           |
| Graph, Glyphen, Makros,           | Textuelle Zauber-Syntax,   |
| typisierte Ports, Layout,         | Autocomplete, Kategorien,  |
| Symmetrisierung                   | Parserfeedback             |
|                                   |---------------------------|
|                                   | Genie-Fenster              |
|                                   | natürliche Beschreibung,   |
|                                   | LLM-Vorschlag, Varianten   |
+--------------------------------------------------------------+
```

---

## 3. Linke Seite: Visuelle Programmierfläche

Funktionen:

- syntaktische Knoten per Drag & Drop platzieren,
- gespeicherte Makros platzieren,
- typisierte Ports verbinden,
- Activation-, Target-, Query-, Effect-, Ressourcen- und Sicherheitsknoten anordnen,
- parallele und sequenzielle Graphzweige darstellen,
- offene, inkompatible oder gefährliche Verbindungen markieren,
- Makros expandieren und einklappen,
- Zauber validieren,
- nach erfolgreicher Prüfung automatisch ordnen, symmetrisieren oder stilisieren.

```text
Arbeitsgraph
→ Parser / Graph-Mapper
→ validierte SpellIR
→ Visualizer / Layout
→ in-world-Zauberrepräsentation
```

Die verständliche Arbeitsgraph-Darstellung muss nicht identisch mit der finalen arkanen Glyphe sein.

---

## 4. Typisierte visuelle Ports

Knoten dürfen nur semantisch passende Daten austauschen.

Beispiele:

```text
TargetNode.output: TargetSet
EffectNode.subject_input: TargetSet
EffectNode.energy_source_input: TargetSet
QueryNode.output: InformationValue oder TargetSet
EffectNode.output: StateChangeRequest[]
```

Gültig:

```text
WasserTargetSet
→ TransferThermalEnergy.subject
```

Ungültig:

```text
Temperaturwert
→ ObjectRef-Port
```

Der Editor soll ungültige Verbindungen möglichst vor dem vollständigen Kompilieren verhindern oder klar markieren.

---

## 5. Rechte Seite oben: Code-/IDE-Fenster

Funktionen:

- Zauber direkt in textueller Syntax schreiben,
- Node- und Operationsnamen per Autocomplete vorschlagen,
- Zielrollen und Porttypen anzeigen,
- Operator-Kategorien als Menü anbieten,
- Bausteine per Drag & Drop in die Codefläche einfügen,
- Syntaxfehler markieren,
- semantische und physikalische Warnungen anzeigen,
- Änderungen live mit Graph und Glyphe synchronisieren.

```text
Code wird verändert
→ Parser erzeugt/ändert SpellIR
→ Graph und visuelle Darstellung werden aktualisiert
```

---

## 6. Rechte Seite unten: Genie-Fenster

Funktionen:

- gewünschte Zauberwirkung natürlichsprachlich beschreiben,
- fehlende Zielrollen und Parameter erkennen,
- Varianten mit unterschiedlichen Sicherheits-/Kostenprofilen anbieten,
- einen formalen Graphvorschlag erzeugen,
- Code- und visuelle Darstellung generieren.

```text
natürliche Beschreibung
    ↓
LLM / Genie
    ↓
Draft SpellIR
    ↓
Regelengine
    ↓
validierter Graph oder Fehlermeldung
```

Das Genie ist nicht regelautoritativ. Es darf Target-, Effect-, Ressourcen- oder Sicherheitsknoten vorschlagen, aber nicht unsichtbar Grundregeln umgehen.

---

## 7. Gemeinsame Zwischenstruktur: SpellIR

```text
SpellIR = Spell Intermediate Representation
```

Vorläufige Struktur:

```text
SpellIR {
    representation_model
    activation_nodes[]

    graph {
        target_nodes[]
        query_and_analysis_nodes[]
        effect_nodes[]
        control_nodes[]
        resource_nodes[]
        safety_nodes[]
        edges[]
    }

    execution_policy
    termination_policy
    failure_model
    library_references[]
    visualization_hints
}
```

SpellIR ist nicht zwingend identisch mit dem finalen Laufzeitformat. Sie muss aber nah genug an der Simulation liegen, dass Regel-, Kosten- und Typprüfung auf ihr möglich sind.

---

## 8. TargetNode im Editor

Ein TargetNode erzeugt ein `TargetSet`.

Im Inspector oder Codefenster müssen mindestens sichtbar sein:

- Selektor
- Anker
- Suchraum
- Filter
- Granularität
- `snapshot` oder `live`
- Aktualisierungsrate
- Zugriffsvoraussetzungen
- Fehlerpolicy

Der Editor sollte Live-Bindungen, große Suchräume und informationsintensive Filter als erhöhte Kosten- oder Risikofaktoren markieren.

---

## 9. EffectNode im Editor

Ein primitiver EffectNode enthält eine atomare Zustandsoperation.

Beispiele:

```text
ApplyForce
TransferThermalEnergy
TransferCharge
TransportComponentMass
ChangeBondStructure
```

Der Editor sollte anzeigen:

- Effect-Domäne
- Operation
- benötigte Zielrollen
- Parameter
- Präzisionsanforderung
- Ausführungsmodus
- erwartete Quellen, Senken und Nebenprodukte
- geschätzte physikalische und thaumische Kosten

Mehrere Effekte werden über getrennte Graphzweige kombiniert.

---

## 10. Makros

Ein Makro kann im Editor als einzelner kompakter Knoten erscheinen.

```text
MacroNode
→ intern expandierbarer Teilgraph
```

Der Editor muss mindestens zwei Ansichten anbieten können:

```text
kompakt:
MacroNode

expandiert:
Target-/Query-/Effect-/Safety-Teilgraph
```

Kosten und Validierung beziehen sich immer auf den expandierten Graphen.

---

## 11. StateChangeRequest-Vorschau

EffectNodes verändern die Welt nicht direkt, sondern erzeugen `StateChangeRequest`s.

Der Editor kann diese in einer Diagnoseansicht darstellen:

```text
angeforderte Zustandsdeltas
physikalische Mindestarbeit
Steuerarbeit
Energiequelle
Senke
Nebenprodukte
Erhaltungsbedingungen
Fehlerpolicy
```

So kann der Spieler erkennen, warum ein formal plausibler Zauber teuer, unmöglich oder gefährlich ist.

---

## 12. Synchronisationsmodell

```text
Visual Canvas ↔ SpellIR ↔ Code Editor
                  ↑
                  |
             Genie Draft
```

### Visuell → Code

```text
Graph wird verändert
→ Graph-Mapper aktualisiert SpellIR
→ Codefenster wird aktualisiert
```

### Code → Visuell

```text
Code wird verändert
→ Parser aktualisiert SpellIR
→ Visualizer aktualisiert Graph/Glyphe
```

### Genie → beide Ansichten

```text
Genie-Vorschlag
→ Draft SpellIR
→ Regelvalidierung
→ Code + Graph + Glyphe
```

---

## 13. Testen / Validieren

Der Button `Testen` bedeutet nicht automatisch, dass der Zauber in der Welt gewirkt wird.

Prüfstufen:

1. Parser- und Syntaxprüfung
2. Typ- und Portprüfung
3. Ziel- und Bindungsprüfung
4. Semantikprüfung
5. Bibliotheksprüfung
6. Ressourcen- und Kopplungsprüfung
7. Erhaltungsprüfung
8. StateChangeRequest-Erzeugung
9. Repräsentationsprüfung
10. Simulationsfähigkeit
11. optionaler Sandbox-Testlauf

```text
Testen = prüfen, erklären, visualisieren und optional isoliert simulieren
```

---

## 14. Fehlerdiagnose

Mögliche Editorfehler:

| Fehler | Beispiel |
|---|---|
| fehlender Port | EffectNode besitzt kein `subject` |
| Typfehler | Temperaturwert an TargetSet-Port |
| leeres TargetSet | kein Wasser im Suchraum |
| unklare Zielrolle | Quelle und Senke nicht unterschieden |
| Ressourcenfehler | Energiequelle reicht nicht |
| Erhaltungsfehler | Masse verschwindet beim Trennen |
| Konfliktfehler | parallele Effekte fordern unvereinbare Deltas |
| Sicherheitswarnung | autonomer Lauf ohne Limit |
| Repräsentationsfehler | Graph nicht als gültige Geometrie darstellbar |

---

## 15. Spätere Spielintegration

Mögliche in-world-Varianten:

- Zauberbuch-Editor
- Schriftrollenwerkbank
- Ritualkreis-Editor
- Tattoo-/Gravurwerkzeug
- Artefakt-Konfiguration
- Akademie-/Labor-Interface

Die frühe UI darf abstrakter sein, sollte aber dieselbe SpellIR verwenden wie die spätere Spielkomponente.

---

## 16. Abgrenzung

Der Spell Editor ist nicht:

- die Regelengine selbst,
- die vollständige Simulation,
- eine Ausnahme von der Repräsentationspflicht,
- eine LLM-Autorität,
- ein Ersatz für formale Syntax.

Er ist Entwicklungs-, Übersetzungs-, Diagnose- und späteres Gameplay-Werkzeug.

---

## 17. Offene Fragen

| Kategorie | Frage |
|---|---|
| Offene Frage | Wird der erste Editor in Godot, Web/Canvas, Python, Unity oder als eigenes Minimaltool gebaut? |
| Offene Frage | Ist SpellIR identisch mit der Laufzeitstruktur oder eine Editor-Zwischenschicht? |
| Offene Frage | Wie stark darf der Visualizer automatisch symmetrisieren? |
| Offene Frage | Wird die finale Glyphe deterministisch aus SpellIR erzeugt? |
| Offene Frage | Wie werden Makros in Graph, Code und Genie gleichwertig dargestellt? |
| Offene Frage | Wie werden Kosten, Erhaltung und StateChangeRequests verständlich visualisiert? |
| Offene Frage | Wie werden parallele Konflikte im Graphen dargestellt? |

---

## 18. Arbeitsstand

| Kategorie | Inhalt |
|---|---|
| Feature | Dreigeteilter Spell Editor verbindet Graph, Code und Genie. |
| Festgelegt | TargetNodes, EffectNodes und typisierte Ports sind Bestandteile der SpellIR-Arbeitsstruktur. |
| Festgelegt | Makros werden für Kosten und Validierung expandiert. |
| Festgelegt | Das LLM/Genie bleibt Hilfsmittel. |
| Hypothese | Der Editor ist ein geeigneter früher Prototyp für Syntax, Visualisierung und Validierung. |
| Offene Frage | Technologie und Umfang des ersten Editor-Prototyps sind noch nicht entschieden. |
