# Raw Notes

Dieses Dokument dient als Eingangsspeicher für ungeordnete Rohnotizen.

## Arbeitsweise

Rohnotizen werden zunächst hier gesammelt und anschließend nach folgenden Kategorien ausgewertet:

- **Festgelegt:** aktuelle Projektregel oder Designentscheidung
- **Hypothese:** plausible, aber noch nicht bestätigte Annahme
- **Offene Frage:** ungeklärter Punkt
- **Widerspruch:** logisch kollidierende Ideen
- **Feature:** spätere Funktion für Prototyp, Simulation oder Spiel
- **Begriff:** zentraler Terminus, der definiert werden muss
- **Beispiel:** konkreter Zauber, Effekt oder Anwendungsfall

## Eingang 2026-07-06

```text
- Magie formularisch generalisieren, sodass jeder beliebige Zauber den man sich ausdenken kann in einer Gleichung ausgedrückt werden kann:

- ATP (Adenosintriphosphat, die Energie-Grundeinheit biologischen Lebens) für Magie verbrauchen?

- Belastung physischer Bewegungszauber auf ganzen Körper verteilen?
- Kognitive Zauber auf ganzen Verstanden verteilen?
(Diese Art von „Anstrengung“ als „Mana“ interpretieren?); Beispiel: schweren Stein gemeinsam heben - Kräfte werden auf alle beteiligten Zauberer verteilt. Für Magie die mehr Kraft beansprucht müssen externe „Mana“-Quellen verwendet werden (Kristalle oder Ähnliches als Energie-Speicher) die der Magier bei sich tragen muss oder die ihm zumindest zugänglich sein müssen.

- die Ausführung einer physischen Manipulation über einen Zauberspruch ist genauso "anstrengend" wie die Ausführung dieser Manipulation mit dem physischen Körper. Entsprechend sind "Action at a distance" Typ Manipulationen so anstrengend wie die physische Manipulation mit einem Hebel der selben Länge (ergo, weiter weg = anstrengender).

- Zauberstäbe können wie "Linsen" für Magie agieren (ergo gleiche Manipulation effizienter) oder mit gleichem Energie-Aufwand höherer Wirkungsgrad. Grundsätzlich kann auch einfach nur mit dem physischen Körper gezaubert werden; dies ist schlichtweg weniger präzise (kann durch regelmäßige Übung bis zu einem gewissen Grad verbessert werden). Zaubern mit maximaler Erfahrung ohne Zauberstab wird immer weniger effizient oder wirksam als Zaubern mit maximaler Erfahrung mit Zauberstab sein.

-In der Praxis sollten Zauberstäbe eingebaute Mana-Speicher-Medien enthalten (z.B. einen austauschbaren/wiederaufladbaren Kristall). Dadurch können Magier effizient auf eine externe Mana-Quelle zugreifen und damit "mehr" durch Zauber bewirken, als sie es rein mit ihrem Körper tun könnten.

- Zaubern wird, wie das Trainieren von Muskeln oder Denkprozessen, mit dem Üben schneller/einfacher/effizienter. Gleichzeitig wird die Zauberfähigkeit durch entsprechende Abstinenz wieder schwächer (Zauber-Atrophie)

- Das Ausüben von Magie unterliegt den Gesetzen der Thermodynamik. Energie/Materie kann nicht geschaffen/zerstört, sondern lediglich in unterschiedliche Formen überführt werden. Das Ausführen von Magie erzeugt Abwärme und unterliegt der Carnot-Effizienz. Dies limitiert in der Praxis wie lange/mächtig Magie auf Dauer ausgeübt werden kann. Prozesse wie chemische Transformationen (Eisenoxid in Eisen und Sauerstoff aufteilen) / Phasenübergange (Wasser in Eis verwandeln) verbrauchen (mindestens) genauso wie viel Mana/Energie wie die entsprechende Enthalpie in Joule.

- Magische Rituale können Objekte verwenden, die Mana gespeichert haben oder durch "Aktivierung" vorformulierte Zaubersprüche ausführen / mit dem verfügbaren Mana aufrecht erhalten können.

- Bei physischen/chemischen Manipulationen die Abwärme produzieren wird diese grundsätzlich erst mal möglichst "faul" radial abgeleitet. Eine Lenkung von Abwärme ist als zusätzlicher Prozess zu betrachten der ebenfalls wieder Mana verbraucht und auch Abwärme verursacht (wie z.B. eine Art Wärmepumpe).

---------------

- Programming as incantations: bezüglich Artem‘s und meiner Idee des Magie-Systems: wir sollten das System selbst hardcoden, aber die Zauberspruch-Umsetzung dann von einem LLM machen lassen! (Für die Ästehtik/als Verschlüsselungs-Mechanik könnte das ganze dann noch mit kryptischen Zeichen präsentiert werden)

--------------

- Brainstorming Session mit Artem 06.07.26: Falls "Magie" im Kontext eines Videospiels/digitaler Umgebung prozedural bzw. von einer KI auf Basis einer Text-Beschreibung erzeugt wird sind folgende Dinge zu beachten. Im Prinzip sollte die KI auf Basis der natürlich-sprachigen Beschreibung Zugriff auf eine "Bibliothek" mit den kleinstmöglichen, semantischen Komponenten des Zaubers haben, deren Umfang von der Präzision bzw. dem Umfang der physikalischen Regeln der digitalen Umgebung abhängig ist. Sprich, je mehr physikalische Komponenten eine Engine modeliert, desto mächtiger können Zaubersprüche sein.
Zusatz-Idee:
- Bei einer hinreichend granularen physics-Engine wird es schnell schwierig jeden impliziten Aspekt eines Zaubers bzw. des Verhaltens eines geschaffenen Objekts zu berücksichtigen. Daher sollte die Schaffung von Zauber einen "Genie"-Slider haben; sprich man sollte angeben können wir sehr die Resultate der natürlichsprachigen Beschreibung supplementiert werden sollten. Entweder null/minimal, sprich der Zauber macht wirklich nur das was man beschreibt, nicht mehr, oder stark, sprich die KI überlegt was popkulturell gemeint sein könnte/berücksichtigt werden sollte und macht einen entsprechenden Vorschlag oder implementiert diesen direkt.
- Wenn Physics objects geschaffen werden (eine KI erzeugt eine Mesh), setzen wieder die physikalischen Gesetzt der Umgebung das Limit der Interagierbarkeit.
- die zaubersprache sollte wie bei Witch Hat Atelier eine visuelle Darstellung mit den kleinstmöglichen semnatischen Komponenten haben (mit KI zusammen überlegen was diese Komponenten sein sollten)
- Ein Protoytp/Proof of Concept sollte vielleicht in 2D anfangen, da 3D deutlich komplexer ist.
- Als allererstes Gedanken darüber machen, welche Game Engine dafür verwendet werdne könnte; dann GitHub Seite anlegen? Die Engine-Wahl bzw. das Github-Projekt sollte auch schon die notwendigen Kriterien für eine Umsetzung als Steam-Spiel berücksichtigen.
- mana-System? / Spells sollten sowohl custom/granular erstellbar sein, als auch über eine Bibiliothek von bereits zusammengestellten / auf höherer Abstraktionebene erstellten Komponenten programmierbar sein. Diese sind weniger Mana-effizient, aber natürlich schneller zusammenstellbar.

- conservation of Energy / mass / Momentum (+any process is lossy and creates waste heat); also conservation of "Mana" as the magical equivalent for energy (maybe also mana waste "heat")?
```