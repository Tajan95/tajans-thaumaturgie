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

## Mindestanforderung an ausführbare Zauber

Ein Zauber ist erst ausführbar, wenn folgende Bedingungen erfüllt sind:

1. Die abstrakte Struktur ist syntaktisch gültig.
2. Alle semantischen Komponenten sind definiert.
3. Ziel, Wirkung, Struktur, Modifier, Kosten und Fehlerlogik sind angegeben oder ableitbar.
4. Die Mana-/Energiequelle ist definiert.
5. Die Repräsentation ist physisch vorhanden oder gültig erzeugbar.
6. Die Regelengine kann den Zauber validieren.
7. Die Simulation kann den Effekt ausführen.

## Offene Fragen

1. Welche Grundformen tragen welche semantische Bedeutung?
2. Gibt es eine feste Leserichtung?
3. Wie werden Verschachtelungen, Bedingungen und Schleifen visuell dargestellt?
4. Wie erkennt man visuelle Syntaxfehler?
5. Können beschädigte Glyphen teilweise, falsch oder gar nicht wirken?
6. Wie groß muss eine Repräsentation sein, damit sie ausführbar ist?
7. Gibt es Materialanforderungen an Schriftrollen, Tattoos oder Gravuren?
