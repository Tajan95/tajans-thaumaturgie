# 09 — Glossary

Dieses Glossar sammelt zentrale Begriffe des Projekts.

**Status:** Frühfassung. Definitionen sind Arbeitsdefinitionen und können ersetzt werden.

---

## Abstrakte Zauberstruktur

Die interne Datenstruktur oder Programmlogik eines Zaubers, unabhängig von seiner konkreten visuellen Darstellung.

**Status:** Begriff

## Artefakt

Ein Objekt, das magische Struktur, Energie, Zielbindung oder eine Kombination daraus speichern und später aktivieren kann.

Nach DD-010 kann ein Artefakt insbesondere metastabile thaumische Potentialzustände, Zaubergeometrie, Zielbindung oder Auslösebedingungen tragen.

**Status:** Hypothese

## Bibliothek

Eine Sammlung wiederverwendbarer Zauberdefinitionen, Makros, Objektdefinitionen, Materialdefinitionen oder Hilfsroutinen, die von einem Zauber referenziert werden kann.

**Status:** Begriff / Offene Ausarbeitung

## Bio-Mana-Quelle

Biologische oder chemisch gebundene Energie, die durch magische Arbeit nutzbar gemacht werden kann.

Wichtig: Dies ist keine eigene Mana-Art, sondern eine Quelle für Mana bzw. magische Arbeit.

Nach DD-010 bedeutet dies genauer: biologische Energie erzeugt ein bio-thaumisches Potential, das durch geeignete Zaubergeometrie angezapft werden kann.

**Status:** Festgelegt

## Element

Funktionaler chemischer Grundbaustein im Materialsystem, z. B. Sauerstoff, Eisen oder Silizium.

Das System benötigt voraussichtlich keinen vollständigen Periodensystem-Katalog, sondern eine spiel- und simulationspraktische Auswahl.

**Status:** Begriff / Offene Ausarbeitung

## Feld-/Wellenmagie

Mögliche spätere High-Level-Interventionsklasse, bei der Magie direkt Felder, elektromagnetische Wellen, Photonen oder ähnliche nicht-materielle physikalische Zielgrößen manipuliert.

Nicht Teil der Standardmagie.

**Status:** Offene spätere Erweiterung

## Fokusmedium

Ein Werkzeug, z. B. ein Zauberstab, das magische Operationen präziser, effizienter oder stabiler macht.

Nach DD-010 ist ein Fokusmedium eine materielle Kopplungsstruktur für thaumische Potentiale, nicht nur ein symbolisches Hilfsmittel.

**Status:** Hypothese / Teilweise geklärt durch DD-010

## Fraktion

Anteil eines Stoffes, Elements oder Materials innerhalb einer Zelle, eines Pixels, eines Objekts oder eines Stoffgemisches.

**Status:** Begriff

## Genie-Slider

Ein Interface- oder Gameplay-Mechanismus, der bestimmt, wie stark ein LLM unausgesprochene Aspekte einer natürlichsprachigen Zauberbeschreibung ergänzt.

Er ist ein Komfort-/Kontroll-Kompromiss, nicht die eigentliche Regelautorität.

**Status:** Feature / Offene Frage

## Import

Eine explizite Einbindung einer Bibliothek oder Definition in einen Zauber.

Wenn ein Import fehlt, beschädigt ist oder nicht aufgelöst werden kann, kann der Zauber ungültig werden oder während der Ausführung abbrechen.

**Status:** Begriff / Offene Ausarbeitung

## Informationskomponente

Ein Zauberbaustein, der primär Informationen verarbeitet, z. B. Suchen, Filtern, Sortieren, Erkennen, Ausweichen oder Zielklassifikation.

**Status:** Begriff / Offene Kostenlogik

## Interventionsklasse

Beschreibt, worauf ein Zauber direkt zugreift, z. B. vorhandene Materie, materielle Zustände oder später eventuell Felder/Wellen.

```text
Interventionsklasse = direkter Zugriffstyp eines Zaubers
```

