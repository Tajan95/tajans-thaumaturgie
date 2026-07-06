# Clustered Notes — 2026-07-06

Dieses Dokument ist die erste bereinigte Triage der Rohnotizen vom 06.07.2026.

Ziel ist noch nicht, endgültige Regeln festzulegen, sondern Redundanzen zu kürzen, Themen zu clustern und offene Systementscheidungen sichtbar zu machen.

---

## 1. Formales Ziel des Magie-Systems

### Bereinigte Kernaussage

Magie soll so generalisiert werden, dass beliebige Zauber nicht als feste Spezialfälle existieren, sondern als formale Kombination kleinerer Komponenten ausdrückbar sind.

Langfristiges Ziel:

```text
Zauber = Ziel + Wirkung + Struktur + Modifier + Energie/Kosten + Bedingung + Fehlerlogik
```

### Kategorie

- **Festgelegt:** Zauber sollen aus kleineren Komponenten ableitbar sein.
- **Begriff:** Zauberformel, Zaubersyntax, semantische Komponente.
- **Offene Frage:** Ist diese Formel eher mathematische Gleichung, Programmsyntax, Graph oder semantischer Baukasten?

---

## 2. Mana, Energie und biologischer Aufwand

### Bereinigte Kernaussage

Mana wird nicht primär als beliebige Fantasy-Ressource gedacht, sondern als Interpretation von Aufwand, Energie, Belastung und Kontrollleistung.

Mögliche Quellen oder Modelle:

1. **Biologisches Mana:** Körperlicher Aufwand, ggf. ATP-nah gedacht.
2. **Kognitives Mana:** geistige Belastung bei informations- oder kontrollintensiven Zaubern.
3. **Externe Mana-Speicher:** Kristalle, Artefakte oder andere Speichermedien.
4. **Gemeinsames Mana:** Mehrere Magier teilen sich die Last eines Zaubers.

### Kategorie

- **Hypothese:** Mana kann als verallgemeinerter Arbeits-/Kontrollaufwand verstanden werden.
- **Hypothese:** ATP könnte als biologische Untergrenze oder Analogie für körperliche Magie dienen.
- **Feature:** Mana-Speicher, Mana-Verteilung zwischen mehreren Zauberern, externe Energiequellen.
- **Offene Frage:** Ist Mana physikalische Energie, biologische Leistungsfähigkeit, magische Sonderenergie oder abstrakter Kostenwert?

### Redundanz gekürzt

Die Notizen zu ATP, körperlicher Belastung, kognitiver Belastung, gemeinsamer Steinhebung und externen Kristallen wurden zu einem gemeinsamen Kostenmodell-Cluster zusammengeführt.

---

## 3. Körperliche und kognitive Belastungsverteilung

### Bereinigte Kernaussage

Magische Manipulation belastet den Magier analog zur entsprechenden physischen oder kognitiven Leistung.

Beispiele:

- Einen schweren Stein magisch zu heben ist ungefähr so anstrengend wie eine äquivalente physische Hebeleistung.
- Mehrere Zauberer können die Last teilen.
- Mentale Zauber könnten nicht einen einzelnen Körperteil, sondern das gesamte Verständnis / Bewusstsein / kognitive System belasten.

### Kategorie

- **Hypothese:** Physische Magie erzeugt körperanalog verteilte Belastung.
- **Hypothese:** Kognitive Magie erzeugt systemische mentale Belastung.
- **Beispiel:** Gemeinsames Heben eines schweren Steins.
- **Offene Frage:** Was genau ist die Einheit kognitiver Belastung?

### Systemischer Nutzen

Dieses Modell verhindert Allmacht, weil Magie nicht kostenlos wirkt. Es macht Zaubern eher zu einer erweiterten Form von Arbeit als zu willkürlicher Realitätsüberschreibung.

---

## 4. Action at a Distance und Distanzkosten

### Bereinigte Kernaussage

Fernmanipulation ist nicht kostenlos. Je weiter entfernt ein Ziel ist, desto höher wird Aufwand, Kontrollverlust oder Fehlerwahrscheinlichkeit.

Arbeitsbild:

```text
Fernwirkung ≈ physische Manipulation über einen Hebel gleicher Länge
```

### Kategorie

- **Hypothese:** Distanz erhöht magische Kosten oder reduziert Präzision.
- **Begriff:** Distanzfaktor, Fernwirkungsaufwand.
- **Offene Frage:** Ist der Distanzfaktor linear, quadratisch, abhängig vom Medium oder abhängig von Zielbindung?

---

## 5. Zauberstäbe, Fokusmedien und magische Linsen

### Bereinigte Kernaussage

