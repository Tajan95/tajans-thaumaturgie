# 11 — LLM Spell Compiler

Dieses Dokument beschreibt die Idee, ein LLM als Übersetzungsschicht zwischen natürlicher Sprache und formaler Zaubersyntax zu verwenden.

**Status:** Feature-Idee / Architekturhypothese  
**Grundentscheidung:** Das LLM ist Hilfsmittel, nicht Regelautorität.

---

## Grundidee

Das Magie-System selbst bleibt hart regelgebunden. Ein LLM darf keine Grundregeln brechen, sondern übersetzt natürlichsprachige Beschreibungen in erlaubte semantische Komponenten.

```text
Nutzerbeschreibung
    ↓
LLM-Interpretation
    ↓
Semantische Zauberbausteine
    ↓
Regelvalidierung
    ↓
Kostenberechnung
    ↓
visuelle Repräsentation
    ↓
Simulation
```

## Programmieranalogie

Das Genie-System verhält sich wie ein LLM beim Programmieren.

Es kann helfen:

- Code/Zauberstruktur vorzuschlagen
- Syntax zu vervollständigen
- Fehler zu erklären
- Alternativen anzubieten
- abstrakte Absichten in konkrete Komponenten zu übersetzen

Aber:

```text
falscher Code kompiliert nicht
falsche Zaubersyntax wirkt nicht korrekt
```

Ein syntaktisch oder semantisch falscher Zauber wird also nicht einfach durch Wunschintention gerettet.

## Autoritative Regelengine

Die Regelengine entscheidet, ob ein vorgeschlagener Zauber gültig ist.

Das LLM darf:

- Absicht interpretieren
- fehlende Parameter vorschlagen
- passende Komponenten aus einer Bibliothek wählen
- mehrere Varianten anbieten
- Fehlerquellen erklären
- eine abstrakte Zauberstruktur visualisieren lassen

Das LLM darf nicht:

- Erhaltungssätze ignorieren
- Kosten umgehen
- nicht existierende Komponenten als gültig deklarieren
- ungültige Zielauswahl erzwingen
- Simulationsergebnisse direkt bestimmen
- fehlende physische Repräsentation überspringen

## Genie-Slider

Der Genie-Slider steuert, wie stark unausgesprochene Details ergänzt werden.

| Stufe | Bedeutung | Risiko |
|---|---|---|
| Minimal | Nur explizit beschriebene Effekte werden umgesetzt. | Viele Zauber bleiben unvollständig. |
| Moderat | Naheliegende Lücken werden ergänzt und sichtbar gemacht. | Gute Balance aus Komfort und Kontrolle. |
| Stark | Popkulturell/intuitiv Gemeintes wird aktiv interpretiert. | Mehr Komfort, aber weniger Kontrolle. |

Der Genie-Slider ist ein Komfort-/Kontroll-Kompromiss. Er verändert nicht die Grundregeln, sondern nur den Grad der automatischen Ergänzung beim Erstellen eines Zaubers.

## Validierungsschritte

Ein LLM-generierter Zauber sollte mindestens diese Prüfungen durchlaufen:

1. **Syntaxprüfung:** Ist die Struktur formal gültig?
2. **Semantikprüfung:** Haben die Komponenten eine definierte Bedeutung?
3. **Ressourcenprüfung:** Gibt es ausreichende Mana-/Energiequellen?
4. **Erhaltungsprüfung:** Werden Masse, Energie und Impuls korrekt bilanziert?
5. **Zielprüfung:** Ist das Ziel eindeutig und erreichbar?
6. **Repräsentationsprüfung:** Kann der Zauber physisch/visuell dargestellt werden?
7. **Simulationsprüfung:** Kann die Engine den Effekt ausführen?

## Offene Fragen

1. Ist der Genie-Slider ein Gameplay-System, ein Editorwerkzeug oder beides?
2. Wie werden LLM-Vorschläge sichtbar validiert?
3. Wie wird verhindert, dass natürlichsprachige Bequemlichkeit die formale Zaubersprache entwertet?
4. Wie genau wird ein generierter Zauber in eine sichtbare Formel/Glyphe rückübersetzt?
5. Welche Fehlerdiagnosen bekommt der Spieler bei ungültiger Zaubersyntax?
