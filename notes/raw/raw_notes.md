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

## Eingang 2026-07-07

```text
- rein vokalisierte Zauber? Müssen Zauber immer eine physische Komponente haben (also Speicher-Medium, wie ein Artefakt, Zauberstab, gemalter Zauberkreis etc.) oder können sie auch rein "somatisch" gewirkt werden und dann durch Gestikulation/Vokalisierung getriggert werden?

- da Zauber sehr komplex werden können bzw. aus sehr granularen Komponenten bestehen sind für die Praxis meistens Makros sinnvoll(notwendig, sprich, vorgefertigte Zauber-Komponenten, die in irgendeiner Art "Bibliothek" gespeichert werden können (ähnlich einer Funktionen-Library beim Programmieren), welche irgendwie referenziert/importiert werden kann. Die Frage ist dahingehend ob diese "Bibliotheken" irgendwo global referenziert werden/überall abrufbar sind, oder lokal beim Spieler/Zauberer irgendwo hinterlegt sein müssen (in Form von mitgetragenen Bücher/Schriftrollen/Artefakten), damit ein lokal ausgeführter Zauber auf diese zugreifen kann, damit der Zauber korrekt ausgeführt werden kann?
(Es wäre alleine schon sehr nützlich, wenn Bibliotheken für das refernzieren physischer Objekte existiert, damit ein Zauber, der auf ein Objekt wirken soll, nicht jedes mal erst in juristischer Feinarbeit definieren muss, was ein gegebenes Objekt überhaupt ist, sondern die Definition einfach aus einer Bibliothek beziehen kann).

- die Zaubersprache sollte eine klare visuelle Repräsentation besitzen (noch nicht sicher ob ein Diagramm, Graph, etc - am ehesten an WicthHat Atelier mit seinen Zauberkreisen orntieren), sodass ein erfahrener Zauberer selbst ohne die direkte Beschreibung der Wirkung eines Zaubers rein visuell erahnen kann, was eine Zaubervisualisierung (oder ein Artefakt, auf das sie eingraviert/gemalt ist) bewirken wird.
```

## Eingang 2026-07-08

```text
- game engine Wahl?

- Feedbacke Schleife mit Rückfragen`?

- falls Mana im biologischen Kontext ATp sein sollte so würden sich so etwas wie Tier- oder Menschenopfer als Quelle biologischen Manas für ein gegebenes Ritual natürlich ergeben. Zwar ein morbides Beispiel, aber es wäre irgendwie elegant wenn sich popkulturelle Darstellungen von Zauberei emergent aus dem feinbeschriebenen Magie-System ergeben.

-Docs-S-Code für graphische Darstellung?

- 2D Welt, links nach rechts? Verschiedene Level um verschiedene Spell-Makros kennen zu lernen
Normale Energie-Quellen sollten Mana übertragbar sein / Mana in normale Energie

- Welt Block bzw. Pixel-basiert? Komposit-Materialien (wie z.B. Stein = Silizium + Sauerstoff + Spuren-Elemente) werden dann als homogene Masse angezeigt (bis zu dem Punkt dass sie getrennt werden sollten)

- Materialzusammensetungen/ Elemente/Fraktionen (Benennung von bestimmten Materialen/Element-Mischungen, jede heweils mit bestimmten Attributen und Werten für bestimmte Parameter wie Dichte, Leitfähigkeit etc.)

- vier Phasen (Gas, Flüssigkeit, Feststoff, Plasma) (Feuer ist kein Grundelement; magisches Feuer = Plasma)

- Magnetfelder / Strom

- Säuren/ Laugen

- Einfluss der Größe von gemalten Zaubern auf Artefakte? Mana-Penalty wenn deutlich kleiner als Objekt?

-  Beispiel für schwebendes Licht könnte sein: schwebendes Magnetfeld + Luft-Plasma? Oder direkt Lichtwellen? (Braucht es eine materielle Quelle wie ein Stück Metall das sich aufheizen und leuchten kann, oder können Lichtwellen quasi einfach so entstehen? Quasi die Frage ob Lichterzeugung ein Medium braucht (wie Luft) oder auch in einem Vakuum entstehen kann/direkte Lichtwellenerzeugung? Sprich Grundsatzfrage, was kann Magie? Nur energetischer Einfluss auf Materie oder direkte Erzeugung intrinsischer physikalischer Phänomene?)

- „Material-Zusammensetzung-Analyser“ als inherente Fähigkeit des Spielers oder ein eigener Spell?
2D Welt in zwei oder drei Ebenen?

- information processing spell components should be cheaper than movement/transformation spell components? (Eg. Flying lamp that avoids collision - the avoidance part is a information processing spell component or short, a intelligence spell component. Also in this category are things like seeking, sorting, collecting, separating, repelling, attracting etc.)

- Elements that should exist:
Every material (composed of substances, composed of elememts) should have attributes like hardness, density, conductivity, flammability, susceptibility to acids/bases, magneticism, reflectivity, bounciness, flexibility, friction, viscosity (if liquid), freezing/boiling point, breaking mode (splintering, tearing, crumbling, deforming, exploding), chemical energy/reactivity (or maybe more general, electronegativity) - there should be both a element catalogue (not all elements, useful functional cutoff) and a material/substance catalogue (pragmatically chosen; things like wood, rock, photosynthetic tissue, meat, oil, water, air, sand, soil, magma, etc.)
The elements I would include are: hydrogen, (maybe helium), argon, carbon, nitrogen, phosphoros, oxygen, sulfur, chlorine, sodium, (maybe calcium; correction: definitive - for stoff like limestone, needed for cement), (maybe magnesium, for Chlorophyll), iron, copper, silver, gold, platinum, lead, (maybe mercury), uranium, (maybe aluminium or titanium?), (maybe lithium), silicon, (maybe fluorine), (maybe potassium), (maybe tin, maybe zinc), (maybe tungsten).

