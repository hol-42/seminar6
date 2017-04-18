# Seminar 6

Es gibt einige Dinge über Javascript, die man wissen sollte, sonst frägt man
sich immer wieder was da gemacht wird. Ausserdem ist es von Vorteil ein 
bisschen den Unterschied zwischen dem neuen und der alten Javascript Syntax
zu verstehen. Es beherrschen heute aber alle Browser den neuen Syntax, daher
ist es nur dann notwendig den alten Syntax zu verstehen, wenn man Codebeispiele
anschaut.

## Javascript Versionen

Javascript ist eigentlich ECMAScript vom offiziellen Normungsgremium

- "Alte Version": ES5
- Seit Juni 2015 gibt es ES2015 die anfänglich ES6 hiess. Grosse Veränderungen.
- Die ES2016 Version ist ES7 hat aber nicht mehr so grosse Veränderungen.
- ES8 gibt es noch nicht

## Resourcen im Internet

Mozilla sind diejenigen die wirklich sehr viel Arbeit bezüglich Javascript
aufbringen und ihre Artikel sind gut und oft übersetzt. Speziell diese Seite:

https://developer.mozilla.org/de/docs/Web/JavaScript/Eine_Wiedereinfuehrung_in_JavaScript

Das MDN (Mozilla Developer Network) ist also sehr empfehlenswert.

## Datentypen

Natürlich gibt es Numbers, Strings, Booleans. Aber auch Functions und 
Objects sind Datentypen und `undefined` und `null` werden auch als
Datentypen angesehen. Eigentlich sind Functions auch Objects. Die
korrekte Aufzählung laut MDN:

- Numbers (numerische Werte)
- Strings (Zeichenketten)
- Booleans (boolesche Werte)
- Symbol (neu in ES 6)
- Objects (Objekte)
    - Functions (Funktionen)
    - Arrays
    - Date (Datums und Zeitobjekt)
    - RegExp (Reguläre Ausdrücke)
- null
- undefined

# Praktisches zu Nummern

Im Terminal eingeben:

```bash
$ node
```

Dann im in der node shell eingeben:
```js
0.1+0.2
```
erstaunliches Ergebnis, richtig?  

Dann sollte man über Konvertierungen bescheid wissen. 
```js
> "5"+6
'56'
```
Wenn etwas keine Nummer ist ist es Not A Number (NaN)
```
> parseInt("quatsch")
NaN
```
Und beim Teilen durch Null gibt es wenigstens bei dieser Sprache das richtige
Ergebnis:
```js
> 1 / 0
Infinity
```
Entsprechend kann man Abfragen:
```js
> isFinite(1/0)
false
> isNaN("quatsch")
true
```
# Praktisches zu Strings
Einfach mal ausprobieren.
```js
> "Hallo".length
5
> var meinString="Jürgen Hollfelder"
undefined
> meinString
'Jürgen Hollfelder'
> meinString.length
17
> meinString.charAt(0)
'J'
> meinString.charAt(meinString.length-1)
'r'
> meinString.replace("Hollfelder", "Hollenfelder")
'Jürgen Hollenfelder'
> meinString.toUpperCase()
'JÜRGEN HOLLFELDER'
> meinString
'Jürgen Hollfelder'
```
# null und undefined
Es gibt ein Unterschied zwischen `null` und `undefined`. Um das genau
zu verstehen muss man verstehen muss man kurz sich vergegenwärtigen, dass
Javascript nicht erwartet, dass man eine Variable definiert und wenn
man sie definiert, dass man dann den Typ angibt. Der Grund weshalb TypeScript
recht populär ist. Beispiel (`var` definiert global, `let` seit ES2015 
definiert nur im Scope z.B. innerhalb geschweifert Klammern):
```js
> let varA
undefined
> varA
undefined
> varA == undefined
true
> let varB = "wird zum String"
undefined
> varB
'wird zum String'
> varB == undefined
false
> typeof varB
'string'
> typeof varA
'undefined'
> varB = ''
''
> typeof varB
'string'
> varB == null
false
> varB
''
> varB = null
null
> varB
null
> varB == null
true
```
# Booleans