Zauberstäbe sind keine absolute Voraussetzung für Magie, aber sie wirken als Fokus- oder Linsensystem.

Funktionen:

- höhere Präzision
- besserer Wirkungsgrad
- geringerer Energieverlust
- stabilere Zielauswahl
- Integration externer Mana-Speicher, z. B. Kristalle

### Kategorie

- **Hypothese:** Zauberstäbe erhöhen Effizienz und Präzision.
- **Hypothese:** Ohne Zauberstab ist Magie möglich, aber ineffizienter.
- **Feature:** Zauberstab mit austauschbarem oder wiederaufladbarem Mana-Speicher.
- **Offene Frage:** Ist der Zauberstab eher optische Linse, Werkzeuggriff, Antenne, Parser, Verstärker oder Sicherheitsvorrichtung?

### Starke Designannahme

Maximal erfahrenes Zaubern ohne Zauberstab bleibt schwächer oder ineffizienter als maximal erfahrenes Zaubern mit geeignetem Zauberstab.

**Status:** Noch bestätigen.

---

## 6. Training, Effizienz und Zauber-Atrophie

### Bereinigte Kernaussage

Zaubern ist trainierbar. Übung verbessert Geschwindigkeit, Effizienz, Präzision und Belastbarkeit. Mangelnde Nutzung führt zu Rückbildung.

### Kategorie

- **Hypothese:** Zauberfähigkeit verhält sich teilweise wie Muskeltraining und teilweise wie kognitive Routine.
- **Feature:** Skill-Progression, Effizienzsteigerung, Zauber-Atrophie.
- **Offene Frage:** Welche Komponenten verbessern sich durch Training: Energieoutput, Präzision, mentale Syntax, Fehlertoleranz oder alles getrennt?

---

## 7. Thermodynamik, Erhaltungssätze und Mindestkosten

### Bereinigte Kernaussage

Magie unterliegt Erhaltungssätzen. Energie, Masse und Impuls werden nicht aus dem Nichts erschaffen oder vernichtet, sondern transformiert oder umverteilt.

Wichtige Annahmen:

- Energieerhaltung gilt.
- Massenerhaltung gilt, sofern keine explizite Umwandlung modelliert wird.
- Impulserhaltung gilt.
- Jeder Prozess ist verlustbehaftet.
- Magische Arbeit erzeugt Abwärme.
- Phasenübergänge und chemische Transformationen kosten mindestens ihre physikalische Enthalpie in Joule bzw. ein Mana-Äquivalent davon.

Beispiele:

- Wasser zu Eis: mindestens Energie entsprechend der Temperaturänderung und Kristallisationsenthalpie.
- Eisenoxid zu Eisen + Sauerstoff: mindestens Aufwand entsprechend der chemischen Umwandlung.

### Kategorie

- **Festgelegt:** Magie soll nicht gegen Thermodynamik arbeiten, sondern innerhalb eines erweiterten Kostenmodells.
- **Hypothese:** Mana könnte ein Äquivalent zu Energie sein, aber mit eigenen Speicher- und Transferregeln.
- **Begriff:** Mana-Joule, magische Arbeit, Abwärme, Enthalpiekosten.
- **Offene Frage:** Gibt es zusätzlich zu physikalischer Abwärme auch „Mana-Abwärme“?

### Systemischer Nutzen

Dieses Cluster ist ein starker Kern des Systems. Es macht Magie berechenbar, begrenzt und simulierbar.

---

## 8. Abwärme und Nebenprodukte

### Bereinigte Kernaussage

Abwärme wird standardmäßig auf einfache Weise radial abgeführt. Jede aktive Kontrolle oder Lenkung von Abwärme ist ein zusätzlicher Prozess mit eigenen Kosten und Verlusten.

Arbeitsregel:

```text
Nicht kontrollierte Abwärme → radial/faul verteilt
Kontrollierte Abwärme → zusätzlicher Zauberprozess mit zusätzlichen Kosten
```

### Kategorie

- **Hypothese:** Abwärme folgt ohne Zusatzkontrolle einem einfachen radialen Abflussmodell.
- **Feature:** Wärmelenkung, Wärmebündelung, magische Wärmepumpe.
- **Offene Frage:** Wird Abwärme rein physikalisch simuliert oder als abstrakter Risikowert?

---

## 9. Rituale, gespeicherte Zauber und Artefakte

### Bereinigte Kernaussage

Rituale und Artefakte können gespeicherte Energie und/oder vorformulierte Zauber enthalten.

Funktionen:

- Mana speichern
- vorbereitete Zaubersyntax speichern
- Zauber nach Aktivierung ausführen
- Zauber mit verfügbarem Mana aufrechterhalten

### Kategorie

