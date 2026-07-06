# 07 — Design Decisions

Dieses Dokument hält getroffene Designentscheidungen fest.

Ziel ist, spätere Änderungen nachvollziehbar zu machen und nicht dieselben Grundfragen mehrfach neu zu diskutieren.

## Format

```md
## DD-000 — Titel

**Datum:** YYYY-MM-DD  
**Status:** Festgelegt / Ersetzt / Verworfen  
**Kontext:** Warum stand die Entscheidung an?  
**Entscheidung:** Was wurde entschieden?  
**Begründung:** Warum wurde so entschieden?  
**Folgen:** Was ergibt sich daraus?
```

## Entscheidungen

### DD-001 — Projektstruktur wird modular dokumentiert

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Das Projekt soll nicht in einer chaotischen Sammeldatei wachsen, sondern versionierbar und logisch gegliedert sein.

**Entscheidung:**  
Das Repository verwendet eine modulare Struktur mit `docs/`, `notes/`, `prototype/` und `issues/`.

**Begründung:**  
Theorie, Rohnotizen, technische Experimente und Arbeitsaufgaben müssen getrennt bleiben, damit das System langfristig wartbar bleibt.

**Folgen:**  
Neue stabile Inhalte werden in passende `docs/`-Dateien überführt. Unsortierte Gedanken bleiben zunächst in `notes/raw_notes.md`.

### DD-002 — Zauber müssen ableitbar sein

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Das System soll sich von klassischer Fantasy-Magie unterscheiden, in der Zauber oft als feste Einzelaktionen existieren.

**Entscheidung:**  
Ein Zauber darf nicht einfach existieren, sondern muss aus kleineren Komponenten logisch ableitbar sein.

**Begründung:**  
Nur dadurch wird Magie programmierbar, simulierbar und systematisch erweiterbar.

**Folgen:**  
Konkrete Zauber wie Feuerball, Barriere oder Heilung gelten zunächst nur als Beispiele. Sie müssen später aus Ontologie, Syntax, Operatoren, Modifiern und Kostenmodell konstruiert werden.

### DD-003 — Mana ist ein abstrakter Energie-/Arbeitsbegriff, keine konkrete Substanz

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Die Rohnotizen verwendeten Mana teils als ATP-nahe biologische Energie, teils als körperliche Anstrengung, teils als externe Kristallenergie und teils als allgemeines Energieäquivalent.

**Entscheidung:**  
Mana wird vorläufig als abstrakter Abrechnungsbegriff für magische Energie bzw. magische Arbeit behandelt, vergleichbar mit Joule als Maßeinheit für Arbeit/Energie. Mana ist keine konkrete Substanz.

Biologische Energie, chemisch gebundene Energie, Kristalle, Artefakte oder andere Speicher sind **Quellen** bzw. **Speichermedien** für Mana, nicht Mana selbst.

**Begründung:**  
So bleibt das System offen für biologische und nicht-biologische Energiequellen. ATP bzw. chemisch/biologisch gebundene Energie kann als in-world-Erklärung dafür dienen, warum Lebewesen Mana bereitstellen können, ohne Mana selbst auf ATP zu reduzieren.

**Folgen:**  
Der Begriff „kognitives Mana“ wird verworfen bzw. nicht als eigener Mana-Typ verwendet. Kognitive Arbeit, Konzentration und Verständnis sind stattdessen Kontroll- oder Ausführungsflaschenhälse, nicht die magische Energie selbst.

### DD-004 — Naturgesetze und Erhaltungssätze bleiben gültig

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Das System soll sehr mächtige und unintuitive Effekte erlauben, aber nicht in beliebige Wunschmagie abrutschen.

**Entscheidung:**  
Massen-, Energie- und Impulserhaltung bleiben grundsätzlich gültig. Magie darf keine Energie oder Masse aus dem Nichts erschaffen oder vernichten.

Magie darf jedoch ungewöhnliche Transformationspfade ermöglichen, sofern Quellen, Senken, Kosten und Nebenprodukte berücksichtigt werden.

