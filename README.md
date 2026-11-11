# Junior Embedded Developer – Zukunftstag 2026

Willkommen zu deinem eigenen kleinen Embedded-Software-Projekt! In dieser Dokumentation lernst du, wie ein Computer mit LEDs, Tasten und Sensoren die echte Welt wahrnimmt und steuert.

Am Ende hast du:

- ein Herz auf dem BBC micro:bit programmiert,
- einzelne LEDs über Koordinaten gesteuert,
- ein Lauflicht mit und ohne Schleifen gebaut,
- die Geschwindigkeit mit Tasten verändert,
- erste Schritte mit MicroPython gemacht und
- einen Maqueen Lite V5 als fahrenden Roboter kennengelernt.

> Das druckbare Begleitheft findest du hier: [Junior Embedded Developer – Workbook](./Junior_Embedded_Developer_Workbook.pdf)

## Inhalt

1. [Was ist Embedded Software?](#1-was-ist-embedded-software)
2. [Unsere Hardware](#2-unsere-hardware)
3. [Programmieren mit MakeCode](#3-programmieren-mit-makecode)
4. [Aufgabe 1: Herz anzeigen](#4-aufgabe-1-herz-anzeigen)
5. [Aufgabe 2: Eigene Pixel](#5-aufgabe-2-eigene-pixel)
6. [Aufgabe 3: Zwei Tasten](#6-aufgabe-3-zwei-tasten)
7. [Aufgabe 4: Lauflicht ohne Schleife](#7-aufgabe-4-lauflicht-ohne-schleife)
8. [Aufgabe 5: Lauflicht mit Schleifen](#8-aufgabe-5-lauflicht-mit-schleifen)
9. [Zusatzaufgabe: Tempo per Tastendruck](#9-zusatzaufgabe-tempo-per-tastendruck)
10. [MicroPython](#10-micropython)
11. [Maqueen Lite V5](#11-maqueen-lite-v5)
12. [Fehlersuche](#12-fehlersuche)

## Vorbereitung

### Das brauchst du

- BBC micro:bit V2
- USB-Kabel
- Computer mit aktuellem Webbrowser
- optional: Batteriehalter
- optional: DFRobot Maqueen Lite V5

### Entwicklungsumgebungen

- [Microsoft MakeCode](https://makecode.microbit.org/) – Programmieren mit Blöcken
- [MicroPython-Editor](https://python.microbit.org/) – Programmieren mit Text

Für MakeCode ist keine Installation und keine Anmeldung notwendig.

## 1. Was ist Embedded Software?

**Embedded** bedeutet „eingebettet“. Ein kleiner Computer ist in ein Gerät eingebaut und übernimmt dort eine bestimmte Aufgabe.

Beispiele aus dem Alltag:

- Eine Waschmaschine misst die Temperatur und steuert den Motor.
- Ein Fahrradlicht reagiert auf einen Sensor.
- Ein Auto steuert Fensterheber, Beleuchtung und Assistenzfunktionen.

Ein Mikrocontroller liest **Eingaben**, verarbeitet sie im **Programm** und steuert **Ausgaben**:

```text
Taste oder Sensor  →  Programm  →  LED, Lautsprecher oder Motor
```

## 2. Unsere Hardware

### BBC micro:bit V2

Der micro:bit besitzt unter anderem:

- eine LED-Matrix mit 5 × 5 LEDs,
- die Tasten A und B,
- ein berührungsempfindliches Logo,
- Bewegungssensor und Kompass,
- Mikrofon und Lautsprecher,
- Funk und USB-Anschluss.

### Koordinaten der LED-Matrix

Die Position jeder LED wird mit `x` und `y` beschrieben. Beide Werte reichen von `0` bis `4`.

```text
        x →
      0 1 2 3 4
 y  0 · · · · ·
 ↓  1 · · · · ·
    2 · · ● · ·    Mitte: (2, 2)
    3 · · · · ·
    4 · · · · ·
```

## 3. Programmieren mit MakeCode

1. Öffne [makecode.microbit.org](https://makecode.microbit.org/).
2. Wähle **Neues Projekt**.
3. Gib deinem Projekt einen Namen.
4. Ziehe Blöcke aus den Kategorien in den Arbeitsbereich.
5. Teste dein Programm zuerst im Simulator.
6. Übertrage es danach auf den micro:bit.

Wichtige Kategorien:

| Kategorie | Wofür? |
|---|---|
| Grundlagen | Symbole, Text, Pausen und Bildschirm löschen |
| Eingabe | Tasten und Sensoren |
| LED | Einzelne LEDs und Helligkeit |
| Logik | Bedingungen wie „wenn … dann … sonst“ |
| Schleifen | Befehle wiederholen |
| Variablen | Werte speichern und verändern |

## 4. Aufgabe 1: Herz anzeigen

Zeige beim Start ein Herz auf der LED-Matrix.

**Benötigte Blöcke:**

```text
Grundlagen → beim Start
Grundlagen → zeige Symbol
```

- [ ] Das Herz erscheint im Simulator.
- [ ] Das Herz erscheint auf meinem micro:bit.

## 5. Aufgabe 2: Eigene Pixel

Schalte die mittlere LED bei `(2, 2)` ein. Ergänze danach weitere Punkte und zeichne ein eigenes Muster.

**Benötigter Block:**

```text
LED → zeichne Punkt bei x/y
```

- [ ] Die mittlere LED leuchtet.
- [ ] Ich habe ein eigenes Muster gezeichnet.

## 6. Aufgabe 3: Zwei Tasten

Taste A soll einen glücklichen Smiley zeigen, Taste B einen traurigen.

**Hinweis:** Verwende zwei Ereignisse aus der Kategorie **Eingabe**.

- [ ] Taste A zeigt einen glücklichen Smiley.
- [ ] Taste B zeigt einen traurigen Smiley.

## 7. Aufgabe 4: Lauflicht ohne Schleife

Lass einen einzelnen Lichtpunkt über das gesamte 5 × 5-Display wandern. Starte links oben bei `(0, 0)` und ende rechts unten bei `(4, 4)`.

Für jede Position brauchst du drei Schritte:

```text
LED         → zeichne Punkt bei x/y
Grundlagen  → pausiere (ms)
LED         → lösche Punkt bei x/y
```

### Vorgehen

1. Erstelle ein neues MakeCode-Projekt.
2. Programmiere zuerst drei Positionen.
3. Ergänze danach die übrigen LEDs.
4. Prüfe, ob immer nur eine LED gleichzeitig leuchtet.

### Denk nach

- Welche Koordinate kommt nach `(4, 0)`?
- Wie viele einzelne Positionen musst du programmieren?
- Was passiert, wenn du das Löschen einer LED vergisst?

- [ ] Mein Lauflicht besucht alle 25 LEDs.

## 8. Aufgabe 5: Lauflicht mit Schleifen

Erzeuge dasselbe Lauflicht jetzt mit zwei verschachtelten Schleifen:

- Die äußere Schleife wählt die Zeile `y`.
- Die innere Schleife läuft durch die Spalten `x`.
- Beide Schleifen zählen von `0` bis `4`.

### Denk nach

- Warum ergeben zwei Schleifen genau 25 Positionen?
- Welche Schleife muss innen stehen, damit das Licht zeilenweise läuft?

### Freiwillige Herausforderung: Schlangenlauflicht

Lass das Licht in jeder zweiten Zeile in die entgegengesetzte Richtung laufen.

Tipp: Unter **Mathematik** findest du den Block **Rest von …**. Der Rest verrät dir, ob eine Zahl gerade oder ungerade ist.

- [ ] Das Lauflicht verwendet zwei Schleifen.
- [ ] Bonus: Das Licht läuft schlangenförmig.

## 9. Zusatzaufgabe: Tempo per Tastendruck

Steuere die Geschwindigkeit des Lauflichts:

- Taste A: schneller
- Taste B: langsamer
- A+B: Tempo auf `100 ms` zurücksetzen

Verwende eine Variable für die Wartezeit und verändere sie bei jedem Tastendruck um `10 ms`.

### Wichtig

Begrenze die Wartezeit, damit sie nicht kleiner als `10 ms` und nicht größer als `2000 ms` wird.

- [ ] Taste A macht das Lauflicht schneller.
- [ ] Taste B macht das Lauflicht langsamer.
- [ ] Die Wartezeit bleibt im erlaubten Bereich.

## 10. MicroPython

Öffne [python.microbit.org](https://python.microbit.org/) und teste dieses Programm:

```python
from microbit import *

while True:
    if button_a.is_pressed():
        display.show(Image.HAPPY)
    else:
        display.show(Image.SAD)
    sleep(100)
```

### Was passiert im Code?

| Code | Bedeutung |
|---|---|
| `from microbit import *` | Stellt die micro:bit-Funktionen bereit |
| `while True:` | Wiederholt den eingerückten Programmteil |
| `if / else` | Entscheidet zwischen zwei Möglichkeiten |
| `sleep(100)` | Wartet 100 Millisekunden |

> In Python sind Einrückungen wichtig. Sie zeigen, welche Befehle zusammengehören.

## 11. Maqueen Lite V5

Der Maqueen wird durch den micro:bit zu einem fahrenden Roboter. Er besitzt unter anderem:

- zwei Motoren,
- Liniensensoren,
- einen Ultraschallsensor,
- RGB-LEDs.

### Idee eines Linienfolgers

1. Fährt der Roboter über der Linie, fährt er geradeaus.
2. Erkennt der linke Sensor die Linie, korrigiert der Roboter nach links.
3. Erkennt der rechte Sensor die Linie, korrigiert er nach rechts.

Arbeite schrittweise: zuerst Motoren testen, dann Sensorwerte beobachten und erst danach die Lenkregeln ergänzen.

Offizielle Anleitung: [DFRobot Maqueen Lite V5](https://wiki.dfrobot.com/mbt0046/docs/21343)

## 12. Fehlersuche

Wenn etwas nicht funktioniert, prüfe der Reihe nach:

- [ ] Ist der micro:bit mit Strom versorgt?
- [ ] Wurde das richtige Programm übertragen?
- [ ] Sind alle Blöcke korrekt verbunden?
- [ ] Stimmen die Koordinaten?
- [ ] Liegen Sensorwerte im erwarteten Bereich?
- [ ] Sind Bedingungen und Schleifen richtig aufgebaut?

## Mein Entwickler-Tagebuch

### Das hat heute gut funktioniert

_Notiere hier deine Beobachtungen._

### Diesen Fehler habe ich gefunden

_Was war die Ursache? Wie hast du den Fehler behoben?_

### Das möchte ich als Nächstes ausprobieren

_Welche eigene Idee möchtest du programmieren?_

---

Viel Spaß beim Programmieren, Experimentieren und Fehlerfinden! 🚀
