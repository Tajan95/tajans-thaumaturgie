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

### DD-008 — Zauberbibliotheken verwenden ein Hybridmodell

**Datum:** 2026-07-08  
**Status:** Festgelegt  

**Kontext:**  
Komplexe Zauber benötigen wiederverwendbare Definitionen, Makros und Objekt-/Materialbeschreibungen. Gleichzeitig soll die physische Repräsentationspflicht erhalten bleiben.

**Entscheidung:**  
Zauberbibliotheken verwenden ein Hybridmodell:

- Grundprimitive sind systemisch verfügbar.
- Häufige einfache Makros können memorisiert werden.
- Komplexe Makros und Spezialdefinitionen müssen lokal vorhanden, gelernt oder importiert sein.
- Objekt- und Materialdefinitionen können teils allgemein verfügbar, teils spezialbibliotheksabhängig sein.

**Begründung:**  
Das Modell verbindet Spielbarkeit mit Weltlogik. Spieler müssen nicht jedes Grundzeichen ständig physisch importieren, aber komplexe Wissensstrukturen bleiben materiell, lernbar, verlierbar, kopierbar, fälschbar und angreifbar.

**Folgen:**  
Memory-Slots können häufig verwendete Makros ohne mitgeführte Referenzbibliothek reproduzierbar machen. Trotzdem muss jeder Zauber weiterhin physisch/visuell dargestellt werden, z. B. durch Zeichnen, Schreiben, Gravieren oder Tattoos.

### DD-009 — Standardmagie ist materiegebunden

**Datum:** 2026-07-08  
**Status:** Festgelegt  

**Kontext:**  
Am Beispiel eines schwebenden Lichtzaubers stellte sich die Frage, ob Magie direkt elektromagnetische Wellen, Photonen, Magnetfelder oder Felder im Allgemeinen erzeugen darf, oder ob sie primär auf vorhandene Materie wirken muss.

**Entscheidung:**  
Standardmagie ist zunächst materiegebunden. Magie darf direkt auf vorhandene Materie und deren Zustände wirken, z. B. Position, Geschwindigkeit, Temperatur, Phase, Druck, chemische Bindung, Ladungsverteilung oder Zusammensetzung.

Kontaktlose Kraftvektoren auf Materie sind erlaubt, sofern Zielbezug, Reichweite, Energieaufwand, Impulsbilanz und Fehlerbedingungen erfüllt sind.

Direkte Feld-/Wellenmanipulation, z. B. substratlose Licht-, Magnetfeld- oder EM-Wellen-Erzeugung, bleibt als spätere High-Level-Interventionsklasse möglich, wird aber nicht als Standardmagie angenommen.

**Begründung:**  
Diese Entscheidung hält die Materialität der Welt als primäre Simulationsgrundlage stabil. Die meisten gewünschten magischen Effekte bleiben möglich, müssen aber über Materie, Zustände, Energiequellen und Erhaltungssätze konstruiert werden.

**Folgen:**  
Ein einfacher Lichtzauber braucht eine materielle Basis, z. B. ionisierte Luft, Plasma, erhitzte Partikel oder ein glühendes Medium. Ein Schwebezauber wirkt als Kraft-/Impulsmanipulation auf ein materielles Ziel. Direkte Photonen- oder Feldmanipulation wird nicht ausgeschlossen, aber als spätere, schwierigere Erweiterung behandelt.

### DD-010 — Mana nutzt ein thaumisches Feldpotential realer Energiequellen

**Datum:** 2026-07-08  
**Status:** Festgelegt  

**Kontext:**  
Mana war bereits als abstrakter Energie-/Arbeitsbegriff und nicht als konkrete Substanz festgelegt. Offen blieb aber, wie biologische, chemische, mechanische, elektrische oder andere Energiequellen in-world greifbar zu magischer Arbeit werden, ohne eine separate Mana-Maschine oder Mana-Partikel einzuführen.

