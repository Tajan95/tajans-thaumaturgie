# 17 — Information Processing Spell Components

Dieses Dokument sammelt die frühe Idee, dass bestimmte Zauberkomponenten primär Informationsverarbeitung statt physischer Transformation leisten.

**Status:** Hypothese / offene Kostenlogik

---

## Grundidee

Nicht jeder Teil eines Zaubers leistet direkte physische Arbeit.

Manche Komponenten prüfen, suchen, sortieren, erkennen, unterscheiden oder steuern.

Diese Komponenten sollten getrennt von Bewegungs-, Wärme- oder Transformationseffekten betrachtet werden.

```text
physische Arbeit ≠ Informationsverarbeitung
```

## Beispiele

| Komponente | Beschreibung |
|---|---|
| Suchen | Ziel oder Materialklasse finden. |
| Sortieren | Objekte nach Eigenschaft trennen. |
| Sammeln | passende Zielobjekte zusammenführen. |
| Trennen | Gemische nach Eigenschaft separieren. |
| Ausweichen | Kollisionen erkennen und vermeiden. |
| Anziehen | Zielklasse erkennen und Bewegung darauf ausrichten. |
| Abstoßen | Zielklasse erkennen und Bewegung davon weg ausrichten. |
| Filtern | nur passende Objekte/Materialien beeinflussen. |
| Erkennen | Eigenschaft oder Zustand bestimmen. |

## Beispiel: fliegendes Licht

Ein schwebendes Licht, das Hindernissen ausweicht, besteht aus mehreren Komponenten:

```text
Licht-/Emissionskomponente
+ Schwebekomponente
+ Wahrnehmungs-/Erkennungskomponente
+ Ausweichlogik
+ Bewegungssteuerung
```

Die Ausweichlogik ist dabei nicht dieselbe Art von Arbeit wie das physische Bewegen oder Leuchten.

## Kostenhypothese

Informationsverarbeitung sollte tendenziell weniger Mana kosten als physische Bewegung oder Transformation, weil sie nicht direkt Masse oder Energie umlagert.

Aber sie ist nicht kostenlos.

Mögliche Kostenquellen:

- Komplexität der Prüfung
- Menge der zu analysierenden Objekte/Zellen
- Präzisionsanforderung
- Geschwindigkeit der Entscheidung
- Laufzeitdauer
- Fehlertoleranz/Sicherheitslogik
- benötigte Bibliotheken/Definitionen

## Verhältnis zu kognitiver Kontrolle

Informationsverarbeitung im Zauber ist nicht dasselbe wie kognitive Kontrolle des Zauberers.

| Begriff | Bedeutung |
|---|---|
| Kognitive Kontrolle | Belastung des Zauberers beim Verstehen/Ausführen. |
| Informationskomponente | Teil des Zauberprogramms, der Daten auswertet. |

Ein Zauber kann Informationsverarbeitung automatisieren, sofern er dafür gültige Syntax, Ressourcen und Referenzen besitzt.

## Mögliche technische Analogie

```text
physische Zauberkomponente = Aktor
Informationskomponente = Sensor + Filter + Entscheidungslogik
```

## Offene Fragen

1. Werden Informationskomponenten mit Mana, Komplexitätspunkten oder Rechenkosten bepreist?
2. Können Informationskomponenten ohne Sensorik wirken?
3. Welche Weltinformationen darf ein Zauber auslesen?
4. Wie verhindert man allwissende Such- oder Analysezauber?
5. Können Informationskomponenten auf Bibliotheken und Objektdefinitionen zugreifen?
6. Wie werden Fehler in Erkennung, Klassifikation oder Zielauswahl modelliert?
7. Sind Informationskomponenten im visuellen Zauberbild erkennbar?
