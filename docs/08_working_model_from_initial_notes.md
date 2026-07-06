# 08 — Working Model from Initial Notes

Dieses Dokument fasst das erste mögliche Arbeitsmodell zusammen, das aus den Rohnotizen vom 06.07.2026 ableitbar ist.

**Status:** Hypothese / Arbeitsmodell  
**Nicht endgültig festgelegt.**

---

## 1. Kernthese

Magie ist eine regelgebundene Form von Zustandsveränderung.

Sie kann physische, chemische, thermische, räumliche, kognitive oder relationale Zustände verändern, aber nicht kostenlos und nicht beliebig.

Vorläufige Form:

```text
Magische Operation = kontrollierte Zustandsänderung unter Energie-, Informations-, Präzisions- und Erhaltungskosten
```

---

## 2. Vorläufige Zauberformel

```text
Zauber = Zielauswahl + Wirkung + Struktur + Modifier + Energiequelle + Kontrollaufwand + Nebenprodukte + Fehlerlogik
```

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

## 4. Mana als Arbeitsbegriff

Mana wird vorläufig nicht als einfacher Fantasy-Balken behandelt, sondern als Sammelbegriff für bezahlbaren Änderungsaufwand.

Mögliche Untertypen:

| Typ | Bedeutung | Status |
|---|---|---|
| Bio-Mana | körperliche Leistungsfähigkeit / ATP-nahe Energiequelle | Hypothese |
| Kognitives Mana | mentale Kontroll- und Verstehensleistung | Hypothese |
| Externes Mana | gespeicherte Energie in Kristallen, Artefakten oder Ritualen | Hypothese |
| System-Mana | abstrakte Simulationsressource für Kostenrechnung | Offene Frage |

## 5. Erhaltung und Verluste

Vorläufig gilt:

- Energie wird nicht erschaffen oder vernichtet.
- Masse wird nicht erschaffen oder vernichtet, außer ein expliziter Umwandlungsprozess ist definiert.
- Impuls muss berücksichtigt werden.
- Jeder Prozess erzeugt Verluste.
- Abwärme entsteht standardmäßig und muss aktiv gelenkt werden, wenn sie nicht frei/radial abfließen soll.

## 6. Fokusmedien

Zauberstäbe und ähnliche Werkzeuge wirken vorläufig als Fokusmedien.

Sie können:

- Präzision erhöhen
- Wirkungsgrad erhöhen
- Zielauswahl stabilisieren
- externe Mana-Speicher einbinden
- komplexe Zaubersyntax leichter kontrollierbar machen

## 7. LLM-Interface

Ein LLM kann als Zauber-Compiler oder Assistent dienen:

```text
Natürlichsprachige Beschreibung → semantische Bausteine → Validierung → ausführbarer Zauber
```

Das LLM darf keine Grundregeln überschreiben. Die Regelengine bleibt autoritativ.

## 8. Prototypische Umsetzung

Der erste Prototyp sollte in 2D beginnen.

Minimal zu testen:

- Entitäten mit Position, Masse, Material und Temperatur
- Wirkungen wie Bewegen, Erwärmen, Abkühlen, Binden, Trennen
- Zielauswahl über Punkt, Radius oder Objekt-ID
- Kostenmodell mit Mindestarbeit und Verlusten
- Abwärme oder abstrakter Verlustwert
- einfache Fehlerfälle

## 9. Größte offene Entscheidungen

1. Was ist Mana ontologisch?
2. Wie exakt werden physikalische Erhaltungssätze umgesetzt?
3. Welche Zauberform ist intern am besten: Sequenz, Baum, Graph oder Komponentenobjekt?
4. Welche Rolle spielen visuelle Zeichen: UI, Lore oder Regelmechanik?
5. Wie stark darf ein LLM fehlende Details ergänzen?
