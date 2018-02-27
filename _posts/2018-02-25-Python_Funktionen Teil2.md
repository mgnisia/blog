---
layout: single
title:  "Erweiterte Funktionen in Python"
tags:
  - Python
  - Funktion
---
Welche Möglichkeiten bestehen Funktionen zu erweitern?

Zunächst einmal gilt es zu unterscheiden, welche Parametertypen für eine Funktion grundsätzlich möglich sind. Diese kann man der folgenden Tabelle entnehmen.
### Theorie

|    Typ   |   Erläuterung          |
|:---------:|-------------|
| Pflichtparameter    | Diese Parameter müssen bei Aufruf der Funktion vorgegeben werden.  |
| Standardparameter      | Diese Parameter können bei Aufruf der Funktion vorgegeben werden. Falls dies nicht der Fall ist, wird der vordefinierte Fall des Parameters angenommen.   |
| Parameter mit unterschiedlicher Länge `(*args)`   | Von diesen Parametern (arguments) können beliebig viele an die Funktion übergeben werden.        |
| Schlüsselparameter (`**kwargs`)       | Mit diesen Parametern (keyword-arguments)  können Optionen der Funktion gesteuert werden.     |

Damit die verschiedenen Parametertypen deutlich werden, folgen nun zu jedem Typ ein Beispiel.

#### Pflichtparameter

# Änderungasdf adsasdfas

# change part2
 asdfafsdf
# change asdf asdfasdfaasdf asdf a dsf

Bereits im Post [einfache Funktion]({{ site.baseurl }}{% post_url 2018-02-25-Python_Funktionen %}) haben wir eine Funktion mit Pflichtparametern geschrieben, diese war wie folgt definiert:
``` python
def addieren(add1, add2):
	"In dieser Funktion addieren wir zwei Parameter."
	ergebnis = add1 + add2
	return ergebnis
```
Die Parameter add1 und add2 müssen auf jeden Fall beim Aufrufen der Funktion vorgeben werden.

#### Standardparameter


``` python
def addieren_pflicht(add1, add2=5):
	"In dieser Funktion addieren wir zwei Parameter."
	ergebnis = add1 + add2
	return ergebnis
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
