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
**Status:** Teilweise geklärt durch DD-003, DD-004, DD-009 und DD-010

Magie wird nicht als beliebige Realitätsüberschreibung behandelt. Vorläufig gilt:

```text
Magie = regelgebundene Zustandsmanipulation unter Erhaltungssätzen und Mana-/Arbeitskosten
```

Mana selbst ist kein konkreter Stoff und kein Teilchen. Nach DD-010 ist Mana der nutzbare thaumische Arbeitsfluss aus realen physikalischen Energiepotentialen.

```text
physikalisches Energiepotential
→ gekoppeltes thaumisches Potential
→ Zaubergeometrie koppelt daran
→ magische Arbeit
→ physikalische Quelle entlädt sich + Verluste
```

**Noch offen:**  
Wie exakt das thaumische Potential quantitativ aus physikalischen Energiepotentialen berechnet wird.

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
- Quellkollaps durch zu schnelle Entladung
- Speicherbruch durch Überladung
- Rückkopplung in Fokusmedium, Speicher oder Körper

**Noch offen:**  
Ob zusätzlich abstrakte Misslingen-Modifier für bestimmte Gameplay- oder Simulationssituationen nötig sind.

### OQ-008 — Gibt es ein Mana-Trägermedium?

**Kategorie:** Theorie / Lore / Simulation  
**Status:** Teilweise geklärt durch DD-010

Mana ist kein Stoff und kein Teilchen. Das Standardmodell verwendet stattdessen ein thaumisches Feldpotential: eine Kopplungsschicht, über die reale physikalische Energiepotentiale magisch adressierbar werden.

Das thaumische Feld ist keine zusätzliche Energiequelle, sondern eine Übertragungs- und Kopplungsebene.

**Noch offen:**  
Wie das thaumische Feld in der Simulation konkret parametrisiert wird und ob es räumliche Hintergrundwerte, Materialkopplungen oder nur an Quellen gebundene Potentiale besitzt.

### OQ-012 — Können Zauber rein vokal oder somatisch gewirkt werden?

**Kategorie:** Syntax / Gameplay / Lore  
**Status:** Teilweise geklärt durch DD-007

Rein vokale oder rein somatische Zauber ohne physische visuelle Repräsentation sind nicht vorgesehen.

Vokalisierung und Gestik können aber Trigger, Zielhilfe, Timing oder Laufzeitparameter eines bereits physisch repräsentierten Zaubers sein.

**Noch offen:**  
Wie nah die physische Repräsentation am Zauberer oder Ziel sein muss.

### OQ-013 — Wo befinden sich Zauberbibliotheken?

**Kategorie:** Syntax / Semantik / Gameplay / Lore  
**Status:** Teilweise geklärt durch DD-008

Zauberbibliotheken verwenden ein Hybridmodell:

- Grundprimitive sind systemisch verfügbar.
- Häufige einfache Makros können memorisiert werden.
- Komplexe Makros und Spezialdefinitionen müssen lokal vorhanden, gelernt oder importiert sein.

**Noch offen:**  
Wie Memory-Slots, Bibliotheksversionen und visuelle Importzeichen genau funktionieren.

### OQ-019 — Kann Magie Felder und Wellen direkt erzeugen?

**Kategorie:** Theorie / Simulation  
**Status:** Teilweise geklärt durch DD-009 und DD-010

Standardmagie ist materiegebunden. Direkte substratlose Feld-/Wellenmanipulation ist nicht Teil der Standardmagie.

Das thaumische Feld nach DD-010 ist keine Erlaubnis, beliebige physikalische Felder oder Photonen direkt zu erzeugen. Es ist eine Kopplungsebene für reale Energiepotentiale, die weiterhin bevorzugt auf materielle Zielzustände angewendet werden.

**Noch offen:**  
Ob und wann direkte EM-/Photonen-/Feldmagie als spätere High-Level-Interventionsklasse eingeführt wird.

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

Mana ist als abstrakte magische Arbeitswährung festgelegt. Nach DD-010 ist es der nutzbare thaumische Arbeitsfluss aus realen physikalischen Energiepotentialen.