Boolsche Operatoren: 

- `&&` ist `AND`
- `||` ist `OR`
- `!` ist `NOT`

Es kann jeder Wert zu einem Boolschen Wert konvertiert werden, dabei gilt:

- false , 0, leere Strings (""), NaN , null , und undefined werden zu false
- Alle anderen Werte werden true

Beispiel:
```js
> const varC
undefined
> let varD = Boolean(varC)
undefined
> varD
false
> varD = !varC
true
```
Vergleiche erfolgen mit `==` bzw. `===`. Letzteres ist präzisser, weil es 
auch den Datentypen in den Verleich mit einschliesst.
```js
> varX = "1"
'1'
> varY = 1
1
> varX == varY
true
> varX === varY
false
```
# Kontrollstrukturen
Vom Syntax her ähnlich wie andere C ähnliche Sprachen:
```js
if (a=b) {
    console.log('a ist gleich b')
}
else if (a=c) {
    console.log('a ist gleich c')
}
else {
    console.log('a ist weder gleich b noch gleich c')
}
Übrigens: Die Semicolons werden nicht wirklich benötigt, wenn 
der nächste Befehl auf der nächsten Zeile beginnt.
https://www.codecademy.com/blog/78-your-guide-to-semicolons-in-javascript

Schleifen mit `for` und `while` sind ähnlich einfach und spar ich mir
für den Moment mal. 

Aber es gibt einen `iff` und der ist oft sehr praktisch:
```js
> (varX == varY) ? "gleich" : "ne doch nicht gleich"
'gleich'
```

Auch ein NVL kann man machen indem man ausnutzt, dass aufgehöt wird
wenn ein Wert `true` ist.
```js
> let varUndefined
undefined
> let varDefined = 4711
undefined
> varUndefined
undefined
> varDefined
4711
> var varTest = varUndefined || varDefined
undefined
> varTest
4711
```
# Funktionen

Einfache Funktionen sind schnell begriffen, aber einfach um es kurz vorzustellen.
Es gibt aber keine Unterscheidung zwischen Prozeduren und Funktionen. Eigentlich
sind alles Funktionen können aber auch rein Prozeduren sein.
```js
> function machwas() {
... console.log('Hallo')
... }
undefined
> machwas
[Function: machwas]
> machwas()
Hallo
undefined
> function gibwas(n) {
... return n*2
... }
undefined
> gibwas
[Function: gibwas]
> gibwas(2)
4
> gibwas()
NaN
```

Da Funktionen aber auch Variablen sind können Funktionen auch anderen Variablen
zugewiesen werden.

```
> x = gibwas
[Function: gibwas]
> x()
NaN
> x(3)
6
> 
```

# Objekte
Ein Objekt ist einfach eine kommagetrennte Auflistung von Key / Value Paaren.

Beispiel

```js
let meinObjekt = {
    Nachname: 'Müller',
    Vorname: 'Thomas',
    Beruf: 'Fussballer'
}
```

Geschachtelte Objekte gehen auch:


```js
let meinObjekt = {
    Nachname: 'Hollfelder',
    Vorname: 'Jürgen',
    Adresse: {
        Strasse: 'Löwenstr. 29',
        PLZ: '70597',
        Ort: 'Stuttgart',
        Land: 'Deutschland'
    }
}
```

Zugriff mit Punktnotation oder per Index

```js
> meinObjekt.Adresse.Strasse
'Löwenstr. 29'
> meinObjekt['Adresse']['Ort']
'Stuttgart'
> 
```
Möglich ist es aber auch eine "Klasse" zu erstellen. Allerdings heisst das
Prototyp in der Javascript Welt und ist tatsächlich auch ein klein wenig etwas
anderes:

```js
> function Person(name, beruf) {
...     this.name = name
...     this.beruf = beruf
... }
undefined
> let jemand = new Person('Dirk Nowitzki', 'Basketballer')
undefined
> jemand.name
'Dirk Nowitzki'
> jemand
Person { name: 'Dirk Nowitzki', beruf: 'Basketballer' }
```

# Array

Mit Objekten kann man zwar noch weit mehr anfangenk, dazu aber noch später mehr.
Jetzt erst einmal ein Ausflug zu Array
```js
> let meinArray = ['Hund', 'Katze', 'Maus']
undefined
> meinArray
[ 'Hund', 'Katze', 'Maus' ]
> meinArray[0]
'Hund'
> meinArray[-1]
undefined
> meinArray[100]
undefined
> meinArray[2]
'Maus'
```

Total logisch. Aber zählen fängt bei 0 an.

Zufügen geht mit `push`, zählen mit `length` und es gibt noch eine Menge 
weiterer, die man unter 
https://developer.mozilla.org/de/docs/Web/JavaScript/Eine_Wiedereinfuehrung_in_JavaScript#Arrays 
gut nachlesen kann.

Erwähnenswert ist noch `forEach`:

```js
> meinArray.forEach( function (meinElement) { console.log(meinElement) })
Hund
Katze
Maus
undefined
```

Es wird als Parameter eine Funktion übergeben. Funktionen werden ja wie Variablen
behandelt. Daher funktioniert das.

Im ES6 gibt es dann noch die arrow Notation. Ist kürzer hat in Spezialfällen 
auch ein paar andere Vorteile:

```js
> meinArray.forEach( (meinElement) => { console.log(meinElement) })
Hund
Katze
Maus
undefined
> 
```

# Funktionen in Objekten

```js
meinObjekt = {
    vorname: 'Donald',
    nachname: 'Duck',
    name: function() {
        return this.vorname + ' ' + this.nachname
    }
}

