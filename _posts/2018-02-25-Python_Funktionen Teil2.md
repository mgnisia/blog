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


### Pflichtparameter


Bereits im Post [einfache Funktion]({{ site.baseurl }}{% post_url 2018-02-25-Python_Funktionen %}) haben wir eine Funktion mit Pflichtparametern geschrieben, diese war wie folgt definiert:
``` python
def addieren(add1, add2):
	"In dieser Funktion addieren wir zwei Parameter."
	ergebnis = add1 + add2
	return ergebnis
```
Die Parameter add1 und add2 müssen auf jeden Fall beim Aufrufen der Funktion vorgeben werden.

### Standardparameter


``` python
def addieren_pflicht(add1, add2=5):
	"In dieser Funktion addieren wir zwei Parameter."
	ergebnis = add1 + add2
	return ergebnis
```

Werden Standardparameter wie in diesem Fall für den Parameter `add2` vorgegeben, so kann die Funktion auch nur mit einem Parameter aufgerufen werden.

``` python
addieren_pflicht(add1=2)
```

Das Ergebnis wäre in diesem Fall dann 7.


### Parameter mit unterschiedlicher Länge `*args`

Allgemein baut sich eine Funktion `*args` folgendermaßen auf:

``` python
def Funktionsname(*args) :
for i in args :
  return i
```

Eine Funktion, die beliebig viele Werte addiert, könnte mithilfe von `*args` sehr einfach gebaut werden.