Offen ist, ob ein Mana exakt einer physikalischen Energiemenge entspricht oder ob Mana-Joule eine interne Simulationsgröße mit Kopplungs- und Effizienzfaktoren bleibt.

### OQ-007 — Wie wird biologische Materie magisch verbrannt?

**Kategorie:** Theorie / Kosten / Simulation  
**Status:** Offen

Lebewesen oder biologische Materie können als Mana-Quelle dienen, indem chemisch gebundene Energie magisch nutzbar gemacht wird.

Nach DD-010 bedeutet das: biologische Energie erzeugt ein bio-thaumisches Potential, das durch Zaubergeometrie angezapft werden kann.

Offen ist, ob dieser Prozess analog zu Stoffwechsel, Verbrennung, Lebensenergieentzug oder direkter chemischer Umwandlung modelliert wird.

### OQ-009 — Wie werden zeitähnliche Effekte formalisiert?

**Kategorie:** Theorie / Simulation  
**Status:** Offen

Zeitumkehrung, Zeitverlangsamung und Zeitbeschleunigung sollen nicht als Bruch von Naturgesetzen behandelt werden, sondern möglicherweise als präzise Manipulation von Zustandsvektoren, Bewegungen oder lokalen Prozessraten.

### OQ-010 — Wie wird visuelle Syntax geparst?

**Kategorie:** Syntax / Semantik / Simulation  
**Status:** Offen

Jeder ausführbare Zauber braucht eine physische visuelle Repräsentation. Offen ist, wie Zeichnungen, Glyphen, Gravuren oder Tattoos formal geparst und in ausführbare Datenstrukturen übersetzt werden.

Nach DD-010 muss diese Repräsentation nicht nur Bedeutung codieren, sondern auch als Zaubergeometrie bzw. thaumische Kopplungsstruktur modellierbar sein.

### OQ-011 — Was ist ein ausführbarer Zauber?

**Kategorie:** Syntax / Simulation / Gameplay  
**Status:** Offen

Ein abstrakt programmierter Zauber muss in eine visuelle Repräsentation übersetzbar sein. Eine visuelle Repräsentation muss in Programm-Logik übersetzbar sein. Offen ist, welche Mindestbedingungen ein Zauber erfüllen muss, um als ausführbar zu gelten.

### OQ-014 — Was ist ein Grundprimitive und was ist importpflichtig?

**Kategorie:** Syntax / Semantik  
**Status:** Offen

Das System muss unterscheiden, welche semantischen Bausteine immer verfügbar sind und welche als Bibliothek, Makro oder Objektdefinition importiert werden müssen.

### OQ-015 — Wie funktionieren Objektdefinitions-Bibliotheken?

**Kategorie:** Semantik / Zielauswahl / Simulation  
**Status:** Offen

Bibliotheken könnten definieren, was ein Objekt wie „Tür“, „Stein“, „Wasser“ oder „Klinge“ bedeutet. Offen ist, wer entscheidet, ob ein konkretes Ziel zu einer solchen Definition passt.

### OQ-016 — Wie lesbar ist ein Zauber für erfahrene Zauberer?

**Kategorie:** Semantik / Gameplay / Visuelle Sprache  
**Status:** Offen

Erfahrene Zauberer sollen aus der visuellen Struktur grob erkennen können, was ein Zauber bewirkt. Offen ist, wie viel ohne Analyse sofort erkennbar ist und was Fachwissen oder Tools erfordert.

### OQ-017 — Wie wird die Materialauflösung der Welt modelliert?

**Kategorie:** Simulation / Materialität  
**Status:** Offen

Die 2D-Welt könnte pixel-/zellbasiert sein, aber Materialien müssen interne Zusammensetzungen, Sub-Pixel-Fraktionen und homogene Makroanzeigen besitzen können.

### OQ-018 — Welche Elemente und Materialien gehören in den ersten Katalog?

**Kategorie:** Semantik / Simulation / Gameplay  
**Status:** Offen

Das System braucht einen funktionalen Element-, Stoff-, Material- und Objektkatalog. Offen ist, welche Einträge für den ersten Prototyp nötig sind.