- **Hypothese:** Rituale sind vorbereitete Zauberprozesse mit gespeicherter Struktur und/oder Energie.
- **Feature:** Artefakte, Trigger-Zauber, permanente oder semi-permanente Effekte.
- **Begriff:** Ritual, Artefakt, gespeicherter Zauber, Aktivierung.
- **Offene Frage:** Speichert ein Artefakt Energie, Syntax, Zielbindung oder alles getrennt?

---

## 10. LLM als Zauber-Compiler / Natural-Language Interface

### Bereinigte Kernaussage

Das Magiesystem selbst soll hart und regelgebunden implementiert werden. Die Übersetzung natürlichsprachiger Zauberbeschreibungen in konkrete Zauberbausteine könnte durch ein LLM erfolgen.

Architekturidee:

```text
Natürliche Sprache → LLM-Interpretation → semantische Zauberbausteine → Regelengine → Simulation
```

Das LLM erzeugt also nicht die Realität direkt, sondern schlägt eine gültige Kombination aus erlaubten Bausteinen vor.

### Kategorie

- **Feature:** LLM-gestützter Zauber-Compiler.
- **Feature:** Ästhetische Verschlüsselung durch kryptische Zeichen.
- **Hypothese:** Eine Bibliothek kleinster semantischer Komponenten ist notwendig.
- **Offene Frage:** Wie wird verhindert, dass das LLM ungültige, zu mächtige oder unprüfbare Zauber erzeugt?

### Wichtiges Architekturprinzip

Die Regelengine muss autoritativ bleiben. Das LLM darf interpretieren, aber nicht die Grundregeln brechen.

---

## 11. Genie-Slider / Implizite Ergänzung durch KI

### Bereinigte Kernaussage

Ein „Genie-Slider“ könnte steuern, wie stark die KI unausgesprochene Aspekte eines Zaubers ergänzt.

Mögliche Stufen:

| Stufe | Verhalten |
|---|---|
| Minimal | Der Zauber macht nur exakt, was beschrieben wurde. |
| Moderat | Offensichtliche Lücken werden ergänzt. |
| Stark | Popkulturelle oder intuitive Bedeutung wird aktiv interpretiert. |

### Kategorie

- **Feature:** Genie-Slider als Interpretationsgrad.
- **Gameplay:** Unterschied zwischen präziser Zaubersyntax und komfortabler Alltagsbeschreibung.
- **Offene Frage:** Ist der Genie-Slider ein reines UI-/Gameplay-Feature oder Teil der Magie-Lore?

### Risiko

Je stärker der Genie-Slider, desto größer die Gefahr, dass das System von formaler Magie zu Wunschmagie abrutscht.

---

## 12. Visuelle Zaubersprache

### Bereinigte Kernaussage

Die Zaubersprache soll visuell darstellbar sein, ähnlich inspiriert von Systemen wie Witch Hat Atelier, aber mit eigenen kleinsten semantischen Komponenten.

### Kategorie

- **Feature:** Visuelle Zeichen für semantische Zauberkomponenten.
- **Begriff:** Zeichen, Glyph, Symbol, semantisches Primitive.
- **Offene Frage:** Sind Zeichen nur Darstellung, oder haben sie regelmechanische Funktion?

---

## 13. Physik-Engine, Objekt-Erzeugung und Interagierbarkeit

### Bereinigte Kernaussage

Die Macht eines Zaubers hängt davon ab, welche physikalischen Eigenschaften die Engine überhaupt modelliert.

Wenn ein Zauber ein physisches Objekt erzeugt, z. B. ein Mesh, bestimmen die simulierten Physikregeln, wie dieses Objekt interagiert.

### Kategorie

- **Hypothese:** Je granularer die Engine, desto ausdrucksstärker die Zauber.
- **Feature:** Erzeugung physikalischer Objekte durch Zauber.
- **Offene Frage:** Soll Objekt-Erzeugung echte Materietransformation, Beschwörung, Projektion oder Mesh-Spawn mit Kostenmodell sein?

---

## 14. Prototyping: 2D vor 3D

### Bereinigte Kernaussage

Ein erster Proof of Concept sollte in 2D beginnen, weil 3D deutlich komplexer ist.

Möglicher Minimalprototyp:

- 2D-Raum oder Grid
- Entitäten mit Position, Masse, Material, Temperatur
- einfache Wirkungen wie Bewegen, Erwärmen, Abkühlen, Binden, Trennen
- Zielauswahl über Punkt, Radius oder Objekt
- Kostenberechnung
- Abwärme oder Verlustmodell

### Kategorie