**Begründung:**  
Strenge Erhaltungsgesetze machen das System berechenbar, begrenzbar und simulierbar. Gleichzeitig bleiben viele magisch wirkende Effekte möglich, z. B. Illusionen als Lichtprojektionen, Blei-zu-Gold als extrem energieintensive nukleare Transformation oder zeitähnliche Effekte als präzise Vektor-/Zustandsmanipulation.

**Folgen:**  
„Unmögliche“ Zauber sind nicht deshalb verboten, weil sie fantastisch wirken, sondern weil ihnen Energiequelle, Materiequelle, Impulsbilanz, Zieldefinition oder gültige Transformationslogik fehlt.

### DD-005 — LLM/Genie ist Hilfsmittel, nicht Regelautorität

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Ein LLM kann beim Erstellen komplexer Zauberprogramme helfen, könnte aber ohne Begrenzung die formale Strenge des Systems unterlaufen.

**Entscheidung:**  
Ein LLM bzw. Genie-System darf nur als Hilfsmittel zum Erstellen, Ergänzen oder Übersetzen von Zauber-Syntax dienen. Die Regelengine bleibt autoritativ.

**Begründung:**  
Das entspricht der Nutzung eines LLMs beim Programmieren: Es kann Code vorschlagen, erklären und vervollständigen, aber syntaktisch oder semantisch falscher Code kompiliert bzw. läuft nicht korrekt.

**Folgen:**  
Der Genie-Slider ist ein Komfort-/Kontroll-Kompromiss. Je stärker das Genie ergänzt, desto bequemer wird die Zaubererstellung, aber desto weniger direkte Kontrolle hat der Spieler über die genaue Ausführung.

### DD-006 — Makro-Zauber sind Komfortschichten mit emergenter Effizienz

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Zauber sollen sowohl granular selbst programmiert als auch über vorgefertigte Komponenten/Makros zugänglich sein.

**Entscheidung:**  
Makros sind höhere Abstraktionsebenen über der eigentlichen Zaubersyntax. Ihre Effizienz wird nicht künstlich durch einen pauschalen Modifier gesetzt, sondern ergibt sich aus Overhead, Generalität, Sicherheitslogik und Situationspassung.

**Begründung:**  
Ein generisches Einsteiger-Makro ist oft weniger effizient, weil es mehr Fälle absichert und unnötigen Overhead enthalten kann. Ein hand- oder situationsspezifischer Custom-Zauber kann effizienter sein, weil er exakt auf das Zielproblem zugeschnitten ist.

**Folgen:**  
Effizienz ist ein emergentes Phänomen der Zauberstruktur. Experten-Makros können sehr effizient sein, wenn sie gut optimiert sind; Einsteiger-Makros sind eher robust und bequem als optimal.

### DD-007 — Zauber benötigen eine physische visuelle Repräsentation

**Datum:** 2026-07-06  
**Status:** Festgelegt  

**Kontext:**  
Die Zaubersprache soll nicht nur abstrakte Datenstruktur sein, sondern innerhalb der Spielwelt als visuelle Programmiersprache existieren.

**Entscheidung:**  
Jeder ausführbare Zauber benötigt innerhalb der Spielwelt eine physische, visuelle Repräsentation, z. B. Schriftrolle, Buch, Gravur, Zeichnung, Ritualkreis oder magisches Tattoo.

Auch vokalisierte Zauber benötigen irgendwo am Körper oder in der Nähe des Zauberers eine kompatible physische Repräsentation.

**Begründung:**  
Dadurch bleibt Magie eine sichtbare, prüfbare und manipulierbare Syntax statt unsichtbarer Willenskraft. Das stärkt sowohl Systemlogik als auch Gameplay.

**Folgen:**  
Technisch kann ein Zauber intern als Datenstruktur modelliert werden, muss aber in eine regelkonforme visuelle Darstellung übersetzbar sein. Umgekehrt muss eine korrekt gezeichnete Darstellung durch Parser/Regelengine in ausführbare Zauberlogik übersetzt werden können.