**Status:** Begriff / Teilweise festgelegt

## Kognitive Kontrolle

Mentale Arbeit, Konzentration, Verständnis und Ausführungsfähigkeit, die beim Konstruieren, Halten oder Ausführen eines Zaubers nötig sind.

Kognitive Kontrolle ist keine Mana-Art, sondern ein Kontrollflaschenhals.

**Status:** Festgelegt

## Kognitives Mana

Verworfener bzw. nicht verwendeter Begriff.

Mentale Belastung wird als kognitive Kontrolle modelliert, nicht als eigener Mana-Typ.

**Status:** Verworfen

## Makro-Zauber

Eine vorgefertigte höhere Abstraktion über der eigentlichen Zaubersyntax.

Makros sind komfortabel, können aber Overhead enthalten. Ihre Effizienz ergibt sich aus ihrer konkreten Struktur, nicht aus einem künstlichen Klassenmodifier.

**Status:** Festgelegt

## Mana

Abstrakter Energie-/Arbeitsbegriff für magische Arbeit, vergleichbar mit Joule als Maßeinheit für Energie bzw. Arbeit.

Mana ist keine konkrete Substanz und kein Teilchen. Nach DD-010 bezeichnet Mana genauer den nutzbaren thaumischen Arbeitsfluss aus realen physikalischen Energiepotentialen.

```text
Mana = nutzbarer thaumischer Arbeitsfluss aus realen Energiepotentialen
```

**Status:** Festgelegt

## Mana-Joule

Arbeitstitel für eine mögliche quantitative Einheit magischer Arbeit.

Ob ein Mana-Joule direkt einer physikalischen Energiemenge entspricht oder nur eine Simulationsgröße ist, bleibt offen.

**Status:** Offene Frage

## Mana-Partikel

Verworfenes Standardmodell, nach dem Mana aus eigenen diskreten Teilchen bestehen würde.

Das Projekt verwendet stattdessen ein Feldpotential-/Arbeitsflussmodell. Mana-Speicher enthalten keine Mana-Partikel, sondern halten metastabile thaumische Potentialzustände.

**Status:** Verworfen durch DD-010

## Mana-Speicher

Ein Medium, z. B. ein Kristall oder Artefakt, das nutzbare magische Arbeit speichern kann.

Nach DD-010 speichert ein Mana-Speicher keine Mana-Substanz, sondern einen metastabilen thaumischen Potentialzustand.

**Status:** Festgelegt als Arbeitsmodell durch DD-010

## Mana-Speicherattribute

Vorläufige Material- oder Objektattribute zur Beschreibung von Mana-Speichern und Fokusmedien.

| Attribut | Bedeutung |
|---|---|
| `mana_capacity` | Maximale speicherbare thaumische Arbeit / Potentialmenge. |
| `mana_charge` | Aktuell gespeicherte thaumische Ladung bzw. nutzbare Arbeit. |
| `thaumic_potential` | Aktuelle thaumische Spannung / Potentialhöhe. |
| `mana_conductivity` | Wie gut thaumischer Fluss durch das Material läuft. |
| `mana_leakage` | Wie schnell gespeichertes Potential verloren geht. |
| `mana_conversion_efficiency` | Wie gut reale Energie in nutzbaren thaumischen Arbeitsfluss gekoppelt wird. |
| `mana_discharge_rate` | Wie schnell gespeichertes Potential sicher abgegeben werden kann. |
| `mana_overload_threshold` | Grenze, ab der Material, Fokus oder Zauber instabil wird. |
| `syntax_affinity` | Wie gut ein Material physische Zaubergeometrie trägt oder verstärkt. |
| `feedback_risk` | Risiko einer Rückkopplung in Speicher, Fokusmedium oder Zauberer. |

**Status:** Begriff / Hypothese

## Material

Spielpraktische Stoff- oder Objektklasse mit Eigenschaften wie Dichte, Härte, Leitfähigkeit, Reaktivität oder Viskosität.

