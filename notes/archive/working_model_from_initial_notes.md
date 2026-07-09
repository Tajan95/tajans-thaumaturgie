# 08 — Working Model from Initial Notes

Dieses Dokument fasst das erste Arbeitsmodell zusammen, das aus den Rohnotizen und der ersten Klärung vom 06.07.2026 ableitbar ist.

**Status:** Arbeitsmodell  
**Teilweise durch Designentscheidungen DD-003 bis DD-007 stabilisiert.**

---

## 1. Kernthese

Magie ist eine regelgebundene Form von Zustandsveränderung.

Sie kann physische, chemische, thermische, räumliche, optische, kognitive oder relationale Zustände verändern, aber nicht kostenlos und nicht beliebig.

Vorläufige Form:

```text
Magische Operation = kontrollierte Zustandsänderung unter Energie-, Informations-, Präzisions- und Erhaltungskosten
```

---

## 2. Vorläufige Zauberformel

Ein ausführbarer Zauber benötigt mindestens:

```text
Zauber = Zielauswahl
       + Wirkung
       + Struktur
       + Modifier
       + Mana-/Energiequelle
       + Kontrollaufwand
       + Nebenprodukte
       + Fehlerlogik
       + physische visuelle Repräsentation
```

Die visuelle Repräsentation kann z. B. eine Schriftrolle, Gravur, Zeichnung, Buchseite, ein Ritualkreis oder ein magisches Tattoo sein.

## 3. Vorläufiges Kostenmodell

```text
Gesamtkosten = physikalische Mindestarbeit
             + Kontrollaufwand
             + Distanzfaktor
             + Komplexitätsfaktor
             + Dauerfaktor
             + Verlustwärme
             + Sicherheits-/Stabilisierungskosten
```

Kontrollaufwand ist keine eigene Energiequelle. Er beschreibt mentale, motorische oder syntaktische Belastung bei Konstruktion, Ausführung und Stabilisierung eines Zaubers.

## 4. Mana als Arbeitsbegriff

Mana wird als abstrakter Energie-/Arbeitsbegriff verstanden.

```text
Mana ≈ magische Arbeitswährung / Mana-Joule
```

Mana ist keine konkrete Substanz. Quellen und Speicher können jedoch sehr konkret sein.

| Begriff | Bedeutung | Status |
|---|---|---|
| Mana | Abstrakte Einheit magischer Arbeit/Energie | Festgelegt |
| Bio-Mana-Quelle | Biologische oder chemisch gebundene Energie, die magisch nutzbar gemacht wird | Festgelegt |
| Externer Mana-Speicher | Nicht-biologisches Medium, z. B. Kristall oder Artefakt | Hypothese |
| Kognitive Kontrolle | Konzentration, Verständnis und Ausführungsfähigkeit; keine Mana-Art | Festgelegt |

## 5. Erhaltung und Verluste

Es gilt:

- Energie wird nicht erschaffen oder vernichtet.
- Masse wird nicht erschaffen oder vernichtet, außer ein expliziter Umwandlungsprozess ist definiert.
- Impuls muss berücksichtigt werden.
- Jeder Prozess erzeugt Verluste.
- Abwärme entsteht standardmäßig und muss aktiv gelenkt werden, wenn sie nicht frei/radial abfließen soll.

Magie darf ungewöhnliche Transformationen durchführen, aber sie muss Quellen, Senken, Kosten und Nebenprodukte berücksichtigen.

## 6. Unintuitive, aber erlaubte Effekte

Das System verbietet nicht alles, was im Alltag unmöglich wirkt. Entscheidend ist, ob ein Effekt innerhalb der Erhaltungsgesetze formulierbar und bezahlbar ist.

Beispiele:

| Effekt | Vorläufige Interpretation |
|---|---|
| Illusion | Lichtprojektion oder Wahrnehmungs-/Signalmanipulation ohne Massenänderung |
| Blei zu Gold | Nukleare Transformation mit extrem hohen Kosten und Nebenprodukten |
| Zeitumkehrung | Spekulativ: präzise Umkehrung relevanter Zustands-/Bewegungsvektoren |
| Zeitverlangsamung | Spekulativ: Manipulation lokaler Prozessraten oder Dynamiken |

## 7. Fokusmedien

Zauberstäbe und ähnliche Werkzeuge wirken als Fokusmedien.

Sie können:

- Präzision erhöhen
- Wirkungsgrad erhöhen
- Zielauswahl stabilisieren
- externe Mana-Speicher einbinden
- komplexe Zaubersyntax leichter kontrollierbar machen

## 8. LLM-Interface

Ein LLM kann als Zauber-Compiler oder Assistent dienen:

```text
Natürlichsprachige Beschreibung → semantische Bausteine → Validierung → ausführbarer Zauber
```

Das LLM darf keine Grundregeln überschreiben. Die Regelengine bleibt autoritativ.

Ein falsch erzeugter oder falsch interpretierter Zauber verhält sich wie fehlerhafter Code: Er kompiliert nicht, läuft nicht, bricht ab oder erzeugt nicht den gewünschten Effekt.

## 9. Makros und Effizienz

Zauber können granular selbst geschrieben oder über Makros bzw. Bibliothekskomponenten erstellt werden.

| Ansatz | Vorteil | Nachteil |
|---|---|---|
| Einsteiger-Makro | schnell, robust, bequem | potenzieller Overhead, oft nicht optimal |
| Experten-Makro | schnell und effizient, wenn gut optimiert | schwer zu erstellen oder zu verstehen |
| Custom-Zauber | maximal situationsspezifisch, potenziell sehr effizient | langsam, komplex, fehleranfällig |

Effizienz entsteht aus der Struktur des Zaubers, nicht aus einem künstlichen Klassenmodifier.

## 10. Prototypische Umsetzung

Der erste Prototyp sollte in 2D beginnen.

Minimal zu testen:

- Entitäten mit Position, Masse, Material und Temperatur
- Wirkungen wie Bewegen, Erwärmen, Abkühlen, Binden, Trennen
- Zielauswahl über Punkt, Radius oder Objekt-ID
- Kostenmodell mit Mindestarbeit und Verlusten
- Abwärme oder abstrakter Verlustwert
- einfache emergente Fehlerfälle
- Übersetzung zwischen abstrakter Zauberstruktur und visueller Darstellung

## 11. Größte offene Entscheidungen

1. Gibt es eine direkte Mana-Joule-Umrechnung?
2. Wie exakt werden physikalische Erhaltungssätze im ersten 2D-Prototyp umgesetzt?
3. Welche Zauberform ist intern am besten: Sequenz, Baum, Graph oder Komponentenobjekt?
4. Wie wird die visuelle Zaubersprache konkret geparst und validiert?
5. Wann sind abstrakte Misslingen-Modifier nötig, statt Fehler rein emergent entstehen zu lassen?
