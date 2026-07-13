# 13 — Visual Spell Language

**Stand:** 2026-07-13, 18:18 Europe/Berlin  
**Status:** Grundentscheidung festgelegt, konkrete Symbolsprache offen

Dieses Dokument beschreibt die Grundentscheidung, dass Zauber innerhalb der Spielwelt als physische visuelle Programmiersprache existieren.

---

## Grundsatz

Jeder ausführbare Zauber benötigt eine physische, visuelle Repräsentation.

Mögliche Träger:

- Schriftrolle
- Buchseite
- Gravur
- Zeichnung
- Ritualkreis
- magisches Tattoo
- eingebrannte, geätzte oder projizierte Zeichen

Auch vokalisierte Zauber benötigen eine solche Repräsentation am Körper oder in der Nähe des Zauberers.

---

## Vokalisierung und Gestik

Vokalisierung und Gestik können Zauber auslösen, parametrisieren oder ausrichten.

Sie ersetzen aber nicht die notwendige physische visuelle Repräsentation.

```text
Vokalisierung/Gestik = Trigger oder Laufzeitinput
Physische Repräsentation = notwendige Zauberstruktur
```

Mögliche Funktionen von Stimme/Gestik:

- Aktivierung eines vorbereiteten Zaubers
- Auswahl eines Zieles
- Timing einer Wirkung
- Modulation von Stärke oder Richtung
- Bestätigung einer Bedingung
- Halte- oder Toggle-Input für dauerhafte Effekte

---

## Start-Glyphe / Activation Node

Jeder ausführbare Zauber besitzt mindestens eine Start-Glyphe bzw. einen Aktivierungsknoten.

```text
Start-Glyphe = sichtbarer Entry Point des Zauberprogramms
```

Ohne Start-Modifier gilt:

```text
Start-Glyphe fertiggestellt → Zauber validieren → einmalig ausführen
```

Diese Default-Regel ist wichtig:

> Startbedingungen, Verzögerungen, Vokalisierung, Gestik oder Sicherheitsmechanismen sind explizite visuelle Anweisungen, keine unsichtbaren Annahmen.

Damit muss die visuelle Sprache zeigen können, ob ein Zauber sofort auslöst oder auf einen Trigger wartet.

Mögliche visuelle Bestandteile der Start-Glyphe:

| Visuelles Element | Semantische Funktion |
|---|---|
| Start-Kern | ausführbarer Einstiegspunkt |
| Trigger-Marker | Fertigstellung, Stimme, Geste, Kontakt, Zeit, Umweltbedingung |
| Modus-Ring | einmalig, gehalten, Toggle, autonom, wiederholt |
| Ressourcen-Kopplung | Vorabkosten, Reservierung, Dauerverbrauch, gebundene Quelle |
| Stop-Marker | Ende nach Sequenz, Dauer, Bedingung, Loslassen oder Ressourcenende |
| Sicherheitsknoten | Abort-Regeln, Grenzwerte, Rückkopplungsschutz |

Ein erfahrener Zauberer sollte daher grob erkennen können:

- feuert der Zauber sofort?
- ist er vorbereitet und wartet auf ein Wort, eine Geste oder eine Umweltbedingung?
- muss er gehalten werden?
- ist er ein Toggle?
- läuft er autonom aus einer Quelle weiter?
- besitzt er eine sichere Abschaltung?

Details siehe:

- `spell_lifecycle_and_activation.md`

---

## Warum?

Magie soll nicht nur unsichtbarer Wille sein, sondern eine prüfbare, manipulierbare und fehleranfällige Programmiersprache.

Das erzeugt:

- klare Syntax
- sichtbare Fehlerquellen
- materielle Angriffsflächen
- Vorbereitung statt beliebiger Spontanität
- Gameplay über Zeichnen, Kopieren, Modifizieren und Zerstören von Zaubern

---

## Technisches Modell

Die visuelle Darstellung und die interne Zauberstruktur müssen wechselseitig kompatibel sein.

```text
visuelle Repräsentation
    ↕
Parser / Visualizer
    ↕
abstrakte Zauberstruktur
    ↕
Regelengine
    ↕
Simulation
```

---

## Zwei Arbeitsrichtungen

### 1. Von Zeichnung zu Zauber

Ein korrekt gezeichneter Zauber wird geparst und in eine ausführbare Zauberstruktur übersetzt.

```text
Glyphe → Parser → Zauberstruktur → Validierung → Ausführung
```