Ein Material kann aus mehreren Substanzen oder Elementfraktionen bestehen.

**Status:** Begriff / Offene Ausarbeitung

## Materialauflösung

Detailgrad, mit dem die Zusammensetzung eines Materials in der Simulation sichtbar oder berechnet wird.

Ein Stein kann z. B. zunächst homogen erscheinen, intern aber Fraktionen aus Silikaten, Salzen und Spurenelementen enthalten.

**Status:** Begriff / Offene Simulation

## Materiegebundene Magie

Standard-Interventionsklasse des Systems.

Magie koppelt direkt an vorhandene Materie und deren Zustände, z. B. Position, Geschwindigkeit, Temperatur, Phase, Druck, Ladungsverteilung, chemische Bindung oder Zusammensetzung.

**Status:** Festgelegt durch DD-009

## Magische Arbeit

Kontrollierte Zustandsveränderung durch Magie unter Energie-, Kontroll-, Verlust- und Fehlerbedingungen.

Nach DD-010 wird magische Arbeit über thaumischen Arbeitsfluss aus realen Energiepotentialen bezahlt.

**Status:** Festgelegt

## Memory-Slot

Begrenzter gelernter Speicherplatz für ein häufig verwendetes Makro, das ohne mitgeführte Referenzbibliothek korrekt reproduziert werden kann.

Ein Memory-Slot ersetzt nicht die physische visuelle Repräsentation des Zaubers.

**Status:** Feature / Festgelegt als Teil von DD-008

## Modifier

Eine Komponente, die Parameter einer Wirkung verändert, z. B. Stärke, Dauer, Richtung, Form, Reichweite oder Bedingung.

**Status:** Begriff

## Objektdefinition

Eine formale Beschreibung einer Objektklasse, z. B. „Tür“, „Stein“, „Wasser“ oder „Klinge“, auf die Zauber bei Zielauswahl oder Wirkungsauslegung referenzieren können.

**Status:** Begriff / Offene Ausarbeitung

## Operator

Eine logische Strukturkomponente, die Wirkungen verknüpft oder steuert, z. B. Sequenz, Parallelität, Wiederholung, Bedingung oder Umkehrung.

**Status:** Begriff

## Physische visuelle Repräsentation

Eine in der Spielwelt vorhandene sichtbare Form eines Zaubers, z. B. Schriftrolle, Buchseite, Gravur, Zeichnung, Ritualkreis oder Tattoo.

Ein Zauber muss eine solche Repräsentation besitzen, um ausführbar zu sein.

Nach DD-010 ist diese Repräsentation nicht nur Symbol, sondern zugleich materielle Zaubergeometrie: eine Kopplungsstruktur, die thaumische Potentiale anzapfen, lenken oder transformieren kann.

**Status:** Festgelegt

## Phase

Zustandsform eines Materials oder Stoffes: fest, flüssig, gasförmig oder Plasma.

**Status:** Begriff

## Regelengine

Das autoritative System, das prüft, ob ein Zauber syntaktisch korrekt, semantisch gültig, bezahlbar und simulierbar ist.

**Status:** Festgelegt

## Ritual

Ein vorbereiteter oder formal gebundener Zauberprozess, der Energie, Syntax, Bedingungen oder Zielbindung vorab stabilisieren kann.

Nach DD-010 kann ein Ritual auch als räumlich stabilisierte Kopplungsstruktur dienen, die große Energiequellen langsam, effizient oder sicher in Mana-Speicher überführt.

**Status:** Hypothese

## Semantisches Primitive

Ein kleinstmöglicher Bedeutungsbaustein der Zaubersprache.

**Status:** Begriff

## Sub-Pixel-Fraktion

Material- oder Stoffanteil, der kleiner als eine sichtbare Weltzelle bzw. ein Pixelvolumen wäre, aber aus Gründen der Massenerhaltung weiter bilanziert wird.

**Status:** Begriff / Offene Simulation

