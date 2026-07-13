# Tajan's Thaumaturgie

**Stand:** 2026-07-13, 18:18 Europe/Berlin  
**Status:** Frühe Systemarchitektur / Theorie- und Prototypingphase

**Tajan's Thaumaturgie** ist ein Projekt zur Entwicklung eines granularen, modularen und formal ableitbaren Magie-Systems.

Das Ziel ist kein Katalog hardcodierter Zauber, sondern ein regelbasiertes System, in dem Zauber aus kleineren Bedeutungs-, Wirkungs- und Strukturbausteinen zusammengesetzt werden können — ähnlich wie Programme aus Syntax, Operatoren und Datenstrukturen.

Langfristig soll das System digital simulierbar werden: zuerst als 2D-Proof-of-Concept, später optional als ausgereiftere 3D- oder Spielumgebung.

---

## Leitprinzip

> Ein Zauber darf nicht einfach „existieren“, sondern muss aus kleineren, nachvollziehbaren Komponenten logisch ableitbar sein.

---

## Aktueller Kernstand

```text
Magie = regelgebundene Zustandsmanipulation
        unter Energie-, Massen-, Impuls-, Informations-,
        Präzisions-, Kontroll-, Repräsentations- und Kopplungsbedingungen
```

Ein Zauber ist keine freie Realitätsüberschreibung. Er muss formal gültig, bezahlbar, simulierbar und innerhalb der Spielwelt physisch-visuell repräsentiert sein.

Aktuell festgelegt:

- Zauber müssen aus kleineren Komponenten ableitbar sein.
- Mana ist kein Stoff und kein Teilchen, sondern nutzbarer thaumischer Arbeitsfluss aus realen Energiepotentialen.
- Masse, Energie und Impuls bleiben grundsätzlich erhalten.
- Standardmagie ist materiegebunden und wirkt auf vorhandene Materie bzw. deren Zustände.
- Direkte Feld-/Wellenmagie ist keine Standardmagie, bleibt aber als spätere High-Level-Interventionsklasse offen.
- Jeder ausführbare Zauber benötigt eine physische visuelle Repräsentation, z. B. Schriftrolle, Gravur, Zeichnung, Ritualkreis oder Tattoo.
- Physische Zaubergeometrien sind reale Kopplungsstrukturen für thaumische Potentiale.
- Zaubergeometrie kann additiv, subtraktiv oder hybrid realisiert werden; Material bestimmt die Kopplungsqualität.
- Jeder ausführbare Zauber besitzt mindestens eine Start-Glyphe bzw. einen Aktivierungsknoten.
- Ohne expliziten Start-Modifier gilt: `on_complete_execute_once`.
- Ein LLM/Genie-System kann beim Übersetzen natürlicher Sprache in formale Zauberstruktur helfen, ist aber nicht die Regelautorität.
- Makro-Zauber sind Komfortschichten; ihre Effizienz entsteht emergent aus ihrer Struktur.
- Zauberbibliotheken verwenden ein Hybridmodell aus systemisch verfügbaren Grundprimitiven, memorisierten Makros und lokal/importierten Spezialdefinitionen.

Wichtige Einstiegspunkte:

- `PROJECT_STATUS.md` — aktueller Projektstand und nächste Schritte
- `project/design_decisions.md` — getroffene Designentscheidungen
- `project/open_questions.md` — offene Theorie-, Design- und Simulationsfragen
- `docs/README.md` — Übersicht über die Dokumentationsstruktur
- `docs/reference/glossary.md` — Glossar zentraler Begriffe

---

## Projektziele

1. Aufbau einer konsistenten Magie-Ontologie.
2. Entwicklung einer formalen Zauber-Syntax.
3. Definition von Modifiern, Operatoren, Zielauswahl, Dauer, Reichweite und Bedingungen.
4. Modellierung von Energie, Kosten, Grenzen und Fehlerfällen.
5. Entwicklung einer manipulierbaren materiellen Welt als Simulationsgrundlage.
6. Vorbereitung einer digitalen Simulation, zunächst in 2D, später optional in 3D.
7. Prüfung, ob ein LLM-gestützter Zauber-Compiler als Interface zwischen natürlicher Sprache und formaler Zaubersyntax dienen kann.
8. Entwicklung eines Spell Editors, der visuelle Zauberstruktur, textuelle Syntax und Genie-Interface synchronisiert.

---

## Projektstruktur

```text
tajans-thaumaturgie/
├─ README.md
├─ PROJECT_STATUS.md
├─ project/
│  ├─ design_decisions.md
│  ├─ open_questions.md
│  └─ system_tensions.md
├─ docs/
│  ├─ README.md
│  ├─ foundations/
│  ├─ spell_system/
│  ├─ mana_and_energy/
│  ├─ representation_and_material_coupling/
│  ├─ world_model/
│  ├─ implementation/
│  └─ reference/
├─ notes/
│  ├─ raw/
│  ├─ processed/
│  └─ archive/
├─ prototype/
│  └─ 2d/
└─ issues/
```

---

## Arbeitsweise

Das Projekt unterscheidet konsequent zwischen:

- **Theorie:** Was ist im Magie-System grundsätzlich wahr?
- **Regelmechanik:** Wie werden Zauber konstruiert und begrenzt?
- **Simulation:** Wie lässt sich das System technisch abbilden?
- **Gameplay:** Wie wird daraus eine interessante spielbare Erfahrung?
- **Lore:** Wie wird das System innerhalb einer Welt gedeutet?

Neue Ideen werden nach Möglichkeit in diese Kategorien einsortiert:

- **Festgelegt**
- **Hypothese**
- **Offene Frage**
- **Widerspruch**
- **Feature**
- **Begriff**
- **Beispiel**

---

## Aktueller nächster sinnvoller Einstieg

Issue #2 wird aktuell schrittweise bearbeitet.

Bereits dokumentiert:

```text
Activation & Termination Model
= Wie wird ein Zauber scharfgeschaltet, gestartet, gehalten und beendet?
```

Nächster granularer Schritt:

```text
Effect Node und Target Node definieren.
```

Diese Entscheidung klärt, was die kleinste Einheit einer Wirkung ist, wie Zielauswahl formal an Wirkung gekoppelt wird und wie daraus später ein simulierbarer Eingriff in WorldCells, Materialien oder Objekte entsteht.
