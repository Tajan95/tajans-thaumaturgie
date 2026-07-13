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

---

## Teilweise geklärte Fragen

### OQ-001 — Was ist Magie ontologisch?

**Kategorie:** Theorie  
**Status:** Teilweise geklärt durch DD-003, DD-004, DD-009 und DD-010

```text
Magie = regelgebundene Zustandsmanipulation
        unter Erhaltungssätzen und Mana-/Arbeitskosten
```

Mana ist kein Stoff oder Teilchen, sondern nutzbarer thaumischer Arbeitsfluss aus realen physikalischen Energiepotentialen.

**Noch offen:**  
Wie das thaumische Potential quantitativ berechnet wird.

### OQ-002 — Welche Form hat ein Zauber intern?

**Kategorie:** Syntax / Simulation  
**Status:** Teilweise geklärt durch DD-012 bis DD-015

Geklärt:

```text
ActivationNode
→ TargetNode(s)
→ EffectNode(s)
→ StateChangeRequest(s)
```

- TargetNodes erzeugen typisierte TargetSets.
- Primitive EffectNodes enthalten eine atomare Zustandsoperation.
- Mehrere Wirkungen können parallel oder sequenziell verbunden werden.
- Makros expandieren zu primitiven Teilgraphen.

Aktuelle starke Hypothese:

```text
Interne Zauberform = Komponentenobjekt + typisierter gerichteter Wirkungsgraph
```

**Noch offen:**  
Ob dieses Hybridmodell endgültig festgelegt wird und welche weiteren Node-Familien die minimale SpellIR benötigt.

### OQ-003 — Wie wird Zielauswahl definiert?

**Kategorie:** Semantik / Simulation  
**Status:** Teilweise geklärt durch DD-013

TargetNodes definieren Selektor, Anker, Suchraum, Filter, Granularität, Bindungsmodus, Aktualisierung, Zugriffsvoraussetzungen und Fehlerverhalten.

Vorläufige Referenzen:

```text
ObjectRef
CellRef
CellRegionRef
SurfaceRef
MaterialFractionRef
PointRef
BiologicalRegionRef
```

**Noch offen:**  
Welche Referenz-, Filter- und Selektortypen Grundprimitive sind und welche Wissen oder Bibliotheken benötigen.

### OQ-004 — Wie entstehen Fehlerfälle?

**Kategorie:** Kosten / Simulation / Gameplay  
**Status:** Teilweise geklärt

Fehler entstehen bevorzugt emergent aus:

- ungültiger Syntax oder Portverbindung
- semantischem Widerspruch
- leerer oder gebrochener Zielbindung
- unzureichender Energiequelle
- fehlender Bibliothek oder Repräsentation
- nicht abgeführter Wärme oder Nebenprodukten
- Quellkollaps, Speicherbruch oder Rückkopplung
- beschädigter Start-Glyphe
- fehlender Terminationslogik
- widersprüchlichen parallelen StateChangeRequests

**Noch offen:**  
Ob zusätzliche abstrakte Misslingen-Modifier benötigt werden.

### OQ-008 — Gibt es ein Mana-Trägermedium?

**Kategorie:** Theorie / Lore / Simulation  
**Status:** Teilweise geklärt durch DD-010

Das Standardmodell verwendet ein thaumisches Feldpotential als Kopplungsebene für reale Energiepotentiale, nicht als zusätzliche Energiequelle.

**Noch offen:**  
Wie dieses Feld räumlich und quantitativ simuliert wird.

### OQ-011 — Was ist ein ausführbarer Zauber?

**Kategorie:** Syntax / Simulation / Gameplay  
**Status:** Teilweise geklärt durch DD-007 und DD-012 bis DD-015

Ein ausführbarer Zauber benötigt mindestens:

```text
ActivationNode
+ TargetNode
+ EffectNode
+ Ressourcenmodell
+ physische Repräsentation
+ gültige Fehlerlogik
```

**Noch offen:**  
Welche zusätzlichen Mindestknoten bei Transfers, Nebenprodukten, Bibliotheken und kontinuierlicher Ausführung zwingend sind.

### OQ-012 — Können Zauber rein vokal oder somatisch gewirkt werden?

**Kategorie:** Syntax / Gameplay / Lore  
**Status:** Teilweise geklärt durch DD-007 und DD-012

Rein vokale oder somatische Zauber ohne physische Repräsentation sind nicht vorgesehen. Stimme und Gestik können Trigger oder Laufzeitinput sein.