## Thaumische Spannung

Potentialdifferenz im thaumischen Feldmodell, die aus einem realen physikalischen Energiepotential hervorgeht.

Eine thaumische Entladung entlädt zugleich das gekoppelte physikalische Analog.

**Status:** Begriff / Festgelegt durch DD-010

## Thaumischer Arbeitsfluss

Nutzbarer Fluss magischer Arbeit aus einem thaumischen Potential durch eine Zaubergeometrie.

```text
physikalisches Energiepotential
→ thaumisches Potential
→ thaumischer Arbeitsfluss
→ magische Arbeit
```

**Status:** Begriff / Festgelegt durch DD-010

## Thaumisches Feld

Hypothetische Kopplungsschicht der Welt, über die reale physikalische Energiepotentiale magisch adressierbar werden.

Das thaumische Feld ist keine zusätzliche Energiequelle, sondern eine Übertragungs- und Kopplungsebene.

**Status:** Begriff / Festgelegt als Arbeitsmodell durch DD-010

## Thaumisches Potential

Gekoppelte Feldspannung, die aus physikalischen Energieunterschieden hervorgeht und durch geeignete Zaubergeometrie nutzbar gemacht werden kann.

**Status:** Begriff / Festgelegt durch DD-010

## Visuelle Lesbarkeit

Die Eigenschaft eines Zaubers, durch seine sichtbare Struktur zumindest grob interpretierbar zu sein.

Erfahrene Zauberer sollen anhand visueller Muster Zielklasse, Wirkungsart, Struktur, Modifier oder Risiken erkennen können.

**Status:** Feature / Offene Ausarbeitung

## Visuelle Zaubersprache

Eine physische, sichtbare Programmiersprache für Zauber. Sie muss in eine abstrakte Zauberstruktur geparst werden können, und eine abstrakte Zauberstruktur muss regelkonform visualisierbar sein.

Nach DD-010 ist sie zusätzlich eine reale Geometrie zur Kopplung, Leitung und Transformation thaumischer Potentiale.

**Status:** Festgelegt / Ausarbeitung offen

## Vokalisierung

Stimmliche Auslösung oder Parametrisierung eines Zaubers.

Vokalisierung kann einen vorbereiteten Zauber triggern oder steuern, ersetzt aber nicht die notwendige physische visuelle Repräsentation.

**Status:** Festgelegt / Ausarbeitung offen

## Weltzelle

Kleinste räumliche Simulationseinheit der 2D-Welt, die Material, Temperatur, Phase, Fraktionen und ggf. Bewegungsvektoren tragen kann.

Nach DD-010 kann eine Weltzelle optional auch thaumische Zustandsgrößen wie `thaumic_potential`, `mana_capacity`, `mana_charge`, `mana_conductivity` oder `mana_leakage` tragen.

**Status:** Begriff / Offene Simulation

## Zauberformel

Die vollständige formale Struktur eines Zaubers, bestehend aus Zielauswahl, Wirkung, Struktur, Modifiern, Kosten, Bedingungen, Fehlerlogik und visueller Repräsentation.

**Status:** Begriff

## Zaubergeometrie

Physische Syntaxstruktur eines Zaubers, die nicht nur Bedeutung repräsentiert, sondern thaumische Potentiale koppeln, leiten, transformieren und auf Zielzustände anwenden kann.

```text
Zaubergeometrie = Schaltkreis / Antenne / Linse / Ventil / Transformator
                  für thaumische Potentiale
```

**Status:** Begriff / Festgelegt durch DD-010

## Zauberstab

Ein mögliches Fokusmedium, das Präzision, Effizienz, Zielstabilität und Zugriff auf externe Mana-Speicher verbessern kann.

Nach DD-010 kann ein Zauberstab als Komposit aus Leiter, Speicherzugang, Geometrieträger, Zielantenne und Sicherheitsfilter verstanden werden.

**Status:** Hypothese / Teilweise geklärt durch DD-010
