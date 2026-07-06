# 06 — Open Questions

Dieses Dokument sammelt offene Theorie-, Design- und Simulationsfragen.

## Kategorien

| Kategorie | Bedeutung |
|---|---|
| Theorie | Betrifft die Grundlogik des Magie-Systems. |
| Syntax | Betrifft Aufbau und Kombinierbarkeit von Zaubern. |
| Semantik | Betrifft Bedeutung einzelner Zeichen, Operatoren oder Modifier. |
| Kosten | Betrifft Grenzen, Aufwand und Risiko. |
| Simulation | Betrifft technische Abbildbarkeit. |
| Gameplay | Betrifft spätere Spielbarkeit. |
| Lore | Betrifft Weltdeutung, Kultur oder Erzählung. |

## Teilweise geklärte Fragen

### OQ-001 — Was ist Magie ontologisch?

**Kategorie:** Theorie  
**Status:** Teilweise geklärt durch DD-003 und DD-004

Magie wird nicht als beliebige Realitätsüberschreibung behandelt. Vorläufig gilt:

```text
Magie = regelgebundene Zustandsmanipulation unter Erhaltungssätzen und Mana-/Arbeitskosten
```

Mana selbst ist kein konkreter Stoff, sondern ein abstrakter Energie-/Arbeitsbegriff.

**Noch offen:**  
Ob es in-world zusätzlich ein Trägermedium, Teilchenfeld oder eine physikalische Kopplungsschicht für Mana gibt.

### OQ-004 — Wie entstehen Fehlerfälle?

**Kategorie:** Kosten / Simulation / Gameplay  
**Status:** Teilweise geklärt

Fehlerfälle sollen bevorzugt emergent entstehen:

- unzureichende Mana-Quelle
- syntaktisch falscher Zauber
- semantischer Widerspruch
- ungültige Zielauswahl
- nicht mehr zugreifbare Referenz/Bibliothek/Fokusstruktur
- nicht abgeführte Verlustwärme
- instabile Bindung

**Noch offen:**  
Ob zusätzlich abstrakte Misslingen-Modifier für bestimmte Gameplay- oder Simulationssituationen nötig sind.

## Offene Fragen

### OQ-002 — Welche Form hat ein Zauber intern?

**Kategorie:** Syntax / Simulation  
**Status:** Offen

Ist ein Zauber besser als lineare Sequenz, Syntaxbaum, Graph, Komponentenobjekt oder Hybridmodell beschreibbar?

### OQ-003 — Wie wird Zielauswahl definiert?

**Kategorie:** Semantik / Simulation  
**Status:** Offen

Wir müssen klären, ob Ziele über Sicht, Entfernung, Symbolbindung, Materialeigenschaft, Koordinate, Name, Kontakt oder Relation ausgewählt werden.

### OQ-005 — Was begrenzt Rekursion und Kombinatorik?

**Kategorie:** Theorie / Syntax / Kosten  
**Status:** Offen

Wenn Modifier auf Modifier oder Zauber auf Zauber wirken können, braucht das System Grenzen gegen unendliche Verstärkung oder Selbstreferenz.

### OQ-006 — Gibt es eine direkte Mana-Joule-Umrechnung?

**Kategorie:** Kosten / Simulation  
**Status:** Offen

Mana ist als abstrakte magische Arbeitswährung festgelegt. Offen ist, ob ein Mana exakt einer physikalischen Energiemenge entspricht oder ob Mana-Joule nur eine interne Simulationsgröße ist.

### OQ-007 — Wie wird biologische Materie magisch verbrannt?

**Kategorie:** Theorie / Kosten / Simulation  
**Status:** Offen

Lebewesen oder biologische Materie können als Mana-Quelle dienen, indem chemisch gebundene Energie magisch nutzbar gemacht wird. Offen ist, ob dieser Prozess analog zu Stoffwechsel, Verbrennung, Lebensenergieentzug oder direkter chemischer Umwandlung modelliert wird.

### OQ-008 — Gibt es ein Mana-Trägermedium?

**Kategorie:** Theorie / Lore / Simulation  
**Status:** Offen

Obwohl Mana als abstrakter Arbeitsbegriff definiert ist, könnte die Welt dennoch ein generisches Medium, Feld oder Teilchen besitzen, das magische Energie transportiert oder koppelt.

### OQ-009 — Wie werden zeitähnliche Effekte formalisiert?

**Kategorie:** Theorie / Simulation  
**Status:** Offen

Zeitumkehrung, Zeitverlangsamung und Zeitbeschleunigung sollen nicht als Bruch von Naturgesetzen behandelt werden, sondern möglicherweise als präzise Manipulation von Zustandsvektoren, Bewegungen oder lokalen Prozessraten.

### OQ-010 — Wie wird visuelle Syntax geparst?

**Kategorie:** Syntax / Semantik / Simulation  
**Status:** Offen

Jeder ausführbare Zauber braucht eine physische visuelle Repräsentation. Offen ist, wie Zeichnungen, Glyphen, Gravuren oder Tattoos formal geparst und in ausführbare Datenstrukturen übersetzt werden.

### OQ-011 — Was ist ein ausführbarer Zauber?

**Kategorie:** Syntax / Simulation / Gameplay  
**Status:** Offen

Ein abstrakt programmierter Zauber muss in eine visuelle Repräsentation übersetzbar sein. Eine visuelle Repräsentation muss in Programm-Logik übersetzbar sein. Offen ist, welche Mindestbedingungen ein Zauber erfüllen muss, um als ausführbar zu gelten.