**Noch offen:**  
Wie nah sich die physische Repräsentation an Zauberer oder Ziel befinden muss.

### OQ-013 — Wo befinden sich Zauberbibliotheken?

**Kategorie:** Syntax / Semantik / Gameplay / Lore  
**Status:** Teilweise geklärt durch DD-008

Grundprimitive sind systemisch verfügbar; einfache Makros können memorisiert, komplexe Definitionen lokal gelernt oder importiert werden.

**Noch offen:**  
Memory-Slots, Versionen und visuelle Importzeichen.

### OQ-017 — Wie wird die Materialauflösung der Welt modelliert?

**Kategorie:** Simulation / Materialität  
**Status:** Teilweise geklärt durch DD-016 bis DD-019

Geklärt:

- WorldCells sind räumliche Einheiten, keine Mindestmassen.
- Sub-Zell-Massen und Stofffraktionen bleiben erhalten.
- Starre Objekte verwenden Sub-Zell-Positionen.
- Flussmaterialien verwenden Zelltransfermodelle.
- Größen bleiben SI-kompatibel und intern quantisierbar.

**Noch offen:**  
Konkrete Zellgröße, effektive Ebenentiefe, Mengenquanten, CompositionPool und adaptive Auflösungswechsel.

### OQ-019 — Kann Magie Felder und Wellen direkt erzeugen?

**Kategorie:** Theorie / Simulation  
**Status:** Teilweise geklärt durch DD-009 und DD-010

Direkte substratlose Feld-/Wellenmanipulation ist keine Standardmagie.

**Noch offen:**  
Ob und wann sie als High-Level-Interventionsklasse eingeführt wird.

### OQ-020 — Wie werden Informationskomponenten bepreist?

**Kategorie:** Kosten / Syntax / Simulation  
**Status:** Teilweise geklärt durch DD-013 und DD-015

Query-, Analysis-, Filter- und Live-Bindungsoperationen verursachen Steuerarbeit. Kostenfaktoren sind unter anderem Suchraum, Auflösung, Aktualisierungsrate, Zielzahl, Unsicherheit und Bibliothekswissen.

**Noch offen:**  
Die konkrete Kostenfunktion und Grenzen gegen allwissende Abfragen.

---

## Offene Fragen

### OQ-005 — Was begrenzt Rekursion und Kombinatorik?

**Kategorie:** Theorie / Syntax / Kosten  
**Status:** Offen

Wie werden Selbstreferenz, rekursive Makros, unendliche Schleifen und exponentielle Graphauswertung begrenzt?

### OQ-006 — Gibt es eine direkte Mana-Joule-Umrechnung?

**Kategorie:** Kosten / Simulation  
**Status:** Offen

Ist Mana exakt eine Energiemenge in Joule oder bleibt es eine interne Größe aus nutzbarer Arbeit, Kopplung, Effizienz und Verlusten?

### OQ-007 — Wie wird biologische Materie als Energiequelle genutzt?

**Kategorie:** Theorie / Kosten / Simulation  
**Status:** Offen

Wie werden Stoffwechsel, chemische Entladung, Erschöpfung, Gewebeschaden und Wärme bilanziert?

### OQ-009 — Wie werden zeitähnliche Effekte formalisiert?

**Kategorie:** Theorie / Simulation  
**Status:** Offen

Können zeitähnliche Effekte als Manipulation von Zustandsvektoren, Bewegungen oder lokalen Prozessraten konstruiert werden?

### OQ-010 — Wie wird visuelle Syntax geparst?

**Kategorie:** Syntax / Semantik / Simulation  
**Status:** Offen

Wie werden physische Glyphen in Activation-, Target-, Effect-, Ressourcen- und Sicherheitsknoten übersetzt, und wie beeinflusst ihre reale Geometrie zugleich die thaumische Kopplung?

### OQ-014 — Was ist ein Grundprimitive und was ist importpflichtig?

**Kategorie:** Syntax / Semantik  
**Status:** Offen

Welche Target-, Effect-, Query- und Control-Nodes sind immer verfügbar?

### OQ-015 — Wie funktionieren Objektdefinitions-Bibliotheken?

**Kategorie:** Semantik / Zielauswahl / Simulation  
**Status:** Offen

Wie wird entschieden, ob ein konkretes Objekt einer Definition wie Tür, Stein, Tier oder Organ entspricht?

### OQ-016 — Wie lesbar ist ein Zauber für erfahrene Zauberer?

**Kategorie:** Semantik / Gameplay / Visuelle Sprache  
**Status:** Offen