- **Festgelegt:** 2D eignet sich als erster Prototyp besser als 3D.
- **Feature:** 2D-Proof-of-Concept.
- **Offene Frage:** Welche Engine eignet sich für spätere Steam-Tauglichkeit und langfristige 3D-Erweiterbarkeit?

---

## 15. Custom Spells vs. Bibliothekskomponenten

### Bereinigte Kernaussage

Zauber sollen sowohl granular selbst konstruierbar als auch aus vorgefertigten Komponenten oder Makros zusammensetzbar sein.

Trade-off:

| Ansatz | Vorteil | Nachteil |
|---|---|---|
| Granularer Custom Spell | effizient, präzise, flexibel | langsam, komplex, fehleranfällig |
| Vorgefertigtes Makro | schnell, komfortabel | weniger effizient, weniger präzise, evtl. teurer |

### Kategorie

- **Feature:** Zauberbibliothek / Makros / höhere Abstraktionsebene.
- **Gameplay:** Komfort gegen Effizienz.
- **Hypothese:** Vorgefertigte Komponenten sind weniger Mana-effizient, aber schneller nutzbar.
- **Offene Frage:** Ist Ineffizienz eine magische Eigenschaft oder ein Balancing-Mechanismus?

---

## 16. Redundanzen, die zusammengeführt wurden

1. **ATP, Mana, körperliche Belastung, kognitive Belastung, externe Kristalle** → Cluster „Mana, Energie und biologischer Aufwand“.
2. **Thermodynamik, Enthalpie, Conservation of Energy/Mass/Momentum, Waste Heat** → Cluster „Thermodynamik, Erhaltungssätze und Mindestkosten“.
3. **Zauberstäbe als Linse, geringere Präzision ohne Stab, Mana-Kristalle im Stab** → Cluster „Fokusmedien und magische Linsen“.
4. **LLM, Programming as Incantations, Natural-Language Spell Generation, Genie-Slider** → Cluster „LLM als Zauber-Compiler“ und „Genie-Slider“.
5. **2D-Prototyp, Engine-Wahl, Steam-Ziel** → Cluster „Prototyping: 2D vor 3D“.

---

## 17. Mögliche Widersprüche oder Spannungspunkte

### W-001 — Mana als ATP vs. Mana als universelles Energieäquivalent

ATP ist biologisch lokal und körpergebunden. Ein universelles Mana-Joule-Modell wäre dagegen allgemeiner und könnte auch Kristalle, Rituale und Artefakte erklären.

**Mögliche Auflösung:** ATP ist nur eine biologische Mana-Quelle, nicht Mana selbst.

### W-002 — „Jeder beliebige Zauber“ vs. strenge Erhaltungsgesetze

Wenn Magie Erhaltungssätzen folgt, ist nicht jeder denkbare Zauber möglich. Möglich ist nur jeder Zauber, der aus erlaubten Transformationen, ausreichender Energie und gültiger Zielauswahl konstruiert werden kann.

**Mögliche Auflösung:** „Beliebig“ bedeutet kombinatorisch offen, nicht physikalisch unbegrenzt.

### W-003 — LLM ergänzt implizite Bedeutung vs. formale Präzision

Ein Genie-Slider kann Komfort erzeugen, aber auch die formale Strenge untergraben.

**Mögliche Auflösung:** LLM-Vorschläge müssen durch eine harte Regelengine validiert werden.

### W-004 — Makros sind ineffizient vs. optimierte Bibliothekszauber

Vorgefertigte Zauber könnten ineffizient sein, wenn sie generisch sind. Sie könnten aber auch effizienter sein, wenn sie von Experten optimiert wurden.

**Mögliche Auflösung:** Standard-Makros sind robust und schnell, aber nicht immer optimal. Experten-Makros können effizient sein, sind aber schwerer zu erstellen oder teurer zu erlernen.

---

## 18. Nächste notwendige Entscheidungen

1. Was ist Mana: Energie, biologischer Aufwand, Kontrollaufwand, Informationsarbeit oder ein Hybrid?
2. Gilt Thermodynamik absolut, oder darf Magie lokale Ausnahmen erzeugen, solange Kosten bezahlt werden?
3. Sind Zauberstäbe nur effizienter oder für bestimmte Zauberklassen praktisch notwendig?
4. Gibt es eine kanonische Grundeinheit für Kosten, z. B. Joule, Mana-Joule oder abstrakte Mana-Punkte?
5. Ist ein Zauber intern eine Sequenz, ein Graph oder ein Komponentenobjekt?
6. Sind visuelle Zeichen nur UI/Ästhetik oder regelmechanisch notwendig?
7. Ist der Genie-Slider Teil der Spielmechanik oder nur ein Entwicklungs-/Editorwerkzeug?
8. Welche minimale 2D-Simulation testet den Kern des Systems am besten?
