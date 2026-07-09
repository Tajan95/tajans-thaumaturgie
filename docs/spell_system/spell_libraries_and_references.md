# 14 — Spell Libraries and References

Dieses Dokument beschreibt die Theorie zu Zauberbibliotheken, Makros, Imports und Objektdefinitionen.

**Status:** Arbeitsmodell / teilweise festgelegt

---

## Grundidee

Komplexe Zauber bestehen aus vielen granularen Komponenten. Für praktische Anwendung braucht das System daher Bibliotheken, die wiederverwendbare Definitionen und Makros bereitstellen.

Analogie:

```text
Programmcode nutzt Libraries / Imports.
Zaubercode nutzt Zauberbibliotheken / Referenzen.
```

## Mögliche Inhalte einer Bibliothek

Eine Zauberbibliothek kann enthalten:

- Makro-Zauber
- semantische Primitive
- Objektdefinitionen
- Materialdefinitionen
- Zielauswahlmuster
- geometrische Standardformen
- Transformationsroutinen
- Informationsverarbeitungsroutinen
- Sicherheitsprüfungen
- Stabilisierungsmuster
- visuelle Glyphenkomponenten

## Bibliotheksarten

| Typ | Inhalt | Beispiel |
|---|---|---|
| Primitive Library | Grundzeichen und elementare Operationen | Ziel, Richtung, Dauer, Bindung |
| Object Library | Definitionen physischer Objekte | Tür, Stein, Wasser, Klinge |
| Material Library | Materialklassen und Eigenschaften | Eisen, Glas, Holz, Blut |
| Spell Macro Library | vorgefertigte Zauberkomponenten | Lichtkugel, Barriere, Wärmeentzug |
| Safety Library | Schutz- und Fehlerprüfungen | Überhitzung vermeiden, Zielvalidierung |
| Geometry Library | Standardformen | Kreis, Linie, Kegel, Feld |
| Information Library | Such-, Filter-, Sortier- und Erkennungsroutinen | finde Metall, meide Hindernis |

## Verfügbarkeitsmodell

### Entscheidung: Hybridmodell

Grundprimitive sind immer verfügbar. Komplexe Makros und spezialisierte Definitionen müssen lokal vorhanden, gelernt oder importiert sein.

```text
Grundprimitive: systemisch verfügbar
häufige einfache Makros: lernbar / memorisierbar
komplexe Makros: lokal / gelernt / importiert
Spezialdefinitionen: lokal / importiert / über Artefakt verfügbar
Objektdefinitionen: teils allgemein, teils spezialbibliotheksabhängig
```

## Physische Repräsentationspflicht bleibt gültig

Auch wenn ein Makro memorisiert wurde, ersetzt dieses Wissen nicht die physische visuelle Repräsentation des Zaubers.

Ein gelernter Zauberer braucht nicht zwingend das ursprüngliche Buch oder die Schriftrolle, muss den Zauber aber in-world neu darstellen können, z. B. durch:

- Tinte auf Papier
- Kreide auf Stein
- Stock in Sand/Erde
- Gravur
- Tattoo
- Ritualkreis

## Memory-Slots

Für häufig verwendete Makros kann es begrenzte Memory-Slots geben.

### Funktion

Memory-Slots erlauben, bestimmte Makros ohne mitgeführte Referenzbibliothek korrekt zu reproduzieren.

Sie bedeuten nicht, dass der Zauber unsichtbar oder rein mental gewirkt wird.

```text
Memory-Slot = gelernte Reproduktionsfähigkeit
physische Zeichnung = weiterhin notwendige Ausführungsform
```

### Mögliche Begrenzungen

- maximale Komplexität
- Anzahl der Slots
- Übung/Skill-Anforderung
- Fehlerwahrscheinlichkeit bei beschädigtem Wissen
- Zeit zum Zeichnen/Rekonstruieren
- Abhängigkeit von bekannten Grundprimitiven

## Imports und Referenzen

Ein Zauber kann Bibliotheken referenzieren.

Beispielhafte Struktur:

```text
import geometry.circle
import material.water
import safety.thermal_limit

target := object.type("water_surface")
effect := thermal.lower_temperature(target)
shape := geometry.circle(radius=2m)
```

## Laufzeit- und Referenzfehler

Wenn eine Bibliothek fehlt oder während der Laufzeit unzugänglich wird, können Fehler entstehen.

| Fehler | Ursache | Mögliche Folge |
|---|---|---|
| Importfehler | Bibliothek nicht vorhanden | Zauber kompiliert nicht |
| Versionsfehler | falsche Bibliotheksversion | semantisch anderer Effekt |
| Referenzbruch | Trägermedium beschädigt/entfernt | Zauber bricht ab oder destabilisiert |
| Typfehler | Ziel passt nicht zur Objektdefinition | keine Wirkung oder Fehlwirkung |
| Sicherheitsfehler | Safety Library fehlt | Risiko von Überhitzung, Streuung, Rückkopplung |
| Memory-Fehler | Makro falsch erinnert oder unvollständig reproduziert | Syntax-/Semantikfehler |

## Objektdefinitions-Bibliotheken

Eine wichtige Funktion von Bibliotheken ist die Definition von Objektklassen.

Ohne solche Definitionen müsste jeder Zauber jedes Ziel extrem präzise neu beschreiben.

Beispiel:

```text
object.type("door")
```

könnte intern definieren:

- flaches bewegliches Bauelement
- meist aus Holz, Metall, Glas oder Verbundmaterial
- trennt zwei Räume
- besitzt Scharniere, Rahmen oder Schließmechanismus
- kann geöffnet, geschlossen, verriegelt, beschädigt oder verschoben werden

## Materialdefinitions-Bibliotheken

Materialbibliotheken definieren Eigenschaften und Zusammensetzungen von Stoffen und Materialien.

Beispiel:

```text
material.rock
```

könnte enthalten:

- Hauptbestandteile
- Dichte
- Härte
- Wärmeleitfähigkeit
- Bruchmodus
- typische Spurenelemente
- Reaktion auf Säuren/Laugen
- magnetische Eigenschaften

## Visuelle Einbindung

Bibliotheksreferenzen müssen in der visuellen Zaubersprache erkennbar oder codiert sein.

Mögliche Darstellung:

- Import-Ring
- Bibliotheks-Siegel
- eingebetteter Glyphenblock
- Referenzknoten im Zaubergraphen
- Randnotiz / Indexzeichen auf Schriftrolle
- Speicherzeichen für memorisierte Makros

## Offene Fragen

1. Wo liegt die Grenze zwischen Grundprimitive und importpflichtiger Bibliothek?
2. Wie werden Bibliotheksversionen behandelt?
3. Können Bibliotheken beschädigt, manipuliert oder gefälscht werden?
4. Können Zauber ohne Zugriff auf eine referenzierte Bibliothek weiterlaufen?
5. Wie werden Objektdefinitionen geprüft?
6. Wie komplex dürfen Memory-Slot-Makros sein?
7. Sind Bibliotheksreferenzen visuell sofort lesbar oder erst durch Analyse erkennbar?
