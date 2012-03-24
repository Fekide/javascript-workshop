# Workshop über JavaScript - The Good Parts

Dauer: 1h
Umgebung: In Google Chrome JavaScript Console

## Motivation
- Dicke der Bücher (JavaScript: The Complete Reference vs. JavaScript: The Good Parts) vergleichen
- Schaut aus wie Java und C, ist aber sehr sehr unterschiedlich davon!

## Hallo Welt (Aufgabe 0)

Erstelle ein Verzeichnis namens `javascript-workshop` und erzeuge dort ein minimales `test.html` mit folgendem Inhalt:

```html
<!doctype html>
<html>
   <head>
      <title>JavaScript Workshop</title>
   </head>
   <body>
      <p>Hallo Welt in HTML</p>
   </body>
</html>
```

Schreibe danach ein JavaScript Datei names `test.js`  mit folgendem Inhalt:

```js
document.write("Hallo Welt in JavaScript");
```

Und ändere die HTML Datei so um, dass die JavaScript Datei importiert wird. 

```html
<!doctype html>
<html>
   <head>
      <title>JavaScript Workshop</title>
      <script type="javascript" src="test.js" />
   </head>
   <body>
      <p>Hallo Welt in HTML</p>
   </body>
</html>
```

Im Weiteren werden wir nur in dieser JavaScript Datei arbeiten. 

## Vorstellung 


## Simple Sprachkonstrukte

```js
// variables
var x = 3;
var y = x + 2; // 5

// conditionals
if(y == 5) {
   console.log("y ist 5");
} else {
   console.log("y ist nicht 5");
}

// for loop
for(var i = 0; i < 10; i++){
   console.log("counter " + i);
}

// while loop
var i = 0;
while(i < 10) {
   console.log("counter " + i);
   i++;
}

// functions

function add(x,y) {
   return x + y;
}
add(2,3); // 5
oder

// anonyme Funktion die in einer Variable gespeichert wird
var add = function(x,y) {
   return x + y;
}
add(2,3); // 5

var x = add;
x(2,3); // 5
```

## Aufgabe 1

Übergabe der Zahlen 1 bis 100 an die FizzBuzz Funktion

Ausgaberegeln/Pseudocode: 

Wenn Zahl durch 5 und 3 teilbar ist, dann FizzBuzz.
Wenn Zahl teilbar durch 3, dann Fizz. 
Wenn Zahl teilbar durch 5, dann Buzz. 
Sonst Ausgabe der Zahl. 

x durch 3 teilbar => x modulo (%) 3 soll gleich 0 sein

Ausgabe auf der Konsole:

```js
console.log("Feki.de ist toll");
```

Ausgabe in aktuellem HTML Fenster:

```js
document.write("Feki.de ist toll");
document.write("<br />"); // für neue Zeile
```

## Komplexere Sprachkonstrukte

```js
// Kombination von objects und functions. Oder wie strukturiere ich meinen Code?

// arrays
var myArray = [1,2,3];
myArray = ["a", "b", "c"];
myArray = [1, "a"];
myArray = [1, [2, [3, "b"]]];
myArray[0]; // 1
myArray[1][0]; // 2

// objects
var object = {};
object = {
   "key": "value";
};
object.key; // "value"
object["key"]; // "value"
object.key = 3;
object.key; // 3

object = {
   "key1": "value1",
   "key2": function (x) { return x + 1 }
};
```

BEISPIEL: `localhost:3000/admin/order_origin/.json`

## Aufgabe 2

Organisiere dein fizzbuzz so, dass es wie folgt aufgerufen werden kann:

```js
// calling fizzbuzz
de.feki.js.fizzbuzz();
```

Hinweis: Nutze hierfür ineinander verschachtelte Objektstrukturen (Hashes) um die entsprechenden Namespaces zu erstellen. 

Zusatzaufgabe: 
Extrahiere drei weitere Methoden (teilbarDurch3, teilbarDurch5 und teilbarDurch3und5) und verwende diese geeignet. Hierzu entweder den direkten Pfad angeben, oder das Schlüsselwort this verwenden. 

## Schlechtes Erbe

### Blockless Statements

```js
if (foo)
     bar();
```

Wenn man nun eine weitere Zeile hinzufügt:

```js
if (foo)
     bar();
     solve();
```

Wann wird `solve();` ausgeführt?

### Expression and Empty Statements

```js
true;false; variablenname; ;;
```

### Floating point arithmetic

Nur double als Nummer-Datentyp. Und das mit IEEE Floating Point Standard. 

```js
0.1 + 0.2 !== 0.3;
```

## Die schlechten Seiten von JS

### Basiert auf Globalen Variablen

```js
var names = ['Simon', 'Flo', 'Andy']
// diese Variable ist nun für alle weiteren JS Anweisungen aufrufbar. 
```
...

Namenskonflikte unvermeidbar. 

```js
var $ = jquery;
var $ = mootools; // überschreiben der Variable
```

### Semi-Colon Insertion

Beispiel: 

```js
var add = function(x,y) {
    return
            x + y;
};
```

vs.

```js
var add = function(x,y) {
    return x + y;
};
```


### == und !=

Beispiel:

```js
'' == '0'             // false
0 == ''               // true
0 == '0'              // true
false == 'false'      // false
false == '0'          // true
false == undefined    // false
false == null         // false
null == undefined     // true
" \t\r\n " == 0       // true
```

Lösung: immer `===` verwenden, da es überall `false` zurückliefert. 


### typeof

```js
typeof false // "boolean"
typeof 3 // "number". Gilt auch für NaN, Infinity
typeof "name" // "string"
typeof undefined // "undefined"
typeof [1,2,3] // "object"
typeof null // "object"
typeof {'name': 'Simon'} // "object"
```

Somit wenig Hilfreich. Beispiel:

```js
typeof y; // "undefined"
y = null; 
typeof y; // "object"
```

Aber für einen Zweck notwendig:

```js
typeof var === 'undefined'
```

Da früher auch `var undefined = "not defined";` erlaubt war. Und man somit nicht `var === undefined` machen sollte. Wobei Chrome das schon nicht mehr zulässt. 

### phony arrays

```js
var myArray = [7,8,9];
// Wird intern umgewandelt in {"0": 7, "1": 8, "2": 9}
```

Deswegen geht auch:
`myArray["0"]` als Zugriff auf das erste Element. 

Arrays werden größer und kleiner, aber sind dadurch auch deutlich langsamer. 

## Aufgabe 3

Gib deinen bisher erstellten Code bei http://www.jslint.com/ ein und verbessere ihn anhand der Angaben des Tools. 


# Links und Ressourcen
 - JavaScript - The Good Parts
    - Video: http://www.youtube.com/watch?v=hQVTIJBZook
    - Buch: http://www.amazon.de/JavaScript-Parts-Working-Shallow-Grain/dp/0596517742
 - JavaScript und JQuery (gute Ergänzung nach obigem Video) http://www.youtube.com/watch?v=GKfHdOrR3lw&feature=related
 - Überblick über JQuery: http://www.youtube.com/watch?v=8mwKq7_JlS8
 - Wat Video: https://www.destroyallsoftware.com/talks/wat