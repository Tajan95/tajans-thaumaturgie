# Clustered Notes — 2026-07-07

Dieses Dokument verarbeitet die Rohnotizen vom 07.07.2026 und gleicht sie gegen den bestehenden Projektstand ab.

---

## 1. Vokalisierte und somatische Zauber

### Rohfrage

Können Zauber rein vokalisiert oder somatisch gewirkt werden, oder brauchen sie immer eine physische Komponente?

### Abgleich mit bisherigem Stand

Durch DD-007 ist bereits festgelegt:

> Jeder ausführbare Zauber benötigt eine physische, visuelle Repräsentation.

Daraus folgt:

- Vokalisierung kann einen Zauber triggern.
- Gestik kann einen Zauber triggern, ausrichten oder parametrisieren.
- Vokalisierung/Gestik ersetzt aber nicht die notwendige physische visuelle Repräsentation.

### Bereinigte Arbeitsregel

```text
Vokalisierung/Gestik = Auslöser oder Parameterinput
Physische visuelle Repräsentation = notwendige Zauberstruktur
```

### Kategorie

- **Festgelegt:** Kein vollständig rein vokaler Zauber ohne physische Repräsentation.
- **Hypothese:** Stimme und Gestik können Trigger, Auswahlhilfe oder Laufzeitparameter sein.
- **Offene Frage:** Wie nah muss die physische Repräsentation am Zauberer oder Ziel sein?

---

## 2. Zauberbibliotheken, Makros und Imports

### Neue Kernaussage

Da Zauber sehr komplex werden können, braucht das System Bibliotheken bzw. Makro-Komponenten, ähnlich wie Funktionen-Libraries beim Programmieren.

Eine Bibliothek kann enthalten:

- Makro-Zauber
- Objektdefinitionen
- Materialdefinitionen
- Standardstrukturen
- Zielauswahl-Patterns
- Sicherheitslogik
- Transformationsroutinen
- Symbol-/Glyphenkomponenten

### Problem

Ein Zauber, der eine Bibliothek referenziert, muss diese Bibliothek zur Laufzeit oder spätestens zur Kompilierung erreichen können.

### Zentrale Frage

Sind Bibliotheken global verfügbar oder müssen sie lokal in der Spielwelt mitgeführt/gespeichert werden?

### Mögliche Modelle

| Modell | Beschreibung | Vorteil | Nachteil |
|---|---|---|---|
| Globale Bibliothek | Alle bekannten Definitionen sind überall abrufbar. | bequem, spielerfreundlich | schwächt physische Weltlogik |
| Lokale Bibliothek | Bücher, Schriftrollen, Artefakte oder Tattoos müssen vorhanden sein. | konsistent mit DD-007, gutes Gameplay | mehr Verwaltung |
| Gelernte Bibliothek | Zauberer kann Definitionen internalisieren. | Fortschritt/Skill möglich | kollidiert evtl. mit physischer Repräsentationspflicht |
| Hybrid | Standardprimitive global/intern, komplexe Makros lokal/importiert. | flexibel | braucht klare Grenze |

### Vorläufige Empfehlung

Ein Hybridmodell wirkt am konsistentesten:

```text
Grundprimitive: immer verfügbar / im Zaubersystem selbst definiert
Makros und komplexe Bibliotheken: lokal gespeichert oder gelernt/importiert
```

### Kategorie

- **Feature:** Zauberbibliotheken / Imports / Makros.
- **Begriff:** Bibliothek, Import, Referenz, Objektdefinition, Makro.
- **Offene Frage:** Sind Bibliotheken global, lokal, gelernt oder hybrid?
- **Offene Frage:** Was passiert, wenn eine Bibliothek während der Laufzeit nicht mehr zugreifbar ist?

---

## 3. Objektdefinitions-Bibliotheken

### Neue Kernaussage

Bibliotheken könnten nicht nur Zauberbausteine speichern, sondern auch Definitionen physischer Objekte.

Nutzen:

Ein Zauber muss nicht jedes Mal vollständig definieren, was z. B. „Tür“, „Stein“, „Wasser“, „Eisen“, „Lebewesen“ oder „Klinge“ bedeutet.

Stattdessen kann er auf eine Objekt- oder Materialdefinition verweisen:

```text
Target := object.type("door")
```

### Kategorie

- **Feature:** Objekt-/Materialbibliotheken.
- **Begriff:** Objekttyp, Materialklasse, Zieldefinition.
- **Offene Frage:** Wie granular müssen Objektdefinitionen sein?
- **Offene Frage:** Wer oder was entscheidet, ob ein konkretes Ziel unter eine Definition fällt?

### Systemischer Nutzen

Das vermeidet übermäßige Definitionsarbeit und erlaubt gleichzeitig eine saubere Zielauswahl.

---

## 4. Visuelle Lesbarkeit von Zaubern

### Kernaussage

Die Zaubersprache soll so klar visuell strukturiert sein, dass erfahrene Zauberer grob erkennen können, was ein Zauber bewirkt, ohne eine direkte Beschreibung zu lesen.

### Abgleich mit bisherigem Stand

Dies passt direkt zu `docs/13_visual_spell_language.md` und DD-007.

### Neue Präzisierung

Die visuelle Repräsentation soll nicht nur hübsche Ästhetik sein, sondern semantisch lesbar.

Ein erfahrener Zauberer sollte erkennen können:

- Zielklasse
- Wirkungsart
- räumliche Struktur
- zentrale Modifier
- Energie-/Bindungsstruktur
- mögliche Gefahren oder Instabilität

### Kategorie

- **Feature:** Semantisch lesbare visuelle Zaubersprache.
- **Hypothese:** Lesbarkeit kann als Skill/Expertise modelliert werden.
- **Offene Frage:** Wie viel Information ist visuell direkt erkennbar und wie viel braucht Analyse/Inspektion?

---

## 5. Redundanzen

| Neue Notiz | Bereits abgedeckt durch |
|---|---|
| Müssen Zauber physisch sein? | DD-007, `docs/13_visual_spell_language.md` |
| Makros sind praktisch nötig | DD-006, `docs/08_working_model_from_initial_notes.md` |
| Klare visuelle Repräsentation | DD-007, `docs/13_visual_spell_language.md` |

## 6. Neue relevante Inhalte

1. Bibliotheken können wie Funktions-Libraries importiert/referenziert werden.
2. Unklar ist, ob Bibliotheken global oder lokal verfügbar sind.
3. Objektdefinitions-Bibliotheken könnten Zielauswahl und Objektklassifikation erleichtern.
4. Visuelle Zauber sollten semantisch lesbar sein, nicht nur dekorativ.

## 7. Nächste Entscheidungen

1. Lokal, global oder hybrid: Wo befinden sich Zauberbibliotheken?
2. Was gilt als Grundprimitive und was als importpflichtiges Makro?
3. Wie funktionieren Objektdefinitionen für Zielauswahl?
4. Können gelernte Bibliotheken ohne physisches Medium genutzt werden?
5. Ist Zauberanalyse ein eigener Skill oder Teil allgemeiner Magiekompetenz?