> meinObjekt
{ vorname: 'Donald', nachname: 'Duck', name: [Function] }
> meinObjekt.name
[Function]
> meinObjekt.name()
'Donald Duck'
```
Wenn aber Funktionen in Objekte grösser werden, will man ja nicht jedesmal
die ganze Funktion da drin haben usw.

Da geht man dann wie folgt vor. Zuerst wird mal eine Funktion erstellt, mit 
der man ein Objekt erstellen kann:

```js
function Person(first, last) {
  this.first = first;
  this.last = last;
}

> p = new Person('Mickey', 'Maus')
Person { first: 'Mickey', last: 'Maus' }
> p
Person { first: 'Mickey', last: 'Maus' }
> p.first
'Mickey'
```

Dann kann eine Prototyp Funktion erstellt werden. Z.B. 

```js
Person.prototype.fullName = function() {
  return this.first + ' ' + this.last; 
}

> p.fullName()
'Mickey Maus'
```

So kann man eben doch in gewisser weise Klassen definieren. Mit ES6 wurde der 
Syntax erweitert. D.h. man kann es auch so machen:

```js
class PersonenKlasse {
    constructor(vorname, nachname) {
        this.vorname = vorname
        this.nachname = nachname
    }
    fullName() {
        return this.vorname + ' ' + this.nachname
    }
}
> let meinePerson = new PersonenKlasse('Max', 'Mustermann')
undefined
> meinePerson
PersonenKlasse { vorname: 'Max', nachname: 'Mustermann' }
> meinePerson.fullName()
'Max Mustermann'
> 
```

Mehr dazu hier: https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Klassen

# Closures

Das ist etwas das man häufiger antrifft und oft auch erst einmal missverstanden wird.
Aber es geht zunächst einmal um nichts anders als dass ein Closure eine Funktion 
ist, die in der Funktion eine Variable benutzt, die sie aus dem Kontext kennt.
Javascript speichert also den ganzen Kontext mit.

Beispiel:

```js
> function aussen(aussenWert) {
... const pi = 3.14
... return function innen(innenWert) {
..... console.log('ich kenne pi',pi, 'und aussenWert', aussenWert, 'und innenWert', innenWert)
..... }
... }
undefined
> x=aussen(5)
[Function: innen]
> x(1234)
ich kenne pi 3.14 und aussenWert 5 und innenWert 1234
undefined
> y=aussen(9999)
[Function: innen]
> y(8888)
ich kenne pi 3.14 und aussenWert 9999 und innenWert 8888
undefined
> 
```