Nach DD-010 sollten für relevante Materialien zusätzlich thaumische Attribute wie `mana_capacity`, `mana_conductivity`, `mana_leakage` oder `mana_conversion_efficiency` geprüft werden.

### OQ-020 — Wie werden Informationskomponenten bepreist?

**Kategorie:** Kosten / Syntax / Simulation  
**Status:** Offen

Suchen, Sortieren, Ausweichen, Filtern und Erkennen wirken eher wie Informationsverarbeitung als physische Arbeit. Offen ist, ob sie Mana, Komplexität, Rechenkosten oder kognitive Kontrolle verbrauchen.

### OQ-021 — Wie funktioniert hierarchische Aggregation ohne Erhaltungsverlust?

**Kategorie:** Simulation / Performance  
**Status:** Offen

Wärme, Gase, Flüssigkeiten und feine Materialfraktionen sollen lokal präzise, regional aggregiert und global bilanziert werden, ohne Masse oder Energie zu verlieren.

### OQ-022 — Wie werden geschlossene Räume und Container erkannt?

**Kategorie:** Simulation  
**Status:** Offen

Aggregierte Material- oder Gaswerte dürfen nicht willkürlich in geschlossene Räume oder Container eindringen. Die Simulation braucht daher eine Container-/Raumprüfung.

### OQ-023 — Beeinflusst die Größe einer visuellen Zauberrepräsentation Effizienz?

**Kategorie:** Syntax / Kosten / Gameplay  
**Status:** Offen

Kleiner gezeichnete Zauber könnten eine Mana-, Präzisions- oder Stabilitäts-Penalty erhalten, besonders wenn die Repräsentation deutlich kleiner als Ziel oder Wirkungsgröße ist.

Nach DD-010 könnte die Größe einer Repräsentation auch die Kopplungsfläche, Entladerate, Streuung oder Überlastungsgrenze beeinflussen.

### OQ-024 — Wann wird High-Level-Feld-/Wellenmagie eingeführt?

**Kategorie:** Theorie / Simulation / Gameplay  
**Status:** Offen

Direkte Feld-/Wellenmanipulation bleibt als spätere Interventionsklasse möglich. Offen ist, welche Voraussetzungen, Kosten, Risiken und Bibliotheken nötig wären, damit diese Klasse nicht die materiegebundene Standardmagie trivial ersetzt.

### OQ-025 — Wie wird thaumisches Potential quantitativ berechnet?

**Kategorie:** Kosten / Simulation  
**Status:** Offen

DD-010 legt fest, dass physikalische Energiepotentiale ein thaumisches Analog besitzen können.

Offen ist, welche Funktion daraus einen Simulationswert macht:

```text
thaumic_potential = f(physikalische Energie, Materialkopplung, Geometrie, Effizienz, Verluste)
```

Mögliche Einflussgrößen:

- verfügbare physikalische Energie
- Leistungsdichte
- Materialkopplung
- Größe und Präzision der Zaubergeometrie
- Distanz zur Quelle
- Speicherkapazität
- Leckage
- Entladerate
- Rückkopplungsrisiko

### OQ-026 — Welche thaumischen Materialattribute braucht der erste Prototyp?

**Kategorie:** Simulation / Materialität / Gameplay  
**Status:** Offen

Für den ersten 2D-Prototyp muss entschieden werden, welche Mana-relevanten Materialwerte tatsächlich nötig sind.

Kandidaten:

- `mana_capacity`
- `mana_charge`
- `thaumic_potential`
- `mana_conductivity`
- `mana_leakage`
- `mana_conversion_efficiency`
- `mana_discharge_rate`
- `mana_overload_threshold`

### OQ-027 — Wie wirkt Zaubergeometrie als Kopplungsgerät?

**Kategorie:** Syntax / Semantik / Simulation  
**Status:** Offen

Nach DD-010 sind physische Zauberrepräsentationen reale Kopplungsstrukturen.

Offen ist, wie genau Geometrie, Material, Größe, Linienführung, Beschädigung, Symmetrie und Präzision die Kopplung an thaumisches Potential beeinflussen.