### 2. Von Programm zu Zeichnung

Ein abstrakt programmierter Zauber wird durch einen Visualizer in eine gültige physische Repräsentation übersetzt.

```text
Zauberstruktur → Visualizer → Glyphe / Schriftrolle / Tattoo / Ritualkreis
```

---

## Semantische Lesbarkeit

Die visuelle Zaubersprache soll nicht nur dekorativ sein. Sie soll semantisch lesbar sein.

Ein erfahrener Zauberer sollte anhand der visuellen Struktur grob erkennen können:

- Zielklasse
- Wirkungsart
- räumliche Struktur
- zentrale Modifier
- Start- und Triggerlogik
- Ausführungsmodus
- Beendigungslogik
- Energie- oder Bindungsstruktur
- Bibliotheksreferenzen
- mögliche Risiken oder Instabilität

Das bedeutet nicht, dass jeder Zauber sofort vollständig verständlich sein muss. Komplexe Zauber können Analyse, Expertise oder Hilfsmittel benötigen.

---

## Mögliche visuelle Informationsschichten

| Schicht | Funktion |
|---|---|
| Grundform | grobe Zauberstruktur, z. B. Kreis, Linie, Knoten, Feld |
| Start-Glyphe | Entry Point, Trigger- und Aktivierungslogik |
| Kernsymbol | Hauptwirkung oder zentrale Operation |
| Zielzeichen | Zielklasse oder Zielbindung |
| Modifier-Ring | Parameter wie Dauer, Richtung, Reichweite, Stärke |
| Import-/Bibliothekszeichen | Referenz auf externe Definitionen oder Makros |
| Sicherheits-/Stabilitätszeichen | Schutzlogik, Grenzwerte, Fehlerbehandlung |
| Energiekopplung | Quelle, Speicher oder Transferpfad |
| Terminationszeichen | Ende nach Sequenz, Dauer, Bedingung, Loslassen, Toggle oder Ressourcenende |

---

## Editor-Implikation

Die visuelle Sprache sollte früh mit einem Editor getestet werden.

Der Editor darf zwischen einer klaren Arbeitsgraph-Darstellung und einer finalen in-world-Zaubergeometrie unterscheiden:

```text
Arbeitsgraph
    → Validierung
    → Layout / Symmetrisierung / Stilisierung
    → gültige physische Zauberrepräsentation
```

Details siehe:

- `../implementation/spell_editor_architecture.md`

---

## Mindestanforderung an ausführbare Zauber

Ein Zauber ist erst ausführbar, wenn folgende Bedingungen erfüllt sind:

1. Die abstrakte Struktur ist syntaktisch gültig.
2. Alle semantischen Komponenten sind definiert.
3. Ziel, Wirkung, Struktur, Modifier, Kosten und Fehlerlogik sind angegeben oder ableitbar.
4. Die Mana-/Energiequelle ist definiert.
5. Mindestens eine gültige Start-Glyphe bzw. ein Aktivierungsknoten ist vorhanden.
6. Die Startlogik ist eindeutig: sofort, getriggert, gehalten, Toggle, autonom oder wiederholt.
7. Die Beendigungs- oder Abbruchlogik ist definiert oder besitzt gültige Defaultwerte.
8. Die Repräsentation ist physisch vorhanden oder gültig erzeugbar.
9. Referenzierte Bibliotheken sind verfügbar oder korrekt eingebettet.
10. Die Regelengine kann den Zauber validieren.
11. Die Simulation kann den Effekt ausführen.

---

## Offene Fragen

1. Welche Grundformen tragen welche semantische Bedeutung?
2. Gibt es eine feste Leserichtung?
3. Wie werden Verschachtelungen, Bedingungen und Schleifen visuell dargestellt?
4. Wie erkennt man visuelle Syntaxfehler?
5. Können beschädigte Glyphen teilweise, falsch oder gar nicht wirken?
6. Wie groß muss eine Repräsentation sein, damit sie ausführbar ist?
7. Gibt es Materialanforderungen an Schriftrollen, Tattoos oder Gravuren?
8. Wie werden Bibliotheksreferenzen visuell dargestellt?
9. Wie viel eines Zaubers kann ein erfahrener Zauberer rein visuell erkennen?
10. Wie wird der Unterschied zwischen Arbeitsgraph und finaler in-world-Glyphe dargestellt?
11. Wie stark darf der Editor automatisch symmetrisieren, ohne die semantische Lesbarkeit zu beschädigen?