Welche Node-Typen, Zielbindungen, Ressourcenpfade und Risiken sind direkt visuell erkennbar?

### OQ-018 — Welche Elemente und Materialien gehören in den ersten Katalog?

**Kategorie:** Semantik / Simulation / Gameplay  
**Status:** Offen

Welche Stoffe, Materialien und Attribute werden für den ersten thermischen, mechanischen und kompositionellen Prototyp benötigt?

### OQ-021 — Wie funktioniert hierarchische Aggregation ohne Erhaltungsverlust?

**Kategorie:** Simulation / Performance  
**Status:** Offen

Wie werden lokale Werte regional aggregiert und später wieder verfeinert, ohne Masse, Energie, Impuls oder Zusammensetzung zu verlieren?

### OQ-022 — Wie werden geschlossene Räume und Container erkannt?

**Kategorie:** Simulation  
**Status:** Offen

Wie verhindert die Simulation, dass aggregierte Gase, Flüssigkeiten oder Wärme durch geschlossene Grenzen diffundieren?

### OQ-023 — Beeinflusst die Größe einer Zauberrepräsentation Effizienz?

**Kategorie:** Syntax / Kosten / Gameplay  
**Status:** Offen

Wie beeinflussen Größe, Präzision, Kopplungsfläche und Material die Entladerate, Stabilität und Überlastungsgrenze?

### OQ-024 — Wann wird High-Level-Feld-/Wellenmagie eingeführt?

**Kategorie:** Theorie / Simulation / Gameplay  
**Status:** Offen

Welche Voraussetzungen verhindern, dass direkte Feld- oder Wellenmagie die materiegebundene Standardmagie trivial ersetzt?

### OQ-025 — Wie wird thaumisches Potential quantitativ berechnet?

**Kategorie:** Kosten / Simulation  
**Status:** Offen

```text
thaumic_potential = f(
    physikalische Energie,
    Leistungsdichte,
    Materialkopplung,
    Geometrie,
    Distanz,
    Effizienz,
    Verluste
)
```

### OQ-026 — Welche thaumischen Materialattribute braucht der erste Prototyp?

**Kategorie:** Simulation / Materialität / Gameplay  
**Status:** Offen

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

Wie beeinflussen Linienführung, Material, Größe, Symmetrie, Beschädigung und Präzision die Kopplung?

### OQ-028 — Welche Fixed-Point-Quanten verwendet die Simulation?

**Kategorie:** Simulation / Performance  
**Status:** Offen

Welche kleinsten internen Einheiten werden für Energie, Masse, Position, Zeit und Stoffanteile verwendet?

Erster Kandidat:

```text
Energie: Millijoule in signed 64-bit Integer
```

### OQ-029 — Wie werden viele Stoffkomponenten pro Zelle gespeichert?

**Kategorie:** Simulation / Performance  
**Status:** Offen

Welche Inline-Kapazität ist sinnvoll, und wie funktionieren CompositionPool, Copy-on-Write und konservierte Spurstoff-Records?

### OQ-030 — Wie werden parallele StateChangeRequests aufgelöst?

**Kategorie:** Syntax / Simulation  
**Status:** Offen

Was geschieht bei widersprüchlichen, konkurrierenden oder ressourcenabhängigen Änderungen im selben Tick?

### OQ-031 — Sind partielle Effect-Ausführungen erlaubt?

**Kategorie:** Syntax / Kosten / Gameplay  
**Status:** Offen

Wird ein EffectNode bei unzureichender Energie abgebrochen, proportional begrenzt, teilweise ausgeführt oder gemäß expliziter Policy behandelt?

### OQ-032 — Welche Grenzen gelten für biologische und kognitive Zauber?

**Kategorie:** Theorie / Syntax / Gameplay  
**Status:** Offen

Biologische und kognitive Makros werden vorläufig aus materiellen, chemischen, elektrischen und informationsverarbeitenden Operationen abgeleitet.

Offen sind:

- notwendige Neuro-/Biologiebibliotheken
- zulässige Analyseauflösung
- individuelle Variation
- Fehlertoleranz
- direkte mentale Fernwirkung
- ethische und spielmechanische Begrenzungen

### OQ-033 — Wie funktionieren diskrete Tiefenebenen?

**Kategorie:** Simulation / Gameplay  
**Status:** Offen

Sind Hintergrund und Vordergrund voll physikalisch, und welche Cross-Layer-Interaktionen, Verdeckungen und Übergänge sind erlaubt?
