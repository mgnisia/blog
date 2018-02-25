---
title:  "Einfache Funktionen in Python"
tags:
  - Python
---
### Theorie

Grundsätzlich baut sich eine Funktion in Python wie folgt auf:

``` python
def Funktionsname(Parameter1):
	"Beschreibung der Funktion"
	variable1 = Parameter1
	variable2 = Parameter1 + 10
	return variable1, variable2
```
Wesentlichen Eigenschaften sind:

* Eine Funktion beginnt immer mit dem Keyword `def`
* Sie muss einen Funktionsnamen besitzen
* Sie sollten einen Rückgabewert besitzen, dieser wird durch `return` zurückgegeben

### Beispiel

Eine Funktion zum Addieren von zwei Zahlen kann daher wie folgt definiert werden:

``` python
def addieren(add1, add2):
	"In dieser Funktion addieren wir zwei Parameter."
	ergebnis = add1 + add2
	return ergebnis
```

### Aufrufen von Funktionen

In Python kann man die Funktion auf zwei Arten aufrufen:
``` python
# 1. Möglichkeit:
addieren(1, 2)
# 2. Möglichkeit;
addieren(add1=1, add2=2)
```
Die Unterschiede zwischen beiden Möglichkeiten bestehen darin, dass im ersten Fall im Gegensatz zum zweiten Fall, die Parameter `add1` und `add2` nicht vorgegeben werden. Bei Funktionen mit vielen Parametern bietet es sich an die zweite Möglichkeit zu verwenden.