**Entscheidung:**  
Jede reale physikalische Energiequelle bzw. jedes reale Energiepotential kann ein gekoppeltes thaumisches Analog besitzen. Dieses thaumische Potential ist keine zusätzliche Energiequelle, sondern eine magisch adressierbare Kopplungs- und Übertragungsebene für reale Energie.

```text
physikalisches Energiepotential
→ gekoppeltes thaumisches Potential
→ Zaubergeometrie koppelt daran
→ magische Arbeit
→ physikalische Quelle entlädt sich + Verluste
```

Mana bezeichnet die nutzbare magische Arbeit bzw. den nutzbaren thaumischen Arbeitsfluss, der über diese Kopplung verfügbar ist.

Mana-Partikel, Mana als eigenes chemisches Element oder Mana als eigenständige Substanz werden als Standardmodell verworfen.

Mana-Speicher enthalten keine Mana-Substanz, sondern halten metastabile thaumische Potentialzustände, vergleichbar mit Kondensatoren, Batterien oder gespannten Feldkonfigurationen.

Physische Zauberrepräsentationen sind nicht nur Symbole, sondern reale Kopplungsstrukturen. Sie wirken wie Antennen, Linsen, Ventile, Transformatoren, Schaltkreise oder Richtungsweiser für thaumische Potentiale.

**Begründung:**  
Dieses Modell bewahrt Erhaltungssätze, erklärt aber trotzdem, warum beliebige reale Energiequellen als Mana-Quellen dienen können. Es macht Zaubergeometrien, Fokusmedien, Artefakte und Mana-Speicher systemisch bedeutungsvoll, ohne zusätzliche Teilchenphysik einzuführen.

**Folgen:**  
Eine thaumische Entladung entlädt immer auch ihr physikalisches Analog. Körpermagie bleibt möglich, solange biologische Energie verfügbar ist, wird aber durch Erschöpfung, Unterzuckerung, Überhitzung und Gewebeschaden begrenzt. Große Zauber benötigen entweder hohe Effizienz, vorhandene Umweltpotentiale, geladene Artefakte oder Infrastruktur.

Aus dem Modell ergeben sich emergente Spiel- und Weltrollen: Kampfzauberer tragen leistungsfähige Speicher oder Foki, Stealth-Zauberer nutzen effiziente kleine Eingriffe, Ritualmagier arbeiten mit stationären Quellen, und Infrastrukturmagier koppeln Zauber an Maschinen, Turbinen, Kraftwerke oder vorbereitete Speicher.

Details siehe: `docs/23_mana_and_thaumic_field_model.md`.

### DD-011 — Zaubergeometrie koppelt material- und grenzflächenabhängig

**Datum:** 2026-07-09  
**Status:** Festgelegt  

**Kontext:**  
Nach DD-010 sind physische Zauberrepräsentationen reale Kopplungsstrukturen für thaumische Potentiale. Offen blieb, ob diese Repräsentationen zwingend aus einem thaumisch leitfähigen Spezialmaterial bestehen müssen, oder ob jede stabile Geometrie in bzw. auf Materie ausreicht.

**Entscheidung:**  
Zaubergeometrie kann additiv, subtraktiv oder hybrid realisiert werden.

```text
Additiv:
  Material wird aufgetragen, z. B. Tinte, Kreide, Asche, Metallpulver.

Subtraktiv:
  Material wird entfernt, verdrängt oder verformt, z. B. Kratzer, Gravur, Furche, Rille, Hohlraum.

Hybrid:
  Subtraktive Form wird mit leitfähigem, stabilisierendem oder speicherndem Material gefüllt oder beschichtet.
```

Spezialtinte oder thaumisch optimiertes Linienmaterial ist nützlich, aber nicht zwingend. Entscheidend ist eine stabile, präzise und materiell realisierte Geometrie.

```text
Geometrie bestimmt Gültigkeit.
Material bestimmt Kopplungsqualität.
```