- Es muss eine erweiterbare Liste natürlicher Objekte geschaffen wird, die aus heterogenen Materialen und nicht rein-elementaren Stoffen, sondern molekularen Stoffen bestehen. Einfaches Beispiel: Gestein. Betseht hauptsächlich aus Quarz (Silizium + Sauerstoff) + metallische oder ionische Spuren-Elemente wie Eisen, Kupfer, Silber, Gold, Platin, NaCl); komplexes Beispiel: Baum. Materialklassen: photosynthetisches Gewebe, Meristem, Holz, Rinde

- damit der Spieler nicht überfordert wird könnten die Elemente bei der Analyse nacheinander eingeführt werden (z.B. hieße es bei Luft am Anfang „Zusammensetzung: 78% Stickstoff, 21% Sauerstoff, 2% unbekannter Rest)

- Bezüglich der Volumina von Stoffen die weniger als 1 Pixel einnehmen sollten: (wenn z.B. Luft, die im Spiel aus z.B: ca. 78% Stickstoff, 20% Sauerstoff, 1% Argon, 1% Wassergas und ca. 0,05% CO2 bestehen könnte, notwendiger Weise den CO2 Anteil bei einer Trennung der Stoffe in weniger als einem Pixel darstellen müsste, könnte man einfach programmieren, dass Stoff, die weniger als 1 Pixel einnehmen müssten, dennoch 1 Pixel einnehmen, sich jedoch diesen Raum gleichzeitig mit anderen Stoffen teilen können, die ebenfalls weniger als ein 1-Pixel-Volumen einnehmen. Wenn z.B. Ein gegebenes Volumen Gestein, bei einer Magischen Auftrennung nach Stoffgemischen (nicht zwangsweise direkt nach Elementen) aufgeteilt wird, und z.B. zu 4 Tausendsteln aus Gold und 2 Tausendsteln aus Platin bestünde, dann würde dieser bei der Aufteilung das selbe Pixel-Volumen einnehmen, könnten jedoch bei einer weiteren Auftrennung auch jeweils 1 eigenes Pixel-Volumen aufnehmen, welche jedoch miteinander keine Kollision hätten und sich "decken" könnten solange ihr jeweiliges gemeinsames Volumen weniger als 1 Pixel-Volumen ist.

- muss mir grundsätzlich noch Überlegen wie die "Materialauflösung" der Welt umgesetzt werden soll. Am liebsten wäre mir (für die 2D-Version) eine Pixel-basierte Welt (mit flüssigen Bewegungsvektoren; sprich nicht einfach nur lineare Bewegungen entlang x/y-Achse), in der alle Materialien manipulierbar/bewegbar/zerstörbar und transformierbar sind; jedoch muss ich mir gut überlegen wie ich das Ganze gut optimiere, damit Ereignisse wie Explosionen das Spiel nicht sofort crashen weil sich sehr viele Pixel mit plötzlich großen Vektoren bewegen und es viele Kollisionen (potentiell auch Transformationen) zu berechnen gibt. Da Spiele wie Enschrouded oder Teardown dieses Problem jedoch scheinbar auch ganz gut in den Griff bekommen haben, bin ich zuversichtlich, dass das in 2D auch gut umsetzbar sein sollte.

- kleine Ergänzung bezüglich Zauber-Bibliotheken bzw. der physischen Repräsentation von Zauber: fairerweise sollten Spieler für häufig verwendete Zauber-Makros (vielleicht nur bis zu einer bestimmten Komplexität) eine gewisse Anzahl an "Memory-Slots" haben; sprich die Zauber sind "gemerkt" und können ohne das Vorhandensein physischer Refernz-bibliotheken wie SChriftrolle/Bücher gecastet werden, indem sie z.B. mit Tinte auf Papier gemalt oder mit einem Stock in Sand/Erde gezeichnet werden. Das würde eine faire Addition zu der Möglichkeit sein komplexer Zauber-Makros eintättowiert zu haben, wenn man diese ohne physische Referenz-Bibliothek casten möchte.

- bezüglich der Verteilung von Wärme/Flüssigkeiten/Gasen in der Welt: Es sollte mir bestimmten Cutoffs gearbeitet werden, ab denen so etwas wie "Abwärme eines Effekts" zunächst lokal berechnet wird und anschließend zu größeren Bereichen aufaddiert wird, bis hin zu globalen Werten, damit so etwas nichts bis hin ins unendliche Detail berechnet werden muss. Sowas funktioniert besonders gut bei radialen Effekten. Ähnliches würde ich z.B. auch benutzen, wenn z.B. eine Maschine/ein Zauber CO2 produziert, welches in die Atmosphäre geleitet wird. Die Materialverteilung sollte in einem kleinen Umkreis präzise, in einem größeren Umkreis weniger präziser und in einem noch größeren Umkreis als Addition zu einem globalen Wert gehandhabt werden. Diese stufenweise Trennung sollte Rechenleistung sparen, und trotzdem Gewährleisten, dass es keine Materialverluste gibt, sprich, dass das Massenerhaltungsgesetz weiterhin berücksichtigt wird. Es sollte weiterhin spezielle Prüfer geben, damit z.B. geschlossene Räume/Container nicht willkürlich Material hinzugefügt bekommen.
```
