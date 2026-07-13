# Spell Editor Architecture

**Stand:** 2026-07-13, 18:18 Europe/Berlin  
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
- späterer Simulation.

Er soll beim Entwickeln der Zauber-Syntax helfen und gleichzeitig testen, ob die visuelle Sprache, die interne Datenstruktur und die Regelengine wechselseitig übersetzbar sind.

```text
visuelle Zauberstruktur
    ↔ SpellIR
    ↔ textuelle Zauber-Syntax
    ↔ Regelengine
    ↔ Simulation / Testumgebung
```

---

## 2. Grundaufbau

Der Editor besteht vorläufig aus drei Hauptbereichen.

```text
+--------------------------------------------------------------+
| Visuelle Programmierfläche        | Code-/IDE-Fenster         |
|                                   |                           |
| Graph, Glyphen, Makros,           | Textuelle Zauber-Syntax,   |
| Verbindungen, Layout,             | Autocomplete, Kategorien,  |
| Symmetrisierung                   | Parserfeedback             |
|                                   |---------------------------|
|                                   | Genie-Fenster              |
|                                   | natürliche Beschreibung,   |
|                                   | LLM-Vorschlag, Varianten   |
+--------------------------------------------------------------+
```

---

## 3. Linke Seite: Visuelle Programmierfläche

Die linke Seite ist eine graphartige Arbeitsfläche für Zauberbilder.

Funktionen:

- syntaktische Elemente per Drag & Drop platzieren,
- gespeicherte Makros platzieren,
- Knoten verbinden,
- Trigger-, Ziel-, Wirkungs-, Modifier-, Energie- und Sicherheitsknoten anordnen,
- visuelles Feedback zu offenen oder ungültigen Verbindungen anzeigen,
- Zauber testweise validieren,
- nach erfolgreicher Prüfung automatisch symmetrisieren, ordnen oder stilisieren.

Wichtig:

Die sichtbare Darstellung während des Bearbeitens muss nicht bereits die finale in-world-Glyphe sein. Der Editor darf zunächst eine verständliche Arbeitsgraph-Darstellung zeigen und daraus beim Testen/Validieren eine regelkonforme, schönere oder stärker arkane visuelle Repräsentation erzeugen.

```text
Arbeitsgraph → Visualizer/Layout → gültige Zauberrepräsentation
```

---

## 4. Rechte Seite oben: Code-/IDE-Fenster

Das Codefenster zeigt die formale Zauber-Syntax.

Funktionen:

- Zauber direkt in einer textuellen Syntax schreiben,
- bekannte Operationen per Autocomplete vorschlagen,
- Operator-Kategorien als Menü anbieten,
- Bausteine per Drag & Drop in die Codefläche einfügen,
- Syntaxfehler markieren,
- semantische Warnungen anzeigen,
- Änderungen live mit der visuellen Darstellung synchronisieren.

Beispielhafte Arbeitsweise:

```text
Spieler schreibt Syntax rechts
    → Parser erzeugt SpellIR
    → Visualizer erzeugt links die visuelle Struktur
```

---

## 5. Rechte Seite unten: Genie-Fenster

Das Genie-Fenster ist die natürlichsprachige Schnittstelle.

Funktionen:

- Zauberwirkung in natürlicher Sprache beschreiben,
- mögliche fehlende Parameter erkennen,
- Varianten vorschlagen,
- eine formale Zauberstruktur vorschlagen,
- die textuelle Syntax und visuelle Darstellung daraus erzeugen lassen.

Wichtig:

Das Genie erzeugt nur Vorschläge. Es ist nicht regelautoritativ.

```text
natürliche Beschreibung
    ↓
LLM / Genie
    ↓
Draft SpellIR
    ↓
Regelengine
    ↓
Syntax + Visualisierung oder Fehlermeldung
```

Ein ungültiger Vorschlag bleibt ungültig, auch wenn er natürlichsprachlich plausibel klingt.

---

## 6. Gemeinsame Zwischenstruktur: SpellIR

Damit visuelle Darstellung, Textsyntax und Genie-Fenster synchron bleiben, braucht der Editor eine gemeinsame interne Zwischenstruktur.

Vorläufiger Name:

```text
SpellIR = Spell Intermediate Representation
```

SpellIR ist nicht zwingend die finale Simulationsstruktur, sollte aber nah genug daran liegen, dass die Regelengine sie prüfen kann.