Negative Zaubergeometrien funktionieren nicht, weil Luft ein guter thaumischer Leiter wäre. Normale Luft gilt im Standardmodell eher als schwaches Füll- und Zwischenmedium. Der Kopplungseffekt negativer Geometrien entsteht primär durch Material-Luft-Grenzflächen, Hohlraumform, Kantenpräzision, geometrische Kontinuität und Trägermaterialstabilität.

**Begründung:**  
Dieses Modell erhält improvisierte Magie, Gravuren, Ritzungen, Kreidekreise, Runensteine und Artefakte, ohne Materialeigenschaften zu entwerten. Hochwertige Materialien verbessern Kopplung, Entladerate, Stabilität und Sicherheit, sind aber keine absolute Voraussetzung für jeden einfachen Zauber.

Luft wird bewusst nicht als guter thaumischer Leiter definiert, weil sonst die gesamte Atmosphäre zu einem ständig verfügbaren thaumischen Leitmedium würde. Das würde Fernwirkung, Streuung, Leckage und Materialgrenzen schwerer kontrollierbar machen.

**Folgen:**  
Ein in Erde gezogener Kreis kann grundsätzlich funktionieren, ist aber schwach, instabil und störanfällig. Eine präzise Gravur in Stein ist dauerhafter. Metallische oder kristallhaltige Linien können stärkere Kopplung erlauben, erhöhen aber ggf. Überlastungs- oder Rückkopplungsrisiken.

Materialwahl beeinflusst Kopplungseffizienz, maximale Entladerate, Stabilität, Leckage, Überlastungsrisiko und Fehlerverhalten.

Details siehe: `docs/24_spell_geometry_and_material_coupling.md`.

### DD-012 — Zauber besitzen eine Start-Glyphe mit Default-Sofortausführung

**Datum:** 2026-07-13  
**Status:** Festgelegt  

**Kontext:**  
Für Issue #2 muss geklärt werden, wie Zauber als ausführbare Programme beginnen. Gleichzeitig soll die Zaubersprache Spieler nicht durch unsichtbare Sicherheitsannahmen entlasten: Verzögerungen, Bedingungen, Trigger und Failsafes sollen explizite syntaktische Bestandteile sein.

**Entscheidung:**  
Jeder ausführbare Zauber besitzt mindestens eine Start-Glyphe bzw. einen Aktivierungsknoten.

Ohne zusätzlichen Start-Modifier gilt der Default:

```text
on_complete_execute_once
```

Das bedeutet: Sobald die Start-Glyphe vollständig und gültig fertiggestellt ist, versucht der Zauber, sich einmal auszuführen.

Abweichende Start- oder Ausführungslogik muss explizit codiert werden, z. B. Vokalisierung, Gestik, Umweltbedingung, Verzögerung, Scharfschaltung, Halten, Toggle, Dauerlimit, autonome Quellenbindung, Wiederholung oder Failsafe.

**Begründung:**  
Dieses Modell macht die Zaubersprache konsequent programmatisch. Der einfachste Zauber verhält sich wie ein unmittelbar ausgeführtes Programm, während vorbereitete, sichere oder komplexe Zauber zusätzliche Start-/Stop-Logik explizit mitführen müssen.

Dadurch bleiben Makros und Anfängerzauber bequem, weil sie Sicherheitsmechanismen enthalten können, ohne dass diese als unsichtbare Systemannahmen gelten.

**Folgen:**  
Die interne Zauberstruktur braucht ein Activation-/Termination-Modell. Die visuelle Sprache muss Start-Glyphen, Trigger-Marker, Ausführungsmodi, Ressourcenbindung, Stop-Marker und Sicherheitsknoten darstellen können.

Der Spell Editor muss diese Logik sowohl visuell als auch textuell sichtbar machen. Besonders gefährliche Modi, z. B. autonomer Quellenlauf ohne Limit, sollten als Risiko erkennbar sein.

Details siehe: `docs/spell_system/spell_lifecycle_and_activation.md`.
