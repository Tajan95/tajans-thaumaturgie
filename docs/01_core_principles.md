# 01 — Core Principles

## Zweck

Dieses Dokument sammelt die grundlegenden Prinzipien, an denen jede spätere Regel, jedes Zeichen und jeder Zauber geprüft wird.

## Prinzipien

### 1. Ableitbarkeit

Jeder Zauber muss aus kleineren Komponenten ableitbar sein.

Ein Effekt wie „Feuerball“ darf also nicht als atomarer Zauber behandelt werden, sondern muss aus Grundbegriffen wie Energie, Hitze, Richtung, Form, Bewegung, Ziel und Begrenzung entstehen.

### 2. Kausalität

Ein Zauber verändert einen Zustand nicht willkürlich. Er muss eine kausale Transformationsregel besitzen:

```text
Ausgangszustand + magische Operation → Folgezustand
```

### 3. Modularität

Komponenten sollen kombinierbar sein. Ein Modifier wie `Verstärkung`, `Umkehrung` oder `Bindung` soll nicht nur für einen Zauber gelten, sondern systemweit definierbar sein.

### 4. Begrenzung

Magie braucht Grenzen. Mögliche Begrenzungen sind:

- Energieaufwand
- Komplexität
- Präzision
- Reichweite
- Dauer
- Materialwiderstand
- Informationsmangel
- Risiko von Fehlinterpretationen

### 5. Simulierbarkeit

Jede Regel sollte langfristig technisch abbildbar sein. Regeln dürfen abstrakt beginnen, müssen aber später in Datenstrukturen, Zustandsänderungen oder Algorithmen übersetzbar sein.

### 6. Trennung der Ebenen

Lore, Regelmechanik, Simulation und Gameplay dürfen sich gegenseitig inspirieren, sollen aber nicht verwechselt werden.

## Prüfmatrix für neue Ideen

| Frage | Zweck |
|---|---|
| Ist die Idee ableitbar? | Verhindert hardcodierte Zauber. |
| Ist sie konsistent? | Verhindert Widersprüche. |
| Ist sie begrenzt? | Verhindert Beliebigkeit und Allmacht. |
| Ist sie simulierbar? | Sichert spätere technische Umsetzung. |
| Erzeugt sie interessante Kosten? | Macht das System spielbar und strategisch. |
| Gehört sie zu Theorie, Simulation, Gameplay oder Lore? | Hält die Dokumentation sauber. |