Minimal enthält SpellIR:

- Aktivierungsknoten,
- Zielmodell,
- Wirkungsmodell,
- Struktur-/Geometriemodell,
- Modifier,
- Ressourcenmodell,
- Terminationsmodell,
- Fehler-/Failsafe-Modell,
- Referenzen auf Bibliotheken oder Makros,
- Repräsentationsdaten bzw. Visualisierungsanweisungen.

---

## 7. Synchronisationsmodell

Alle drei Eingabeformen sollen denselben Zauber beschreiben können.

```text
Visual Canvas ↔ SpellIR ↔ Code Editor
                  ↑
                  |
             Genie Draft
```

### Von links nach rechts

```text
Graph/Glyphe wird verändert
    → Parser/Graph-Mapper aktualisiert SpellIR
    → Codefenster wird aktualisiert
```

### Von rechts nach links

```text
Code wird verändert
    → Parser aktualisiert SpellIR
    → Visualizer aktualisiert Graph/Glyphe
```

### Von unten nach oben

```text
Genie-Vorschlag
    → Draft SpellIR
    → Regelvalidierung
    → Code + Visualisierung werden erzeugt
```

---

## 8. Testen / Validieren

Der Button `Testen` bedeutet nicht automatisch, dass ein Zauber in der Welt gewirkt wird.

Er kann stufenweise arbeiten:

1. Syntaxprüfung,
2. Semantikprüfung,
3. Bibliotheksprüfung,
4. Ressourcenprüfung,
5. Repräsentationsprüfung,
6. Simulationsfähigkeit,
7. optionaler Testlauf in Sandbox.

```text
Testen = prüfen, visualisieren, ggf. in isolierter Umgebung simulieren
```

---

## 9. Spätere Spielintegration

Der Editor sollte so gestaltet werden, dass er später im Spiel wiederverwendet werden kann.

Mögliche in-world-Varianten:

- Zauberbuch-Editor,
- Schriftrollenwerkbank,
- Ritualkreis-Editor,
- Tattoo-/Gravurwerkzeug,
- Artefakt-Konfigurationsoberfläche,
- Akademie-/Labor-Interface.

Die UI darf für den Prototyp abstrakter sein, sollte aber keine Annahmen treffen, die eine spätere in-world-Integration unmöglich machen.

---

## 10. Abgrenzung

Der Spell Editor ist nicht:

- die Regelengine selbst,
- die vollständige Simulation,
- eine Ausnahme von der physischen Repräsentationspflicht,
- eine LLM-Autorität,
- ein Ersatz für formale Zaubersyntax.

Er ist ein Entwicklungs-, Übersetzungs-, Diagnose- und späteres Gameplay-Werkzeug.

---

## 11. Offene Fragen

| Kategorie | Frage |
|---|---|
| Offene Frage | Wird der erste Editor in Godot, Web/Canvas, Python, Unity oder als eigenes Minimaltool gebaut? |
| Offene Frage | Ist SpellIR identisch mit der späteren Simulationsstruktur oder nur eine Editor-Zwischenschicht? |
| Offene Frage | Wie stark darf der Visualizer die vom Spieler gezeichnete Struktur automatisch symmetrisieren? |
| Offene Frage | Wird die finale visuelle Glyphe deterministisch aus SpellIR erzeugt? |
| Offene Frage | Wie werden Makros in der visuellen Palette, im Codefenster und im Genie-Fenster gleichwertig dargestellt? |
| Offene Frage | Wie werden gefährliche Modi wie autonomer Quellenlauf oder fehlende Failsafes visuell gewarnt? |

---

## 12. Arbeitsstand

| Kategorie | Inhalt |
|---|---|
| Feature | Ein dreigeteilter Spell Editor soll visuelle Zauberstruktur, Code-Syntax und Genie-Fenster verbinden. |
| Hypothese | Der Editor ist ein guter erster ausführbarer Prototyp, weil er Syntax, Visualisierung und Validierung früh zusammenführt. |
| Hypothese | Eine gemeinsame `SpellIR` ist notwendig, damit alle Eingabeformen synchron bleiben. |
| Festgelegt | Das LLM/Genie bleibt Hilfsmittel und wird durch die Regelengine validiert. |
| Offene Frage | Konkrete Technologie und Umfang des ersten Editor-Prototyps sind noch nicht entschieden. |
