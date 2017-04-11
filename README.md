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
# Objekte
... Jetzt wird es spanned, kommt noch
