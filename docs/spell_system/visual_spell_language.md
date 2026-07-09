# 13 — Visual Spell Language

Dieses Dokument beschreibt die Grundentscheidung, dass Zauber innerhalb der Spielwelt als physische visuelle Programmiersprache existieren.

**Status:** Grundentscheidung festgelegt, konkrete Syntax offen.

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

## Warum?

Magie soll nicht nur unsichtbarer Wille sein, sondern eine prüfbare, manipulierbare und fehleranfällige Programmiersprache.

Das erzeugt:

- klare Syntax
- sichtbare Fehlerquellen
- materielle Angriffsflächen
- Vorbereitung statt beliebiger Spontanität
- Gameplay über Zeichnen, Kopieren, Modifizieren und Zerstören von Zaubern

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

## Semantische Lesbarkeit

Die visuelle Zaubersprache soll nicht nur dekorativ sein. Sie soll semantisch lesbar sein.

Ein erfahrener Zauberer sollte anhand der visuellen Struktur grob erkennen können:

- Zielklasse
- Wirkungsart
- räumliche Struktur
- zentrale Modifier
- Energie- oder Bindungsstruktur
- Bibliotheksreferenzen
- mögliche Risiken oder Instabilität

Das bedeutet nicht, dass jeder Zauber sofort vollständig verständlich sein muss. Komplexe Zauber können Analyse, Expertise oder Hilfsmittel benötigen.

## Mögliche visuelle Informationsschichten

| Schicht | Funktion |
|---|---|
| Grundform | grobe Zauberstruktur, z. B. Kreis, Linie, Knoten, Feld |
| Kernsymbol | Hauptwirkung oder zentrale Operation |
| Zielzeichen | Zielklasse oder Zielbindung |
| Modifier-Ring | Parameter wie Dauer, Richtung, Reichweite, Stärke |
| Import-/Bibliothekszeichen | Referenz auf externe Definitionen oder Makros |
| Sicherheits-/Stabilitätszeichen | Schutzlogik, Grenzwerte, Fehlerbehandlung |
| Energiekopplung | Quelle, Speicher oder Transferpfad |

## Mindestanforderung an ausführbare Zauber

Ein Zauber ist erst ausführbar, wenn folgende Bedingungen erfüllt sind:

1. Die abstrakte Struktur ist syntaktisch gültig.
2. Alle semantischen Komponenten sind definiert.
3. Ziel, Wirkung, Struktur, Modifier, Kosten und Fehlerlogik sind angegeben oder ableitbar.
4. Die Mana-/Energiequelle ist definiert.
5. Die Repräsentation ist physisch vorhanden oder gültig erzeugbar.
6. Referenzierte Bibliotheken sind verfügbar oder korrekt eingebettet.
7. Die Regelengine kann den Zauber validieren.
8. Die Simulation kann den Effekt ausführen.

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
