# 14 — Spell Libraries and References

Dieses Dokument beschreibt die frühe Theorie zu Zauberbibliotheken, Makros, Imports und Objektdefinitionen.

**Status:** Neues Arbeitsmodell / offene Grundsatzfrage

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

## Global vs. lokal

Die zentrale offene Frage lautet:

> Sind Bibliotheken global verfügbar, oder müssen sie lokal in der Spielwelt vorhanden sein?

### Modell A — Globale Bibliotheken

Bibliotheken sind überall abrufbar, sobald der Zauberer sie kennt oder freigeschaltet hat.

**Vorteile:**

- bequem
- weniger Inventarverwaltung
- leichter für Einsteiger

**Nachteile:**

- schwächt die physische Weltlogik
- kollidiert teilweise mit der Pflicht physischer Repräsentation
- weniger interessante Risiken bei beschädigten oder fehlenden Referenzen

### Modell B — Lokale Bibliotheken

Bibliotheken müssen physisch vorhanden sein, z. B. in Büchern, Schriftrollen, Artefakten, Zauberstäben, Tattoos oder Gravuren.

**Vorteile:**

- konsistent mit physischer Zaubersyntax
- erzeugt gutes Gameplay: stehlen, kopieren, beschädigen, verlieren, schützen
- Referenzfehler werden in-world plausibel

**Nachteile:**

- mehr Verwaltung
- möglicherweise sperrig für schnelles Zaubern

### Modell C — Gelernte Bibliotheken

Ein Zauberer kann Bibliotheken durch Training internalisieren.

**Vorteile:**

- Skill-Progression
- weniger Abhängigkeit von Inventar
- erklärt meisterhafte Zauberer

**Nachteile:**

- braucht klare Grenze zur physischen Repräsentationspflicht
- darf nicht zu unsichtbarer Wunschmagie werden

### Modell D — Hybridmodell

Grundprimitive sind immer verfügbar, komplexe Makros und spezialisierte Definitionen müssen lokal vorhanden, gelernt oder importiert sein.

**Vorläufige Empfehlung:** Hybridmodell.

```text
Grundprimitive: systemisch verfügbar
komplexe Makros: lokal / gelernt / importiert
Objektdefinitionen: teils allgemein, teils spezialbibliotheksabhängig
```

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

## Visuelle Einbindung

Bibliotheksreferenzen müssen in der visuellen Zaubersprache erkennbar oder codiert sein.

Mögliche Darstellung:

- Import-Ring
- Bibliotheks-Siegel
- eingebetteter Glyphenblock
- Referenzknoten im Zaubergraphen
- Randnotiz / Indexzeichen auf Schriftrolle

## Offene Fragen

1. Wo liegt die Grenze zwischen Grundprimitive und importpflichtiger Bibliothek?
2. Sind Bibliotheken global, lokal, gelernt oder hybrid verfügbar?
3. Wie werden Bibliotheksversionen behandelt?
4. Können Bibliotheken beschädigt, manipuliert oder gefälscht werden?
5. Können Zauber ohne Zugriff auf eine referenzierte Bibliothek weiterlaufen?
6. Wie werden Objektdefinitionen geprüft?
7. Kann ein Zauberer Bibliotheken auswendig lernen, ohne die physische Repräsentationspflicht zu brechen?
8. Sind Bibliotheksreferenzen visuell sofort lesbar oder erst durch Analyse erkennbar?
