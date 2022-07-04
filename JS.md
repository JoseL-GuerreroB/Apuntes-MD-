# JavaScript

---

## Variables

### Estructura de variable

- Tipo de variable
- Nombre
- Dato

```js
var variable = 12;
//tipVar nomVar = Dato;
```

### Tipo de variable

- **Var:** Variable estandar, variable global
- **Let:** Variable local, respeta parametros y utiliza los valores dependiendo si se encuentra dentro de una condicional o fuera
- **Const:** Variable con valor permanente

```js
var variable = 12;
let variable = 12;
const variable = 12;
//scope=limitante campo local, hoisting= campo global
```

### Tipos de datos (**int, float, boleano, string**).

```js
var int = 12;
var string = "Juan";
var boleano = true; // o false
var float = 15.75;
var define; //no definida
// Los tipos de datos solo se muestran en el valor de las variables
```

### Otros resultados de variables;

- **undefined:** No definida
- **null:** Campo vacio
- **nan:** No es un valor calculable

### Operadores aritmeticos

- num **+** num --> Suma
- num **-** num --> Resta
- num \* num --> Multiplicacion
- num **/** num --> Divicion
- num **%** num --> Residuo de divicion

### Operadores de condicion

- **=** --> asignacion
- **==** --> igualacion
- **===** --> igualacion mas precisa, incluyendo tipo de dato
- **< , >** --> menor que, mayor que
- **<= , >=** --> menor o igual a, mayor o igual a
- **!=** --> no es igual
- **!==** --> No es igual, conciderando tipo de dato

### Operadores logicos

- **&&** --> y () y ()
- **||** --> o () o ()\*\*
- **!** --> no !()

---

## Alerta emergente

**alert( );** Aparece un recuadro con un mensaje.

**confirm( );** Aparece un mensaje de confirmacion y te da a elegir 2 valores. True para aceptar y false para cancelar.

**promp( );** Aparece un mensaje con una cuestion para que el usuario pueda dar una respuesta, tambien puede darsele un valor predeterminado.

```js
alert("Bienvenido a mi web");
var confirmacion = confirm("¿Estas seguro?");
var respuesta = prompt("¿Cuantos años tienes", "18");
```

---

## Condicionales y Bucles

### IF

Si la condicion es verdadera, se ejecutara su codigo correspondiente.

```js
var num1 = 10,
  num2 = 20;

if (num1 < num2) {
  //Se ejecuta la istruccion
}
```

### ELSE

Se usa cuando tienes alguna instruccion en caso de que no sea verdadera.

```js
var num1 = 10,
  num2 = 20;

if (num1 > num2) {
  //No se ejecuta la istruccion
} else {
  //Se ejecuta la instruccion
}
```

### Operador ternario: Una alternativa al if else.

```js
var num1 = 10,
  num2 = 20;

num1 < num2
  ? console.log("Ejecuta este si es verdadero")
  : console.log("Ejecuta este si es falso");

num1 < num2
  ? console.log("opcion1")
  : num1 == num2
  ? console.log("opcion2")
  : console.log("opcion3");
```

### IF anidados

```js
var num1 = 10,
  num2 = 20,
  num3 = 40,
  num4 = 5;

if (num1 < num2) {
  //Instrucciones
  if (num1 < num4) {
    //Instrucciones
  } else if (num1 > num3) {
    //Instrucciones
  } else {
    //instrucciones
  }
}
```

### SWITCH

Es un selector capas de crear instrucciones para diversos resultados especificos.

```js
var seleccion = 2;

switch (seleccion) {
  case 1:
    //instrucciones
    break;
  case 2:
    //instrucciones
    break;
  default:
    //Si el valor no coincide con uno de los casos
    //se ejecutan estas instrucciones
    break;
}
```

### SWITCH anidado

var seleccion = 2;

```js
var seleccion = 2,
  seleccion2 = "b";

switch (seleccion) {
  case 1:
    //instrucciones
    switch (seleccion2) {
      case "a":
        //instrucciones
        break;
      case "b":
        //instrucciones
        break;
      default:
        //Si el valor no coincide con uno de los casos
        //se ejecutan estas instrucciones
        break;
    }
    break;
  case 2:
    //instrucciones
    switch (seleccion2) {
      case "a":
        //instrucciones
        break;
      case "b":
        //instrucciones
        break;
      default:
        //Si el valor no coincide con uno de los casos
        //se ejecutan estas instrucciones
        break;
    }
    break;
  default:
    //Si el valor no coincide con uno de los casos
    //se ejecutan estas instrucciones
    break;
}
```

### WHILE

Un bucle que se repetira hasta que la condicion inicial ya no sea verdadera. Si la condicion no es verdadera desde el principio no se ejecutara.

```js
var num1 = 1,
  num2 = 4;

while (num1 < num2) {
  num1++; // El valor de num1 crece hasta que ya no cumpla la condicion
  //da 3 iteraciones
}
```

### DO WHILE

Un bucle que se repetira hasta que la condicion inicial ya no sea verdadera. Si la condicion no es verdadera desde el principio se ejecutara solo una vez ejecutara.

```js
var num1 = 0,
  num2 = 4;

do {
  num1++; //da 3 iteraciones ya que num1 aumenta su valor antes de evaluarse en el while.
} while (num1 < num4);
```

### FOR

Bucle con 3 parametros incluidos. asignacion, evaluacion, incremento.

```js
let str = [];

for (let i = 1; i <= 10; i++) {
  str[i] = i * 2;
}
console.log(str);
// str= [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

---

## Funciones

### Funcion normal

```js
// Sin parametros
function ejecutar() {
  // Indicaciones
}
ejecutar(); //ejecutar

// Con parametros
function ejecutar(param1, param2) {
  let saludo = param1 + param2;
  return saludo;
}
ejecutar("Hola ", "Mundo"); //Ejecuta

//Convertir la variable en la funcion
var funcion = function (param1, param2) {
  let saludo = param1 + param2;
  return saludo;
};
funcion("Hola ", "Mundo");
```

### Flecha

```js
// Funcion sin parametros
var flecha = () => {
  //Instrucciones
};
flecha(); //Ejecucion

// Funcion con un parametro
var flecha1 = (parametro) => {
  //Instrucciones
};
flecha1("Hola man"); //Ejecucion

// Funcion con una sola instruccion
var flecha2 = (parametro) => console.log(parametro);
flecha2("Hola man");

//Funcion con varios parametros
var flecha3 = (num1, num2, num3) => {
  let suma = num1 + num2 + num3;
  return suma;
};
flecha3(5, 4, 3); //Ejecucion
```

---

## Metodos de string

**concat( );** Junta dos o mas cadenas y retorna una total.

```js
const str1 = "Hola",
  str2 = " Mundo";
var str3, str4;

str3 = str1.concat(str2); //Hola Mundo
str4 = str1.concat(str2, " y a todos quienes lo habitan"); //Hola Mundo y a todos quienes lo habitan
```

**startWith( );** Si una cadena comienza con los caracteres sucesivos que se le dan devuelve true, si no false. Tambien puedes controlar desde que pocicion se ejecutara.

```js
const str1 = "Saturno es muy grande";
var str2, str3, str4;

str2 = str1.startsWith("Sat");
//Devuelve true
str3 = str1.startsWith("Sat", 3); //Devuelve false
str4 = str1.startsWith("urno", 3); //Devuelve true
```

**endsWith( );** Si una cadena termina con los caracteres sucesivos que se le dan devuelve true, si no false. Tambien puedes controlar desde que pocicion se ejecutara solo que esta vez no se consideraran los que siguen de la pocicion, si no los anteriores a la pocicion.

```js
const str1 = "Mercurio no es tan grande";
var str2, str3, str4;

str2 = str1.endsWith("nde");
//Devuelve true
str3 = str1.endsWith("rio", 8); //Devuelve true
str4 = str1.endsWith(" no", 8); //Devuelve false
```

**includes( );** Si en la cadena contiene los caracteres sucesivos que le dimos devuelve true, si no devuelve false.

```js
const cadenaDeTexto = "Mi perro es amigable con todos",
  palabra1 = "agrecivo",
  palabra2 = "perro";
var evaluador1, evaluador2;

evaluador1 = `La palabra "${palabra1}" ${
  cadenaDeTexto.includes(palabra1) ? "esta" : "no esta"
} en la cadena de texto`;
// Devuelve false
evaluador2 = `La palabra "${palabra2}" ${
  cadenaDeTexto.includes(palabra2) ? "esta" : "no esta"
} en la cadena de texto`;
// devuelve true
```

**indexOf( );** Devuelve el primer indice en donde se encuetran los caracteres sucesivos dentro de la cadena en donde se busca. Si no lo encuentra da -1. Tambien puedes definir la posicion desde donde se buscara.

```js
const str1 = "Mi gato, mi perro, mi pez y mi canario";
var str2, str3, str4;

str2 = str1.indexOf("mi");
//Devuelve 9
str3 = str1.indexOf("mi", str2 + 1); //Devuelve 19
str4 = str1.indexOf("mi", str3 + 1); //Devuelve 28
```

**lastIndexOf( );** Es como el "indexOf" pero esta vez conciderara la coincidencia mas lejana al punto de partida.

```js
const str1 = "Mi gato, mi perro, mi pez y mi canario";
var str2, str3, str4;

str2 = str1.lastIndexOf("mi");
//Devuelve 28
str3 = str1.lastIndexOf("mi", str2 - 1); //Devuelve 19
str4 = str1.lastIndexOf("mi", str3 - 1); //Devuelve 9
```

**padStart( );** Complementa un string dandole un numero determinado de espacios para que la suma de cada caracter de igual al numero que se le asigna. El segundo valor determina con que caracteres se rellenan los huecos.

```js
const str1 = "5";
var str2, str3, str4;

str2 = str1.padStart(8);
//Devuelve "       5" string de 8 espacios
str3 = str1.padStart(8, "f");
//Devuelve "fffffff5"
str4 = str1.padStart(8, "foca");
//Devuelve "focafoc5"
```

**padEnd( );** Hace casi lo mismo que "padStart", solo que esta vez muestra la cadena despues del valor predeterminado.

```js
const str1 = "5";
var str2, str3, str4;

str2 = str1.padEnd(8);
//Devuelve "5       " string de 8 espacios
str3 = str1.padEnd(8, "f");
//Devuelve "5fffffff"
str4 = str1.padEnd(8, "foca");
//Devuelve "5focafoc"
```

**repeat( );** Devuelve la misma cadena pero repetida las veces indicadas.

```js
const str1 = "Repito ";
var str2, str3, str4;

str2 = str1.repeat(3);
//Devuelve "Repito Repito Repito "
str3 = str1.repeat(0);
//Devuelve " "
str4 = str1.repeat(-1);
// Valor invalido
```

**split( );** divide la cadena como le pidamos utilizando un caracter en especifico, despues cumbierte la cadena en un Array.

```js
const str1 = "los metodos de separacion pueden ser cualquier cosa";
var str2, str3, str4;

str2 = str1.split("");
//Devuelve Array=[ "l","o","s"," ","m","e","t",... ];
str3 = str1.split(" ");
//Devuelve Array=[ "los","metodos","de",... ];
str4 = str1.split("s");
//Devuelve Array=[ "lo"," metodo"," de ","eparacion pueden ","er cualquier co","a"... ];
```

**substring( );** nos retorna un pedazo de la cadena que seleccionamos, apartir de un numero de inicio y uno final si lo requerimos.

```js
const str1 = "Madrugada";
var str2, str3, str4;

str2 = str1.substring(4);
//Devuelve "ugada"
str3 = str1.substring(1, 3);
//Devuelve "ad"
str4 = str1.substring(2, 6);
//Devuelve "drug"
```

**toLowerCase( );** Convierte una cadena a minusculas

```js
const str1 = "MAYONESA";
var strMin;

strMin = str1.toLowerCase(); //Devuelve "mayonesa"
```

**toUpperCase( );** Convierte una cadena a mayusculas

```js
const str1 = "mayonesa";
var strMay;

strMay = str1.toUpperCase(); //Devuelve "MAYONESA"
```

**toString( );** Metodo que devuelve una cadena, apesar de que su valor primitivo tenga otro tipo de dato.

```js
const int = 5,
  float = 10.25,
  boll = false;
var str;

str = int.toString(); //Devuelve "5"
str = float.toString(); //Devuelve "10.25"
str = boll.toString(); //Devuelve "false"
```

**trim( );** Elimina los espacios al principio y al final de una cadena.

```js
const str1 = "   Mazorcañon  ";
var str_Sin_;

str_Sin_ = str1.trim(); //Devuelve "Mazorcañon"
```

**trimEnd( );** Solo elimina los espacios al final.

```js
const str1 = "   Mazorcañon  ";
var str_Sin_;

str_Sin_ = str1.trimEnd(); //Devuelve "  Mazorcañon"
```

**trimStart( );** Solo elimina los espacios del principio.

```js
const str1 = "   Mazorcañon  ";
var str_Sin_;

str_Sin_ = str1.trimStart(); //Devuelve "Mazorcañon  "
```

**valueOf( );** Retorna el valor primitivo de un objeto string.

```js
cadena = new String("Objeto String");
alert(cadena.valueOf()); // Devuelve "Objeto String"
```

---

## Metodo de Arrays

Algunos metodos string funcionan con Arrays como:

- **contact( );** Une dos o más Arrays como uno solo
- **includes( );** Si el valor se encuentra en el Array devuelve true, si no devuelve false
- **indexOf( );** Localiza el valor en el Array y devuelve su pocicion, si no existe devuelve -1. tambien puedes establecer un valor de inicio.
- **lastIndexOf( );** Casi lo mismo que el anterior, solo que este recorre el Array en sentido contrario.
- **toString( );** Concatena el valor del Array completo

**pop( );** Elimina el ultimo elemento del array y lo devuelve como valor.

```js
var vegetales = ["tomate", "brocoli", "cebolla", "col", "sanahoria"],
  vegePop;

vegePop = vegetales.pop(); //Devuelve "sanahoria"
//vegetales = ['tomate','brocoli','cebolla','col'];
```

**shift( );** Elimina el primer elemento del array y lo devuelve como valor.

```js
var vegetales = ["tomate", "brocoli", "cebolla", "col", "sanahoria"],
  vegeShift;

vegeShift = vegetales.shift(); //Devuelve "tomate"
//vegetales = ['brocoli','cebolla','col','sanahoria'];
```

**unshift( );** El método añade uno o más elementos al inicio de un array y devuelve la nueva longitud del array.

```js
var vegetales = ["tomate", "jitomate"],
  vegeUnshift;

vegeUnshift = vegetales.unshift("brocoli", "col");
//Devuelve 4 -- nueva longitud
//vegetales = ['brocoli','col','tomate', 'jitomate'];
```

**push( );** El método añade uno o más elementos al final de un array y devuelve la nueva longitud del array.

```js
var vegetales = ["tomate", "jitomate"],
  vegePush;

vegePush = vegetales.push("brocoli", "col");
//Devuelve 4 -- nueva longitud
//vegetales = ['tomate', 'jitomate','brocoli','col'];
```

**reverce( );** El metodo invierte el orden de los elementos del array.

```js
var vegetales = ["tomate", "jitomate", "brocoli", "col"],
  vegeReverse;

vegeReverse = vegetales.reverse();
//Devuelve El array al revez
//vegetales = ['col','brocoli', 'jitomate', 'tomate'];
```

**sort( );** Devuelve los elementos de un arreglo localmente y lo devuelve ordenados alfabeticamente.

```js
var valores = ["atun", "globo", 1, 9, 40, 104, "burro", "alacran"],
  valOrder;

valOrder = valores.sort();
//Devuelve El array ordenado
//valores = [1, 104, 40, 9, "alacran", "atun", "burro", "globo"];
```

**splice( );** Cambia el contenido del array eliminando elementos existentes y/o agregando nuevos.

```js
const mes = ["Jan", "March", "April", "June"];

mes.splice(1, 0, "Feb");
//En la pocicion 1 añade "Feb"
mes.splice(3, 1, "May");
//En la pocicion 3 elimina "june" y lo remplaza por "May"

//mes = ['Jan','Feb','March','April','May'];
mes.splice(1, 3);
//Elimina el valor de la pocicion 1 hasta el valor de la pocicion 3
//mes = ['Jan','May'];
```

**join( );** Une todos los elementos de una matriz en una cadena y la devuelve.

```js
const array = ["donas", "con", "fresa", "y", "chispas"];
var str1, str2, str3, str4;

str1 = array.join(); //Devuelve "donas,con,fresa,y,chispas"
str2 = array.join(""); //Devuelve "donasconfresaychispas"
str3 = array.join(" "); //Devuelve "donas con fresa y chispas"
str4 = array.join("-"); //Devuelve "donas-con-fresa-y-chispas"
```

**slice( );** Devuelve una parte del array dentro de un nuevo array empezando por inicio hasta el fin.

```js
const animals = ["ant", "bison", "camel", "duck", "elephant"];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]

console.log(animals.slice());
// expected output: Array ["ant", "bison", "camel", "duck", "elephant"]
```

**filter( );** Crea un nuevo array con todos los elementos que cumplan la condicion.

```js
const words = [
  "spray",
  "limit",
  "elite",
  "exuberant",
  "destruction",
  "present",
];

const result = words.filter((word) => word.length == 5);

console.log(result);
// Devuelve Array ['spray', 'limit', 'elite']
```

**forEach( );** Ejecuta la funcion indicada una vez por cada elemento del array.

```js
const array1 = ["a", "b", "c"];

array1.forEach((element) => console.log(element));

// Devuelve: "a"
// Devuelve: "b"
// Devuelve: "c"
```
**map( );** Ejecuta la funcion indicada una vez por cada elemento del array y los retorna en un nuevo array.

```js
const array1 = [1, 12, 31];

array1.map((element) => element*2);

// Devuelve: 2
// Devuelve: 24
// Devuelve: 62
```
**find( );** Ejecuta la funcion indicada una vez por cada elemento del array y retorna el valor que concuerde con la condición.
```js
const array1 = [1, 12, 31];

array1.find((element) => element===12);

// Devuelve: 12
```
**findIndex( );** Ejecuta la funcion indicada una vez por cada elemento del array y retorna la pocicion del valor que coincida con la condición.
```js
const array1 = [1, 12, 31];

array1.findIndex((element) => element===12);

// Devuelve: 12
```
**fill( );** Recorre y rellena los espacios de un array con un solo valor.
```js
const array1 = New Array(4);

array1.fill((element) => element===40);

// Devuelve: [40,40,40,40,40]
```
**every( );** Recorre todos los valores y devuelve false si todos no cumplen con la condición.
```js
const array1 = ['OK','OK','X','OK'];

array1.every((element) => element==='OK');

// Devuelve: false
```

**some( );** Recorre todos los valores y devuelve true si encuentra una coincidencia con la condicion.
```js
const array1 = ['OK','OK','X','OK'];

array1.some((element) => element==='X');

// Devuelve: true
```
---

## Metodos matematicos

**Math.**\_\_\_**;** Operaciones matematicas complejas.

**sqrt( );** Devuelve la raiz cuadrada positiva de un numero.

```js
var num1 = 3,
  num2 = 4,
  res,
  res2,
  res3;

res = Math.sqrt(num2); //Devuelve 2
res2 = Math.sqrt(num1 * 12); //Devuelve 6
res3 = Math.sqrt(num1 * num1 + num2 * num2); //Devuelve 5
```

**cbrt( );** Devuelve la raiz cubica de un numero.

```js
var num1 = 9,
  num2 = 8,
  res,
  res2,
  res3;

res = Math.cbrt(num2); //Devuelve 2
res2 = Math.cbrt(num1 * 24); //Devuelve 6
res3 = Math.cbrt(num1 * num1 + num2 * num2 - 20); //Devuelve 5
```

**pow( );** devuelve la potencia de un numero elevado de otro (numero,potencia).

```js
console.log(Math.pow(2, 3));
// Devuelve: 8
console.log(Math.pow(4, 0.5));
// Devuelve: 2
console.log(Math.pow(7, -2));
// Devuelve: 0.02040816326530612
//                  (1/49)
console.log(Math.pow(-3, 5));
// Devuelve: -243
console.log(Math.pow(-7, -0.5));
// Devuelve: NaN
```

**max( );** Devuelve el mayor de los numeros que se le den.

```js
console.log(Math.max(1, 3, 2));
// Devuelve: 3

console.log(Math.max(-1, -3, -2));
// Devuelve: -1

const array1 = [1, 3, 2];

console.log(Math.max(...array1)); //los 3puntos son necesarios ya que eliminan los corchetes.
// Devuelve: 3
```

**min( );** devuelve el menor de los numeros que se le den.

```js
console.log(Math.min(1, 3, 2));
// Devuelve: 1

console.log(Math.min(-1, -3, -2));
// Devuelve: -3

const array1 = [1, 3, 2];

console.log(Math.min(...array1)); //los 3puntos son necesarios ya que eliminan los corchetes.
// Devuelve: 1
```

**random( );** Devuelve un numero aleatorio menor a 1. Para obtener numeros enteros usar un metodo de redondeo.

```js
console.log(Math.random() * 5);
// Devuelve: un numero aleatorio <5 con decimales

console.log(Math.random() * 2);
// Devuelve: un numero aleatorio <2 con decimales
```

**round( );** Devuelve el valor de un numero redondeando al numero entero mas cercano.

```js
console.log(Math.round(0.9));
// Devuelve: 1
console.log(Math.round(5.95), Math.round(5.5), Math.round(5.05));
// Devuelve: 6 6 5
console.log(Math.round(-5.05), Math.round(-5.5), Math.round(-5.95));
// Devuelve: -5 -5 -6
```

**fround( );** Devuelve la representacion flotante de precicion simple. La función Math.fround() devuelve la representación flotante de precisión simple de 32 bits más cercana de un Number.

```js
console.log(Math.fround(5.5));
// Devuelve: 5.5
console.log(Math.fround(5.05));
// Devuelve: 5.050000190734863
console.log(Math.fround(5));
// Devuelve: 5
console.log(Math.fround(-5.05));
// Devuelve: -5.050000190734863
```

**floor( );** Devuelve el numero entero menor que, o igual al numero flotante que se le da.

```js
console.log(Math.floor(5.95));
// Devuelve: 5
console.log(Math.floor(5.05));
// Devuelve: 5
console.log(Math.floor(5));
// Devuelve: 5
console.log(Math.floor(-5.05));
// Devuelve: -6
```

**trunc( );** Devuelve la parte entera de un numero x, la eliminacion de decimales.

```js
console.log(Math.trunc(13.37));
// expected output: 13
console.log(Math.trunc(42.84));
// expected output: 42
console.log(Math.trunc(0.123));
// expected output: 0
console.log(Math.trunc(-0.123));
// expected output: -0
```

**PI;** El valor de PI 3.1415...

```js
console.log(Math.PI);
// Devuelve: 3.141592653589793
```

**E;** Constante de euler.

```js
console.log(Math.E);
// Devuelve: 2.718281828459045
```

**LN2;** Logaritmo natural de 2.

```js
console.log(Math.LN2);
// Devuelve: 0.6931471805599453
```

**LN10;** Logaritmo natural de 10.

```js
console.log(Math.LN10);
// Devuelve: 2.302585092994046
```

**Log2E;** logaritmo de E con base 2.

```js
console.log(Math.LOG2E);
// Devuelve: 1.4426950408889634
```

**Log10E;** Logaritmo de E con base 10.

```js
console.log(Math.LOG10E);
// Devuelve: 0.4342944819032518
```

---

## Consola

**Console.**\_**;** Se muestra la informacion que requerimos en la consola del navegador.

### Registro

**assert( );** Aparece un error en la consola si la afirmacion es falsa. No recomendada.

```js
console.assert(5 < 8); //No se muestra en la consola
console.assert(8 < 5); //Si se muestra en la consola
```

**clear( );** Limpia la consola.

```js
console.clear(); //Limpia la consola,elimina el rastro de la actividad anterior.
```

**error( );** Muestra un mensaje de error en la consola web, siendo este de color rojo.

```js
console.error("Lo que sea que hiciste, fallo");
//Se muestra en la consola con sus propiedades caracteristicas.
```

**info( );** Emite un mensaje informativo en la consola.

```js
console.info("Estas utilizando codigo obsoleto");
//Muestra mensaje
```

**log( );** Muestra un mensaje en la consola web, un mensaje con propositos de depuracion, como conocer valores de variables.

```js
console.log(`La variable 1 tiene el valor de: ${var1}`);
//Muestra la informacion
```

**table( );** Muestra una tabla con los datos que se le dan. funciona con Arrays y Objetos.

```js
console.table([6, 4, 8, 2, 9, 1, 4]);
//Muestra una tabla de dos columnas donde en una almacena el index y en la otra los numeros del array.
```

**warn( );** Emite un mensaje de advertencia en la consola, siendo este de color amarillo.

```js
console.warn("El codigo esta bien, pero...");
//Muestra la advertencia
```

**dir( );** Despliega una lista interactiva de las propiedades del objeto.

```js
console.dir([6, 4, 8, 2, 9, 1, 4]);
//Array (6) -- tipo de dato del contenido del dir
//Lista de elementos del array.
```

### Conteo

**count( );** Registra el numero de veces que se a llamado a este atributo.

```js
console.count(); // default 1
console.count(); // default 2
console.count(); // default 3
console.count(); // default 4
```

**countReset( );** Reinicia el contador console.count();

```js
console.count(); // default 3
console.count(); // default 4
console.countReset();
console.count(); // default 1
console.count(); // default 2
```

### Grupos

**group( );** Crea un nuevo grupo en la linea en el registro de la consola. Puedes darles nombres.

```js
console.group("grupo1");
console.group;
console.info("Estoy dentro de un grupo");
console.log("Mis operaciones pertenecen a este grupo");
console.group("grupo1.1");
console.group;
console.info("Estoy dentro de un grupo interno en otro grupo");
console.log("Mis operaciones pertenecen a este grupo dentro de otro grupo");
```

**grupEnd( );** Remueve un grupo en linea en el registro de la consola.

```js
console.group("grupo1");
console.group;
console.group("grupo1.1");
console.group;
//...Contenido del grupo1.1
console.groupEnd(); //Grupo finalizado
console.group("grupo1.2");
console.group;
//...Contenido del grupo1.2
console.groupEnd(); //Grupo finalizado
console.groupEnd(); //Grupo principal finalizado
```

**groupCollapsed( );** Similar a console.group, pero este no te despliega directamente el grupo. Lo mantiene cerrado.

```js
console.group("grupo1");
console.group;
```

### Tiempo

**time( );** Inicia un temporizador.

```js
console.time(); //Inicia el conteo del temporizador
```

**timeLog( );** Registra el valor actual de un temporizador ya en ejecucion. En milisegundos.

```js
console.time();
//pasan aproximadamente 3 segundos
console.timeLog(); //devuelve 3126.4389348943 ms
//pasan aproximadamente 4 segundos mas
console.timeLog(); //devuelve 7563.4354455456 ms
```

**timeEnd( );** Detiene el temporizador y devuelve el resultado final del temporizador.

```js
//pasan aproximadamente 3 segundos mas
console.timeEnd(); //devuelve 10095.123190802 ms
```

---

## DOM

### Seleccion de elementos.

**document.**\_\_\_**;** Metodo de seleccion de elementos del documento HTML.

```html
<h1 id="titulo">Titulo</h1>
<div class="contenedor">
  <div class="contenido">Parte 1</div>
  <div class="contenido">Parte 2</div>
  <p class="contenido">Parte 3</p>
  <div class="contenido">Parte 4</div>
  <div class="contenido">Parte 5</div>
</div>
```

**getElementById( );** Selecciona un elemento por el ID de la etiqueta.

```js
const selectId = document.getElementById("titulo");
//Almacena <h1 id="titulo">Titulo</h1>
console.log(selectId);
//Devuelve <h1 id="titulo">Titulo</h1>
```

**getElementsTagName( );** Selecciona todos los elementos que coincidan con el nombre de la etiqueta especificada.

```js
const selectTagName = document.getElementsByTagName("div");
//Almacena la lista de los elementos almacenados

console.log(selectTagName[0]);
//Devuelve <div class="contenedor">...</div>
console.log(selectTagName[1]);
//Devuelve <div class="contenido">Parte 1</div>
console.log(selectTagName[2]);
//Devuelve <div class="contenido">Parte 2</div>
console.log(selectTagName[3]);
//Devuelve <div class="contenido">Parte 4</div>
console.log(selectTagName[4]);
//Devuelve <div class="contenido">Parte 5</div>
```

**querySelector( );** Devuelve el primer elemento que coincida con el grupo especificado de selectores.

```js
const querySelect = document.querySelector(".contenedor");
//Almacena <div class="contenedor">...</div>
console.log(querySelect);
//Devuelve <div class="contenedor">...</div>
```

**querySelectorAll( );** Devuelve todos los elementos que coincidan con el grupo especificado de selectores.

```js
const querySelectAll = document.querySelectorAll(".contenido");
//Almacena la lista de los elementos almacenados

console.log(querySelectAll[0]);
//Devuelve <div class="contenido">Parte 1</div>
console.log(querySelectAll[1]);
//Devuelve <div class="contenido">Parte 2</div>
console.log(querySelectAll[2]);
//Devuelve <p class="contenido">Parte 3</p>
console.log(querySelectAll[3]);
//Devuelve <div class="contenido">Parte 4</div>
console.log(querySelectAll[4]);
//Devuelve <div class="contenido">Parte 5</div>
```

### Edicion de atributos

```html
<input type="text" value="" class="edAtributo" />
```

**setAttribute( );** Da la posibilidad de crear o editar los atributos de su elemento.

```js
const edA = document.querySelector(".edAtributo");
edA.setAttribute("type", "color"); // Modifico el valor del atributo.
edA.setAttribute("name", "colorizante"); // Creó el atributo y su valor.
```

```html
<input type="color" value="" class="edAtributo" name="colorizante" />
```

**getAttribute( );** Obtener el valor del atributo.

```js
var tipo, nombre;
//Conciderando los efectos de set attribute
tipo = edA.getAttribute("type"); // Devuelve color
nombre = edA.getAttribute("name"); // Devuelve colorizante
```

**removeAttribute( );** Remueve el valor de un atributo.

```js
//conciderando los efectos de set attribute
edA.removeAttribute("type"); // // Elimino el atributo.
edA.removeAttribute("name"); // Elimino el atributo.
```

```html
<input value="" class="edAtributo" />
```

### Atributos globales

```html
<h1 class="titulo">TITULO</h1>
```

**setAttribute(**\_\_\_**);** Prueba en cualquier elemento del HTML, en este caso se usara un h1.

**(contentEditable,valor);** indica si el elemento puede ser modificable por el usuario o no.

```js
const titulo = document.querySelector(".titulo");

titulo.setAttribute("contentEditable", "true");
//El texto de h1 puede editarse
titulo.setAttribute("contentEditable", "false");
//El texto de h1 no puede editarse
```

**(dir,valor);** Indica la direccionalidad del texto que se muestra.

```js
titulo.setAttribute("dir", "ltr");
//El texto se muestra de izquierda a derecha
titulo.setAttribute("dir", "rtl");
//El texto se muestra de derecha a izquierda
```

**(hidden,valor);** No importa que valor tenga, hidden oculta el elemento a menos de que sea removido.

```js
titulo.setAttribute("hidden", "true"); // o false
//El texto se oculta
```

**(tabindex,valor);** Enfoca el elemento al teclear Tab. Los valores son numericos y dependiendo del valor que se les de seran enfocados en orden con la tecla Tab.

```js
titulo1.setAttribute("tabindex", "0"); // Al dar click en tab por primera vez, esta propiedad se enfocara
titulo2.setAttribute("tabindex", "2"); // Al dar click en tab por tercera vez, esta propiedad se enfocara
titulo3.setAttribute("tabindex", "1"); // Al dar click en tab por segunda vez, esta propiedad se enfocara
```

**(title,valor);** Contiene un texto con informacion relacionada al elemento al que pertenece, muestra un titulo al hacer hover sobre el.

```js
titulo.setAttribute("title", "Este titulo esta muy simple"); //Muestra el titulo
```

style.**\_**; Contiene declaraciones de estilo css para ser aplicadas al elemento (usar camelCase).

```js
titulo.style.color = "blue"; //Muestra el titulo color azul, tambien puedes añadir colores en hexadecimal "#00f"
titulo.style.backgroundColor = "#000"; //Muestra el recuadro del titulo de color negro
```

### Atributos en inputs

```html
<input type="text" class="input-normal" value="Los pepinos" />
```

```js
const input = document.querySelector(".input-normal");
```

**className;** Revela el nombre de la clase o las clases del input.

```js
console.log(input.className);
//Devuelve "input-normal"
```

**value;** Revela el valor del input.

```js
console.log(input.value); //contenido del input
//Devuelve "Los pepinos"
```

**type;** Cambia el valor del atributo del input

```js
input.type = "number"; //Cambia el type text por el number
input.name = "El input es normal"; //Crea el atrib. name
```

**accept;** Acepta formatos con extenciones determinadas imge/png.

```js
input.accept = "image/gif"; //Tipo de imagen que acepta
```

**form;** Sirvepara hacer funcionar un input-submit mientras esta fuera del form.

```js
input.form = "nomForm"; //El valor debe ser igual al id del form principal y este input debe ser de tipo submit.
```

**minLength;** Minimo de caracteres que tendra el valor del input antes de ser enviado por el formulario.

```js
input.minLength = "4"; //El valor no se enviara si su contenido no es >=4.
```

**placeholder;** Crea un texto alternativo que desaparece cuando comienzas a escribir en el input.

```js
input.placeholder = "Texto de relleno";
```

**required;** Esta propiedad evita que el input envie su valor mientras se nulo (campo vacio).

```js
input.required = "Cualquier valor"; //preferentemente vacio
```

### classList

```html
<div class="clase-vieja">Contenedor</div>
```

```js
const playClass = document.querySelector(".clase-vieja");
```

classList.**\_**; Interactua col las clases de los elementos.

**add( );** Añade una clase al elemento.

```js
playClass.classList.add("clase-nueva");
//ahora su clase es:  class= "clase-vieja clase-nueva"
```

**remove( );** Elimina una clase del elemento.

```js
playClass.classList.remove("clase-nueva");
//ahora su clase es:  class= "clase-vieja"
```

**item( );** Muestra la clase col la pocicion indicada

```js
playClass.classList.item(0);
//Muestra la clase "clase-vieja"
playClass.classList.item(1);
//Muestraria la clase "clase-nueva" si no la hubiera eliminado
```

**contains( );** Devuelve true si la clase incorporada esta en el elemento y false si no es asi.

```js
playClass.classList.contains("clase-vieja");
//Devuelve true
playClass.classList.contains("clase-nueva");
//Devuelve false ya que la elimine
```

**remplace( );** Cambia una clase por otra.

```js
playClass.classList.remplace("clase-vieja", "clase-nueva");
//Ahora la clase es: "clase-nueva"
```

**toggle( );** Si tiene la clase especificada la elimina y si no la incorpora.

```js
playClass.classList.toggle("clase-nueva");
//Elimino la clase, ahora ya no tiene clases.
playClass.classList.toggle("clase-nueva");
//A vuelto a incorporar la clase "clase-nueva"
```

### Obtencion y modificacion del elemento

Contenido

```html
<p class="parrafo">
  Las nueves son oscuras cuando se aproxima una
  <b style="visibility: hidden;">tormenta</b>.
</p>
```

```js
const texto = document.querySelector(".parrafo");
```

**textContent;** Devuelve el texto de cualquier nodo, apesar de estar oculto.

**innerText;** Devuelve el texto visible de un nodo element. **"Obsoleta"**

**outerText;** Devuelve el texto que de las etiquetas html incluidas las etiquetas. **"Obsoleta"**

**innerHTML;** Devuelve el contenido html de un elemento, incluyendo los efectos de las etiquetas internas.

**outerHTML;** Devuelve el codigo html completo del elemento.

```js
console.log(texto.textContent); //Devuelve "Las nueves son oscuras cuando se aproxima una tormenta.
console.log(texto.innerHTML); //Devuelve "Las nueves son oscuras cuando se aproxima una.
console.log(texto.outerHTML); //Devuelve "Las nueves son oscuras cuando se aproxima una.
```

Creacion de elementos

**document.**\_**;** Creacion de elementos desde JS.

```html
<div class="contenedor"></div>
```

```js
const contenedor = document.querySelector(".contenedor");
```

**createElement();** Crea elemento por etiqueta HTML.

```js
const item = document.createElement("P");
//Creo un parrafo <p></p>
//Aun no se incorpora al DOM
```

**createTextNode();** Crea un texto para el elemento.

```js
var textP = item.crateTextNode("Este es el contenido de parrafo");
//Crea un objeto que almacena el contenido
//Aun no se incorpora al DOM
```

**appendChild();** Fuciona el texto con el elemento.

```js
item.appendChild(textP);
//Fusiono y quedo: <p>Este es el contenido de parrafo</p>
//Aun no se incorpora al DOM
contenedor.appendChild(item); //introduce el parrafo en el DOM ya que contenedor es un elemento existente en el HTML
```

**createDocumentFragment();** Utilizar en el appendchild para disminuir recursos.

```js
const contenedor = document.querySelector(".contenedor");
const fragmento = createDocumentFragment();
//Creare 20 parrafos
for (let i = 0; i < 20; i++) {
  const item = document.createElement("P");
  item.innerHTML = "Este es un texto para el parrafo";
  fragmento.appendChild(item);
}
//Introdusco los 20 parrafos en el contenedor
contenedor.appendChild(fragmento);
```

Obtencion de los elementos hijos

```html
<div class="contenedor">
  <h2 class="h2-viejo">titulo2</h2>
  <p class="p1">Este es el parrafo1</p>
  <p>Este es el parrafo2</p>
</div>
```

```js
const contenedor = document.querySelector(".contenedor");
```

**contenedor.**\_\_\_**;** Buscara en la etiqueta padre.

**firstChild;** muestra el primer hijo.

```js
const primerHijo = contenedor.firstChild;
//Almacena #text ya que esta propiedad considera al valor que esta aun lado del principio de la etiqueta. es decir: <div class="contenedor">...
```

**lastChild;** muestra el ultimo hijo

```js
const ultimoHijo = contenedor.lastChild;
//Almacena #text ya que esta propiedad considera al valor que esta aun lado del final de la etiqueta. es decir:
//...</div>
```

**firstElementChild;** Es mas preciso con respecto al siguiente elemento hijo

```js
const primerHijoE = contenedor.firstElementChild;
//Almacena <h2>titulo2</h2>
```

**lastElementChild;** Es mas preciso con respecto al siguiente elemento hijo

```js
const UltimoHijoE = contenedor.firstElementChild;
//Almacena <p>Este es el parrafo2</p>
```

**childNodes;** Muestra todos los hijos

```js
const hijos = contenedor.childNodes;
//Almacena todos los hijos, incluso si no son etiquetas
// #text
// <h2>titulo2</h2>
// #text
// <p>Este es el parrafo1</p>
// #text
// <p>Este es el parrafo2</p>
// #text
hijos.forEach((hijo) => console.log(hijo)); //Usar para recorrer cada hijo
```

**children;** Muestra las etiquetas de los hijos.

```js
const hijosE = contenedor.children;
//Almacena todos los hijos con etiqueta
// <h2>titulo2</h2>
// <p>Este es el parrafo1</p>
// <p>Este es el parrafo2</p>
for (const hijo of hijosE) {
  console.log(hijo);
} //usar para recorrer cada hijo
```

Modificacion de los elementos hijos

**replaceChild( );** remplaza el elemento por otro;

```js
//Se crea un elemento nuevo
const h2Nuevo = document.createElement("h2");
h2Nuevo.innerHTML = "nuevo titulo";
//Se captura el elemento a remplazar
const h2Viejo = document.querySelector(".h2-viejo");

contenedor.replaceChild(h2Nuevo, h2Viejo);
//Se remplaza el titulo2
```

**removeChild( );** Elimina el elemento.

```js
const h2Viejo = document.querySelector(".h2-viejo");

contenedor.removeChild(h2Viejo);
//Ya no hay <h2>
```

**hasChildNodes( );** Sirve para comprobar si tiene o no elementos hijo, devolviendo true si tiene y false si no es asi.

```js
contenedor.hasChildNodes();
//Da true por que el contenedor si tiene hijos
```

Propiedades de elementos padre

**parentElement;**

```js
const h2Viejo = document.querySelector(".h2-viejo");
h2Viejo.parentElement;
//Muestra al padre del elemento, solo si tiene una etiqueta
```

**parentNode;**

```js
const h2Viejo = document.querySelector(".h2-viejo");

h2Viejo.parentNode;
//Muestra al padre del elemento, aunque solo sea un texto
```

Propiedades de elementos hermanos

**nextSibling;** Muestra el siguiente nodo hermano.

```js
const hermanoSig = h2Viejo.nextSibling;
//Almacena #text ya que esta propiedad considera al valor que esta aun lado del final de la etiqueta analizada. es decir: </h2> ...
```

**previousSibling;** Muestra el nodo hermano anterior.

```js
const pNum1 = document.querySelector(".p1");
const hermanoAnt = pNum1.previousSibling;
//Almacena #text ya que esta propiedad considera al valor que esta aun lado del principio de la etiqueta analizada. es decir: ...<h2>
```

**nextElementSibling;** Es mas preciso, busca a una etiqueta.

```js
const hermanoSigE = h2Viejo.nextElementSibling;
//Almacena el siguiente hermano <p>...</p>
```

**previousElementSibling;** Es mas preciso, busca a una etiqueta.

```js
const hermanoAntE = pNum1.previousElementSibling;
//Almacena el siguiente hermano <h2>...</h2>
```

Nodos extras

**closest( );** Selecciona el elemento acendente mas sercano, segun el tipo.

```html
<div>
  div1
  <div>
    div2
    <div class="div-3">Div3</div>
  </div>
</div>
```

```js
const div = document.querySelector(".div-3");

div.closest("div");
// Busca el div acendente mas sercado.
// Como resultado da <div>
//                      div2
//                      <div class="div-3">Div3</div>
//                    </div>
```

---

## POO

### Conceptos basicos

Class y objeto

```js
class Objeto {
  //La clase inicializa al objeto
  //El objeto es la finalidad de la clase
}
```

Atributos Y Metodos

```js
class Gato {
  nombre = "Eris"; //Atributos
  edad = 2;
  sonido = function maullar() {
    //Metodo
    console.log("miau");
  };
}
```

Constructor

```js
class Mascota {
  constructor(nombre, tipo, color) {
    this.nombre = nombre; //reciben el valor del
    this.tipo = tipo; //    parametro
    this.color = color;
    this.presentacion = `Hola, me llamo ${nombre} y soy un ${tipo} de color ${color}.`;
  }
  verInfo() {
    console.log(this.presentacion);
  }
} //Da la posibilidad de generar instancias
//Los metodos se ponen fuera del constructor
```

Instancias

```js
const mascota1 = new Mascota("Eris", "gato", "blanco");
const mascota2 = new Mascota("Canela", "perro", "negro");
const mascota3 = new Mascota("Perla", "canario", "azul");
//Genera varios objetos de la misma categoria

mascota1.verInfo(); // Aplicando el metodo con las
mascota2.verInfo(); // 3 instancias
mascota3.verInfo();
```

### Caracteristicas

Abstraccion

```js
class Mascota {
  constructor(nombre, tipo, color) {
    //simplifica el objeto al minimos de sus atributos y metodos
    this.nombre = nombre;
    this.tipo = tipo;
    this.color = color;
  } //Reducir el objeto a sus propiedades principales
}
```

Herencia

```js
class Mascota {
  constructor(nombre, tipo, color) {
    this.nombre = nombre;
    this.tipo = tipo;
    this.color = color;
  }
}
class Perro extends mascota {
  //Herencia
  constructor(nombre, tipo, color, raza) {
    super(nombre, tipo, color);
    this.raza = raza;
  }
  ladrar() {
    console.log("GUAU");
  }
}
const perro1 = Perro.ladrar(); //ladra
const perro2 = Perro.ladrar(); //ladra
const mascota1 = Mascota.ladrar(); //No ladra ya que ladrar es un metodo de perro, no de mascota.
```

Metodos estaticos

```js
class Perro extends mascota {
  constructor(nombre, tipo, color, raza) {
    super(nombre, tipo, color);
    this.raza = raza;
  }
  static ladrar() {
    //Ignora las propiedades de la clase y solo da resultados cuando no involucra parametros ya que la instancia aun no es creada.
    console.log("GUAU"); //Funciona
  }
  static saludar() {
    //No Funciona
    console.log(`Hola soy un ${tipo} de raza ${raza}`);
  }
}
Perro.ladrar(); //No necesitas crear una nueva instancia para hacerlo funcionar, solo tienes que colocar el nombre de la clase
```

Encapsulamiento getter y setter

```js
class Perro extends mascota {
  constructor(nombre, tipo, color, raza) {
    super(nombre, tipo, color);
    this.raza = "null";
  }
  set setRaza(cambioRaza) {
    //Editar el cambio de
    this.raza = cambioRaza; //raza
  }
  get getRaza() {
    //Optener el cambio de raza
    return this.raza;
  }
}
const perro1 = new Perro("Canela", "perro", "negro", "doberman"); //Se crea el perro 1
perro1.setRaza = "dalmata";
console.log(perro1.getRaza);
```

Modularidad

```js
//Se refiere a saber organizar el flujo de trabajo para no perderse en el
class Mascota {
  constructor() {}
}
class Perro extends mascota {
  constructor() {
    super();
  }
}
//Instancias
```

Polimirfismo

```js
class Mascota {
  constructor(nombre, tipo, color) {
    this.nombre = nombre;
    this.tipo = tipo;
    this.color = color;
  }
  emitirSonido() {
    //Ejemplo de polimorfismo
    if (this.tipo == "perro") {
      console.log("wuau");
    } else if (this.tipo == "gato") {
      console.log("miau");
    } else {
      console.log("pio");
    }
  }
}
const mascota1 = new Mascota("Eris", "gato", "blanco");
const mascota2 = new Mascota("Canela", "perro", "negro");
const mascota3 = new Mascota("Perla", "canario", "azul");
mascota1.emitirSonido(); //ladra
mascota2.emitirSonido(); //maulla
mascota3.emitirSonido(); //pía
```

---

## Window

**window.**\_\_\_**;** Hereda las propiedades de eventTarget.

### Eventos de ventana

**open( );** Abre un navegador en una nueva ventana (url del sitio web).

```js
window.open("https://www.youtube.com");
//Al ejecutar mustra youtube en una ventana nueva
```

**close( );** Cierra la ventana del navegador abierto.

```js
var ventana = window.open("https://www.youtube.com");
ventana.close();
//Al ejecutar cierra la ventana recien abierta
```

**closed;** Muestra true si la ventana a sido cerrada y false si no es asi.

```js
var ventana = window.open("https://www.youtube.com");
ventana.closed; //Muestra false
ventana.close();
ventana.closed; //Muestra true
```

**stop( );** Detiene el proceso de carga de la ventana del navegador.

```js
var ventana = window.open("https://www.youtube.com");
ventana.stop();
//Al ejecutar interrimpe la carga de la pagina
```

**print();** Muestra la herramienta de imprecion del navegador.

```js
print();
```

### Eventos de ventana

\***\*screen;\*\*** Devuelve una referencia al objeto de pantalla asociado con la ventana.

```js
const screen = window.screen;
console.log(screen); //Muestra el objeto con las propiedades de la ventana
console.log(screen.availHeight); //Muestra el valor de la propiedad: 812
```

\***\*screenLeft;\*\*** Devuelve el valor horizontal entre el borde izq del la pantalla y el borde izq de la ventana del navegador.

\***\*screenTop;\*\*** Devuelve el valor vertical entre el borde superior del la pantalla y el borde superior de la ventana del navegador.

```js
const varScreen1 = window.screenLeft;
const varScreen2 = window.screenTop;
```

\***\*scrollX;\*\*** Devuelve el valor de px que el documento se desplaza horizontalmente con el scroll.

\***\*scrollY;\*\*** Devuelve el valor de px que el documento se desplaza verticalmente con el scroll.

```js
const ScrollX = window.scrollX;
const ScrollY = window.scrollY;
```

\***\*scroll( );\*\*** Desplaza la ventana a un lugar particular en el documento.

```js
window.scroll(0, 200); //Desplaza en pixeles
```

\***\*resizeBy( );\*\*** Cambia el tamaño de la ventana actual en una cantidad especifica de pixeles.

\***\*resizeTo( );\*\*** Cambia el tamaño de la ventana actual en una cantidad especifica de pixeles.

\***\*moveBy( );\*\*** Mueve la ventana en una ubicacion relativa.

\***\*moveTo( );\*\*** Mueve la ventana en una ubicacion absoluta.

```js
var ventana = window.open("https://www.youtube.com");
ventana.resizeBy(200, 400); //Solo funcionan del lado
ventana.resizeTo(200, 400); //del servidor
ventana.moveBy(100, 300);
ventana.moveTo(100, 300);
```

### Localizacion

**location.**\_\_\_**;** Propiedad de localizacion.

assign( ) - carga un nuevo documento.

**href;** Devuelve el url de la pagina actual.

**hostname;** Devuelve el nombre de dominio del servidor web.

**pathname;** Devuelve la ruta y el nombre de archivo de la pagina actual.

**protocol;** Devuelve el protocolo web utilizando (http, https).

```js
window.location.href;
window.location.hostname;
window.location.pathname;
window.location.protocol;
//window.location.assign();
```

Herramientas de desarrollo del navegador, entra a inspeccionar elemento en el navegador.

---

## Eventos

**propiedad.add**\_\_**;** Adiere el evento.

**propiedad.remove**\_\_**;** Elimina el evento.

```html
<div class="carta">Esta es una carta</div>
```

```js
const carta = document.querySelector(".carta");
```

### MAUSE

**EventListener("click",Evento);**

```js
carta.addEventListener("click", () => {
  //Dando click
  //funcion a realizar
});
```

**EventListener("dblclick",Evento);**

```js
carta.addEventListener("dblclick", () => {
  //Dando doble click
  //funcion a realizar
});
```

**EventListener("mouseover",Evento);**

```js
carta.addEventListener("mouseover", () => {
  //Cuando pasas el mause por encima del elemento
  //funcion a realizar
});
```

**EventListener("mouseout",Evento);**

```js
carta.addEventListener("mouseout", () => {
  //Cuando pasas el mause por encima del elemento o fuera de sus elementos
  //funcion a realizar
});
```

**EventListener("contextmenu",Evento);**

```js
carta.addEventListener("contextmenu", () => {
  //Cuando das click derecho
  //funcion a realizar
});
```

**EventListener("mouseleave",Evento);**

```js
carta.addEventListener("mouseleave", () => {
  //Cuando el puntero se mueve fuera de un elemento
  //funcion a realizar
});
```

**EventListener("mousedown",Evento);**

```js
carta.addEventListener("mousedown", () => {
  //Cuando aprietas un boton del mause
  //funcion a realizar
});
```

**EventListener("mouseup",Evento);**

```js
carta.addEventListener("mouseup", () => {
  //Cuando sueltas el boton del mause
  //funcion a realizar
});
```

### Teclado

**EventListener("keyup",Evento);**

```js
carta.addEventListener("keyup", () => {
  //Cuando una tecla se deja de precionar
  //funcion a realizar
});
```

**EventListener("keydown",Evento);**

```js
carta.addEventListener("keydown", () => {
  //Cuando una tecla se preciona
  //funcion a realizar
});
```

**EventListener("keypress",Evento);**

```js
carta.addEventListener("keypress", () => {
  //Cuando una tecla se preciona y se deja de precionar
  //funcion a realizar
});
```

### Interfaz

**EventListener("error",Evento);**

```js
carta.addEventListener("error", () => {
  //Cuando ocurre un error al cargar la pagina
  //funcion a realizar
});
```

**EventListener("load",Evento);**

```js
window.addEventListener("load", () => {
  //Cuando el elemento se termine de cargar
  //funcion a realizar
});
```

**EventListener("beforeunload",Evento);**

```js
window.addEventListener("beforeunload", () => {
  //Cuando el usuario esta por cambiar del sitio web desde una misma pestaña
  //funcion a realizar
});
```

**EventListener("unload",Evento);**

```js
window.addEventListener("unload", () => {
  //Cuando el usuario cambia del sitio web desde una misma pestaña.
  //funcion a realizar
});
```

**EventListener("resize",Evento);**

```js
window.addEventListener('resize',() => {
    //Cuando se actualiza la resolucion del navegador
    //funcion a realizar
```

**EventListener("scroll",Evento);**

```js
window.addEventListener('scroll',() => {
    //Cuando se realiza un scroll
    //funcion a realizar
```

**EventListener("select",Evento);**

```js
window.addEventListener('select',() => {
    //Cuando se selecciona un texto
    //funcion a realizar
```

### Propiedades

```js
carta.addEventListener("click", (e) => {
  //Usa el parametro e para utilizar sus propiedades
  e.target; //En el se encuentran las propiedades de la etiqueta.
  e.stopPropagation(); //Detiene la herencia de eventos a los elementos hijos
  e.preventDefault(); //Previene el comportamiento por defecto del atributo (en los formularios no envian los datos).
});
```

### Temporizadores

**setTimeout(funcion, tiempo);** Temporizador de una sola ejecucion.

```js
const temporisador1 = setTimeout(() => {
  document.write("hola");
}, 2000); //Espera 2s y ejecuta la funcion
```

**setInterval(funcion, tiempo);** Temporizador de varias ejecuciones.

```js
const temporisador2 = setInterval(() => {
  document.write("hola");
}, 2000); //Espera 2s y cada 2s ejecuta la funcion
```

**clearTimeout();** o **clearInterval();** Detiene el proceso de los temporizadores.

```js
clearTimeout(temporisador1); //Detiene el setTimeout
clearInterval(temporisador1); //Detiene el setInterval**
```

blques { let var = 23} seleccion el valor de la variable que esta entre las llaves.

---

## Sentencia de error

```js
try {
  //Control de errores
  throw {
    //Ecepcciones
    error: "nombre del error",
    infoError: "informacion del error",
  };
  sgdgdgrigjiguig; //try contiene los errores que puedan ocurrir en nuestro codigo, menos los de sintaxis.
} catch (error) {
  console.log(error.error); //la forma en como los solucionaremos
  console.log(error.infoError); //la forma en como los solucionaremos
} finally {
  console.log("Apesar de todo, me muestro");
  //Haya error o no, se muestra
}
```

desventajas de manera obsoleta
buscar en la pagina oficial procesos estandares

---

## Callbacks y Promesas

### Calback

Una funcion dentro de otra funcion.

```js
function prueba(calback) {
  //El parametro recibe la funcion
  calback(2, 5, 7); //Se ejecuta la funcion interna
}
function Suma(num1, num2, num3) {
  //Esta funcion recibe los parametros de la funcion interna
  return num1 + num2 + num3; //Resultado
}

prueba(Suma); //La funcion prueba recibe como parametro a la funcion Suma
```

### Promise

Objeto que permite usar calbacks para generar menos codigo.

```js
let nombre = "pedro";
const promesa = new promise((resolve, reject) => {
  if (nombre !== "pedro") reject("no es pedro");
  else resolve(nombre);
});
// Los datos estan encapsulados por lo que se necesita realizar otro procedimiento para optener el resultado.
promesa
  .then((resultado) => {
    //recibe un callback para dar el resultado
    console.log(resultado); //imprime cuando si es pedro, llama al resolve.
  })
  .catch((e) => {
    console.log(e);
  }); // imprime cuando no es pedro(error), llama al reject

//Otras formas de usar promesas
const sumar = (num1, num2, num3) => {
  return new promise((res, rej) => {
    if (
      typeof num1 == "number" &&
      typeof num2 == "number" &&
      typeof num3 == "number"
    )
      res(num1 + num2 + num3);
    else rej("No uses caracteres para la suma");
  })
    .then((resultado) => {
      console.log(resultado);
    })
    .catch((e) => {
      console.log(e);
    });
};

const sumar = function (num1, num2, num3) {
  return new promise((res, rej) => {
    if (
      typeof num1 == "number" &&
      typeof num2 == "number" &&
      typeof num3 == "number"
    )
      res(num1 + num2 + num3);
    else rej("No uses caracteres para la suma");
  })
    .then((resultado) => {
      console.log(resultado);
    })
    .catch((e) => {
      console.log(e);
    });
};
```

### Funciones Asincronas

Funciones que te permiten manejar promesas, y ordenar el contenido optenido por estas. Alternativa al .then()

```js
const obtenerInformacion = (text) => {
  return new Promise((res, rej) => {
    setTimeout(() => {
      //Espera un tiempo antes de ejecutarse
      res(text);
      rej("Ocurrio un error");
    }, Math.random() * 5); //Tardaran entre 0s a 5s
  });
};
const mostrarData = async () => {
  let data1 = await obtenerInformacion("1: primer recuadro");
  let data2 = await obtenerInformacion("2: segundo recuadro");
  let data3 = await obtenerInformacion("3: tercer recuadro");
  console.log(data1); //Muestra los resultados
  console.log(data2); //de la promesa
  console.log(data3);
};
mostrarData();
```

---

## Peticion HTTP

Conexion para que el cliente envie una peticion al servidor, y el servidor responde hacia el cliente.

### Json

JavaScript Object Notation

```js
// Objeto json en js
objeto = {
  nombre: "Pablo",
  apellido: "Bautista",
  incrito: true,
  edad: 18,
};

//Objeto serializado, convertido en string
objeto = '{"nombre":"Pablo","apellido":"Bautista","incrito":true,"edad":18}';
```

**JSON.stringifi( );** Serializa un objeto json.

```js
// Objeto json en js
const deserialisado = {
  nombre: "Pablo",
  apellido: "Bautista",
  incrito: true,
  edad: 18,
};

const serializado = JSON.stringifi(deserializado);
//El envio de datos al servidor debe ser serializado
```

**JSON.parse( );** Deserializa un objeto serializado.

```js
//Objeto serializado, convertido en string
serializado =
  '{"nombre":"Pablo","apellido":"Bautista","incrito":true,"edad":18}';

const deserializado = JSON.parse(serializado);
```

### AJAX

Asincronimo JavaScript and XML
Usar unicamente desde un servidor virtual, como xamp o wamp.

**XMLHttpRequest();**

```js
const peticion = new XMLHttpRequest();
peticion.addEventListener("readystatechange", () => {
  if (peticion.readyState == 4 && peticion.status == 200) {
    console.log(peticion.response); //Muestra el objeto del documento informacion.txt
  }
}); // status evalua si el documento a sido encontrado, valor de 200 si es correcto
//readystatechange cambia 4 veces y devuelve {1-4}
// 1 La solicitud se creo correctamente
// 2 La solicitud se envio correctamente
// 3 Procesando la peticion
// 4 Finalizacion
peticion.open("GET", "informacion.txt");
// o POST, Url o ubicacion y nombre de archivo
peticion.send(); //Se envia la peticion

console.log(peticion); //Muestra el objeto del documento

// Nuevo metodo
const peticion = new XMLHttpRequest();
peticion.addEventListener("load", () => {
  let respuesta;
  if (peticion.status == 200) respuesta = peticion.response;
  else respuesta = "El recurso no se ha encontrado";
  console.log(JSON.parse(respuesta).nombre);
  //Deserializamos el objeto y buscamos nombre en el Json
});
peticion.open("GET", "informacion.txt");
peticion.send();

console.log(peticion);
```

**activeXObject();** Complemento para dar soporte a navegadores que no soportan el XMLHttpRequest.

```js
if (window.XMLHttpRequest) {
  let peticion = new XMLHttpRequest();
} else {
  let peticion = new ActiveXObject("Microsoft.XMLHTTP");
}
```

Peticiones Post

```js
// Nuevo metodo
const peticion = new XMLHttpRequest();
peticion.addEventListener("load", () => {
  let respuesta;
  if (peticion.status == 200 || peticion.status == 201)
    respuesta = peticion.response;
  else respuesta = "El recurso no se ha encontrado";
  console.log(JSON.parse(respuesta));
});
peticion.open("Post", "https://reqres.in/api/users");
//Metodo post, URL para enviar las peticiones por este metodo
peticion.setRequestHeader("content-type", "application/json;charset=UTF8");
peticion.send(
  JSON.stringifi({
    name: "morpheus",
    job: "leader",
  })
);
```

### Fetch

Es una forma simplificada de hacer peticiones http.

Usando **Get**

```js
var peticionGet = fetch("https://reqres.in/api/unknown/2");
//fetch tiene get por defecto.//Se crea una promesa
peticionGet.then((res) => res.json()).then((res) => console.log(res));
```

Usando **Post**

```js
var peticion = fetch("https://reqres.in/api/users", {
  method: "POST",
  body: JSON.stringify({
    name: "morpheus",
    job: "leader",
  }),
  headers: { "content-type": "application/json" },
});
peticion.then((res) => res.json()).then((res) => console.log(res));
```

**text( );** Devuelve la promesa con el json serializado.

```js
peticionGet
  .then((res) => res.text()) //Elimina la primera capa de la promesa
  //text() nos da el json serializado.(en string);
  .then((res) => console.log(JSON.parse(res))); //Desencapsula la peticion y nos permite ver el json
```

**json( );** Devuelve la promesa con el json deserializado.

```js
peticionGet
  .then((res) => res.json()) //Elimina la primera capa
  .then((res) => console.log(res)); //Devuelve el objeto json y nos permite verlo
```

**blob( );** Es utilizada para imagenes.

```html
<img src="" id="pintura" />
```

```js
const imagen = document.querySelector(".pintura");
fetch("imagen.jpg")
  .then((res) => res.blob()) //Se usa para decifrar el formato blob
  .then((img) => (imagen.src = URL.createObjectURL(img)));
//Crea una url para el atributo img, con el fin de que la imagen se muestre como si su direccion estuviese en el src de la etiqueta img
```

### Axios

libreria en html:

```html
<script src="http://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<!-- Poner antes del codigo -->
```

```js
axios.("archivo.txt")
	.then(res=>console.log(res.data));

axios.post("https://reqres.in/api/users",{
    "name": "morpheus",
        "job": "leader"
})
	.then(res=>console.log(res.data))
```

### Fetch y Axios con funciones asincronas

Con fetch

```js
const getName = async () => {
  let peticion = await fetch("informacion.txt"); //Desencapsula la primera capa
  let resultado = await peticion.json();
  console.log(resultado.nombre);
};
getName();
```

con axios

```js
const getName = async () => {
  let resultado = await axios("informacion.txt"); //solo necesitas una linea de codigo
  console.log(resultado.data.nombre);
};
getName();
```

---

## Prototipos

Todo en javaScript tiene por lo menos el prototipo object, exepto los tipos de datos null, y undefined.
Los metodos estan alojados en los prototipos,

### Tiene 1 prototipo (objeto)

```js
var objeto = {
  Nombre: "Jorge",
  Edad: 23,
};
console.log(objeto._proto_);
//tiene el prototipo object
```

### Tienen 2 prototipos (el tipo de dato y el objet)

```js
var string = "Valor";
console.log(string._proto_);
//tiene ademas el prototipo string

var number = 15;
console.log(number._proto_);
//tiene ademas el prototipo number

var boleano = false;
console.log(boleano._proto_);
//tiene ademas el prototipo boleano

var array = ["Valor", 5, 12, "valor2", "cadena"];
console.log(array._proto_);
//tiene ademas el prototipo array
```

### Creacion de prototipos

```js
//No tiene prototipo  ƒ () { [native code] }
var funcion = function () {};
console.log(funcion.__proto__);

//Creacion de prototipo
console.log(funcion.prototype);
//Accedemos a los prototipos que creamos
console.log(funcion.prototype.__proto__);
```

### Prototipos en clases

```js
class Objeto {
  constructor() {}
  hablar() {
    console.log("Hola");
  }
}
let objeto = new Objeto();

objeto.hablar = () => {
  console.log("Hola fuera del prototipo");
};

objeto.__proto__.hablar = () => {
  console.log("Hola absoluto"); //Cambio desde el prototipo
};

let arr = [],
  arr2 = [];
arr.__proto__ = objeto;
arr2.__proto__ = objeto.__proto__;
arr.hablar(); //devuelve hola afuera del prototipo
arr2.hablar(); // devuelve hola absoluto
```

---

## Modo estricto

Su localizacion en el documento es importante.
Las palabras recervadas no pueden ser usadas para nombrar las variables.
Las funciones flechas no pueden ser usadas para hacer metodos ni costructores.
this y window son lo mismo a menos que este dentro de una clase u objeto.

```js
"use strict"; //Modo estricto

nombre = "Jose"; // error
var nombre = "jose"; //forma correcta

const obj = {};
object.defineProperty(obj, "nombre", { value: "jose", writeable: false }); //define propiedades del objeto			permite editar el valor o no.
obj.nombre = "Fernando"; //no funciona si esta en modo estricto

delete obj.nombre; //se usa para eliminar propiedades

object.preventExtensions(obj); // no permite añadir mas atributos como apellido

console.log(0o34); //sintaxis para numeros octales
```

---

## Fuciones recurcivas

### Se invoca a si misma

```js
function darVuelta() {
  darVuelta();
}
darVuelta();
```

### Por Evento

```js
const btn = document
  .querySelector("#titulo")
  .addEventListener("click", ejecutar());

const ejecutar = () => {
  //Ejecuta instruccion
};
```

### Parametros infinitos (rest)

El parametro rest siempre debe ir al final.

```js
const suma=(frase,...num)=>{//Crea un array con los parametros
    let resultado=0;
    for (let i = 0; i < num.length; i++) {
        resultado +=num[i];
    }
    console.log(`${frase} ${resultado}`);
}
suma("la suma es:",12,34,53,1);//Parametros infinitos
}
```

---

## API's

API's - interfaz de programacion de aplicaciones.

### Fechas

**getDate( );** Muestra la fecha temporal total, demas de otros datos complementarios.

```js
const var= date();//dia, numDia, mes, año, hora, etc.
// API de tipo string

const fecha= new date();//dia, numDia, mes, año, hora, etc. API de tipo objeto
```

**getdate( );** Nos devuelve el numero de dia del mes.

```js
fecha.getdate(); //Devuelve 8 porque es dia 8
```

**getDay( );** Devuelve el numero del dia de la semana (Dom 0 - Sab 6).

```js
fecha.getDay(); //Devuelve 5 porque es viernes.
```

**getMonth( );** Devuelve el numero de mes (Enero 0 - Diciembre 11).

```js
fecha.getMonth(); //Devuelve 3 porque estoy en el mes de abril
```

**getYear( );** Devuelve el año actual - 1900.

```js
fecha.getYear(); //Devuelve 122 ya que el año es 2022
```

**getHours( );** Devuelve la hora.

```js
fecha.getHours(); //Devuelve 12 ya que son las 12 de la tarde.
```

**getMinutes( );** Devuelve los minutos.

```js
fecha.getMinutes(); //Devuelve 30 ya que son las 12:30
```

**getSeconds( );** Devuelve los segundos.

```js
fecha.getSeconds(); //Devuelve 20 ya que son las 12:30:20
```

### Localizacion temporal

```js
var fechaEspecifica = new Date(1000000000);
//Se coloca la fecha en milisegundos y cada resultado de las propiedades correspondera a esa fecha.

var fechaEspecifica = new Date(2001, 03, 09);
//Se coloca la fecha (año,mes,dia de la semana), los resultados de sus propiedades daran resultados con base a la fecha especifica
```

### Localstorage y sessionstrorege

Objetos de almacenamiento de datos.

**Localstorage** y **sessionstorage**; Almacenamiento local y de session.

el almacenamiento local es permanente mientras que el de secion depende de su constante funcionamiento (si se cierra la pestaña desaparece).

Dar click en aplicaciones y despues ir a la seccion de almacenamiento del inspector del navegador. Dependiendo si es local o de secion, podras encontrar tus variables en sus respectivas opciones.

**setItem( );** Agrega un dato a guardar en el disco local o de session.

```js
localstoage.setItem("Name", "juan");
//guarda en el almacenamiento local
sessionstorage.setItem("Name", "juan");
//guarda en el almacenamiento de secion
```

**getItem( );** Devuelve el valor de una variable almacenada.

```js
localstoage.getItem("Name");
//Devuelve juan
sessionstorage.getItem("Name");
//Devuelve juan, mientras no se haya cerrado la pagina
```

**removeItem( );** Remueve un valor del amacenamiento.

```js
localstoage.removeItem("Name");
//Remueve el valor y la categoria almacenada
sessionstorage.removeItem("Name");
//Remueve el valor y la categoria almacenada
```

**clear( );** Remueve todos los valores de almacenamiento.

```js
localstoage.clear();
//Elimina todo el contenido almacenado
sessionstorage.clear();
//Elimina todo el contenido almacenado
```

### Drag y drop

Es una API que permite arrastrar objetos en un area especifica.

En el html:

```html
<div class="circulo"></div>
<div class="rectangulo"></div>
```

En css:

```css
body {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.circulo {
  background-color: red;
  border-radius: 50%;
  padding: 40px;
  display: inline-block;
  margin: 10px;
}
.rectangulo {
  padding: 100px 200px;
  margin: 50px;
  background-color: grey;
}
```

En js:

```js
const circulo = document.querySelector(".circulo");
const rectangulo = document.querySelector(".rectangulo");
```

Eventos de arrastre

```js
circulo.addEventListener("dragstart", () => console.log(1));
// Se ejecuta al toca el objeto

circulo.addEventListener("drag", () => console.log(2)); // Se ejecuta al arrastra el objeto y mantenlo

circulo.addEventListener("dragend", () => console.log(3));
//Se ejecuta al soltarlo
```

Eventos de zona

Arrastrando circulo al rectangulo.

```js
rectangulo.addEventListener("dragenter", () => console.log(1));
// Se ejecuta al entrar en el area del objeto

rectangulo.addEventListener("dragover", () => console.log(2));
// Se ejecuta al manten el objeto adentro, es infinito y por tal motivo invalida el funcionamiento 3

rectangulo.addEventListener("dragover", (e) => {
  e.preventDefault();
  console.log(2);
});
// Se detiene con el preventDefault() y permite accionar el evento drop.

rectangulo.addEventListener("drop", () => console.log(3));
// Se ejecuta si el objeto se suelta adentro

rectangulo.addEventListener("dragleave", () => console.log(4));
// Se ejecuta cuando el objeto sale de adentro
```

Transferencia de datos

**dataTransfer.**\_\_\_**;** Transferencia de datos de los objetos que interactuan entre si.

**setData( );** Asignacion de datos

```js
circulo.addEventListener("dragstart", (e) => {
  e.dataTransfer.setData("clase", "circulo");
  // Crea una asociacion entre una palabra clave y la clase de un elemento, en este caso el circulo
});
```

**getData( );** Receptor de datos

```js
rectangulo.addEventListener("drop", () => {
  e.dataTransfer.getData("clase");
  //Se le tranfiere el valor de la clase, en este caso es circulo.
});
```

### Geolocalizacion

Accede a la geolocalizacion.

```js
const geo = navigator.geolocation; // vigila la posicion
```

**getCurrentPosition( );**

```js
const geo = navigator.geolocation;

const options = {
  maximumAge: 0, //Cuanto tiempo se almacenara la ubicacion en el cache.
  timeout: 3000, //Cada cuantos milisegundos se actualizara la posicion.
  enableHightAccuracy: true, //Activa la alta precicion de localizacion
};

const err = () => console.log(e);
//Verifica cual es el error del pocicionamento

const posicion = (pos) => {
  console.log(pos);
  //Devuelve un objeto con las propiedades de la pocicion
  console.log(pos.coords);
  //Devuelve un objeto con las propiedades de coordenadas
  console.log(pos.coords.latitude);
  //Devuelve la latitud
};
geo.getCurrentPosition(posicion, err, options);
```

**watchPosition( );** Se usa para optener la pocicion en tiempo real.

### Historial

**objeto history.**\_**;** Propiedad para moverse entre el historial de navegacion.

**back( );** Regresa a la visita anterior.

```js
history.back();
```

**forward( );** Avanza a la visita siguiente. (una vez ya retrocedido en el historial).

```js
history.forward();
```

**length;** Cuenta la cantidad de secciones de historial.

```js
history.length;
```

**go( );** Recarga la pagina y puede avanzar o regresar en los sitios del historial.

```js
history.go(); //Recarga la pagina
history.go(1); //Avanza a la pagina siguiente
history.go(-1); //Retrocede a la pagina anterior
```

**pushState();** Se crean entradas en el historial.

```js
history.pushState(
  { nombre: "pedro" },
  "titulo",
  "?agregadoEnLaParteFinalDeLaURL"
);
history.pushState(
  { nombre: "pedro2" },
  "titulo",
  "?agregadoEnLaParteFinalDeLaURL2"
);
history.pushState(
  { nombre: "pedro3" },
  "titulo",
  "?agregadoEnLaParteFinalDeLaURL3"
);

//En la URL: https://pagina.com.mx/?agregadoEnLaParteFinalDeLaURL$
```

Con el evento popstate:

```js
addEventListener("popstate", (e) => {
  //detecta cada cambio de estado del historial
  console.log(e.state); //muestra los datos correspondientes a cada entrada del historial.
  //si esta en la entrada 2 devielve {nombre:"pedro2"}
});
```

**remplaceState();** Se actualiza el estado del historial.

```js
history.remplaceState(
  { nombre: "pedro" },
  "titulo",
  "?agregadoEnLaParteFinalDeLaURL"
);
history.remplaceState(
  { nombre: "pedro2" },
  "titulo",
  "?agregadoEnLaParteFinalDeLaURL2"
);
history.remplaceState(
  { nombre: "pedro3" },
  "titulo",
  "?agregadoEnLaParteFinalDeLaURL3"
);

//En la URL: https://pagina.com.mx/?agregadoEnLaParteFinalDeLaURL3
//Se queda con la ultima entrada del historial
```

### FileReader

new FileReader( ); Funciona con eventos.

```html
<input type="file" name="abrir" id="archivo" multiple />
<!-- El multiple es para permitir la seleccion de muchos archivos -->
```

```js
const reader = new FileReader();
```

readAsText( ); Lectura de texto de archivos

```js
const archivo = document.getElementById("archivo");
archivo.addEventListener("change", () => {
  //Percibe cualquier cambio
  leerArchivo(archivo.files[0]); //La funcion introduce como parametro el primer archivo seleccionado
});

const leerArchivo = (ar) => {
  const reader = new FileReader();
  reader.readAsText(ar); //Muestra el contenido en texto
  reader.addEventListener("load", (e) => {
    console.log(JSON.parse(e.currentTarget.result));
    //Abre en consola el contenido transformado
  });
};
```

Para multiples archivos

```js
const archivo = document.getElementById("archivo");
archivo.addEventListener("change", () => {
  //Percibe cualquier cambio
  leerArchivo(archivo.files); //La funcion introduce como parametro la seleccion de los archivos como un array
});

const leerArchivo = (ar) => {
  for (let i = 0; i < ar.length; i++) {
    const reader = new FileReader();
    reader.readAsText(ar[i]);
    //Muestra el contenido en texto por cada archivo
    reader.addEventListener("load", (e) => {
      console.log(JSON.parse(e.currentTarget.result));
      //Abre en consola el contenido transformado
    });
  }
};
```

readAsDataUrl( ); Lectura de imagenes o videos.

```js
const divRes = document.querySelector(".resultado");
const archivo = document.getElementById("archivo");

archivo.addEventListener("change", () => {
  leerArchivo(archivo.files);
});

const leerArchivo = (ar) => {
  var fragmento = createDocumentFragment();
  for (let i = 0; i < ar.length; i++) {
    const reader = new FileReader();
    reader.readAsDataURL(ar[i]);
    //Muestra el URL de los archivos multimedia
    reader.addEventListener("load", (e) => {
      let newImg = `<img src="${e.currentTarget.result}">`;
      //La ubicacion que optiene la introduce en una etiqueta img
      fragmento.appendChild(newImg);
      //Las imagenes nuevas son almacenadas
    });
  }
  divRes.appendChild(fragmento);
  //Las imagenes se envian al contenedor
};
```

### IndexedDB

```js
const IDBRequest = indexedDB.open("database", 1);
//Solicita la base de datos (nombre, vercion)

IDBRequest.addEventListener("upgradeneeded", () => {
  const db = IDBRequest.result; //De la solicitud se crea la base de datos a partir del result
  db.createObjectStore("nombres", {
    //Creacion de coleccion o tabla
    autoIncrement: true, //ID
  });
}); //Verifica si no esta creada y tenga que crearse la solicitud desde 0

IDBRequest.addEventListener("success", () => {
  console.log("La solicitud fue exitosa");
}); //Cuando la solicitud este echa, lo detecta

IDBRequest.addEventListener("error", () => {
  console.log("Ocurrio un error");
}); //Si hubo un error en la solicitud, lo detecta

//Almacenar objetos

const addObjeto = (objeto) => {
  const db = IDBRequest.result; //La base de datos
  const IDBtransaction = db.transaction("nombres", "readwrite"); //o readonly para solo lectura
  const ObjectStore = IDBtransaction.objectStore("nombres");
  //Se ejecutara en la tabla nombres
  ObjectStore.add(objeto); //El objeto se añade a la tabla
  IDBRequest.addEventListener("complete", () => {
    console.log("objeto agregado");
  }); //Se ejecuta cuando el objeto ya es almacenado
};

//Leer objetos

const readObjeto = () => {
  const db = IDBRequest.result; //La base de datos
  const IDBtransaction = db.transaction("nombres", "readonly");
  const ObjectStore = IDBtransaction.objectStore("nombres");
  const cursor = ObjectStore.openCursor();
  IDBRequest.addEventListener("complete", () => {
    if (cursor.result) {
      console.log(cursor.result.value);
      cursor.result.continue();
    } else console.log("Todos los datos fueron leidos"); //El else se ejecutara,(solo con cursores)
  }); //Se ejecuta cuando el objeto ya es almacenado
};

//Modificar el objeto

const modifyObjeto = (key, objeto) => {
  const db = IDBRequest.result; //La base de datos
  const IDBtransaction = db.transaction("nombres", "readwrite"); //o readonly para solo lectura
  const ObjectStore = IDBtransaction.objectStore("nombres");
  //Se ejecutara en la tabla nombres
  ObjectStore.put(objeto, key); //El objeto cambia
  IDBRequest.addEventListener("complete", () => {
    console.log("objeto Modificado");
  }); //Se ejecuta cuando el objeto ya esta editado
};

//Eliminar el objeto

const deleteObjeto = (key) => {
  const db = IDBRequest.result; //La base de datos
  const IDBtransaction = db.transaction("nombres", "readwrite"); //o readonly para solo lectura
  const ObjectStore = IDBtransaction.objectStore("nombres");
  //Se ejecutara en la tabla nombres
  ObjectStore.delete(key); //El objeto cambia
  IDBRequest.addEventListener("complete", () => {
    console.log("objeto Eliminado");
  }); //Se ejecuta cuando el objeto ya esta Eliminado
};

//Ejecucion de funciones
//Buscar en aplicaciones, en index db
addObjeto({ nombre: "Juan" });
addObjeto({ nombre: "Carlos" });
modifyObjeto(2, { nombre: "Cuevas" });
deleteObjeto(2);
```

### Matchmedia

Un objeto que devuelve 2 valores, true si respeta las dimenciones del mql y false si no.

```js
const mql = matchMedia("(max-width: 500px)");
console.log(mql.matches); //devuelve true o false

mql.addEventListener("change", () => {
  console.log("La resolucion fue cambiada");
});
```

en html:

```html
<div class="caja">area</div>
```

en js:

```js
const caja = document.querySelector(".caja");
const mql = matchMedia("(max-width: 500px)");

mql.addEventListener("change", () => {
  if (mql.matches) caja.classList.remplace("caja", "responsive-caja");
  else if (caja.className == "responsive-caja")
    caja.classList.remplace("responsive-caja", "caja");
});
```

### Intercection Observe

Esta propiedad devuelve 2 valores, true si el objeto seleccionado es perceptible y false si no es asi.

```js
const caja3 = document.querySelector(".caja3");

const verifyVisibility = (entradas) => {
  //Verificar visibilidad
  const entrada = entradas[0];
  console.log(entrada.isIntersecting); //Propiedades de entrada, si es intersectada devuelve true, si no false
};
const observar = new IntersectionObserver(verifyVisibility);

observar.observe(caja3); //objeto en observacion
```

Intersectar varias cajas al mismo tiempo

```js
const cajas = document.querySelectorAll(".caja");

const verifyVisibility = (entradas) => {
  for (const entrada of entradas) {
    if (entrada.isIntersecting)
      console.log("Se esta mostrando la: ", entrada.target.textContent);
  }
};
const observar = new IntersectionObserver(verifyVisibility);

for (caja of cajas) {
  observar.observe(caja);
  //Recorrera todas las cajas
}
```

VisibilityChange

```js
addEventListener("visibilitychange", (e) => {
  console.log(e.target.visibilityState);
  //Devuelve hidden cuando cambian a otra pestaña
  //Devuelve visible cuando la pestaña de la pagina esta activa
});
```

### Notificaciones

Notificaciones

```js
if (!("notification" in window)) {
  console.log("las notificaciones no estan disponibles");
}
Notification.requesPermission(() => {
  //pide permiso al usiario para mostrar notificaciones
  if (Notification.permission == "granted") {
    //si esta permitido
    new notification("notificacion en accion");
    console.log("permiso concedido");
  }
});
```

---

## Web Workers

Permite procesar dos acciones o mas a la vez.

```js
//En documento principal

document
  .querySelector(".boton")
  .addEventListener("click", () => ejecutarBucle());

const worker = new worker("Worker.js"); //Ejecuta un nuevo archivo js

const ejecutarBucle = () => {
  //Funcion infinita
  worker.postMessage();
};

// ---------Envio de informacion--------------

worker.addEventListener("message", (e) => {
  console.log(e.data); //Devuelve bien y tu?
  worker.terminate(); //Termina la cumunicacion entre el worker y el archivo original
});
const ejecutarBucle2 = () => {
  worker.postMessage("Hola, como estas");
};

//En documento worker.js van los procesos que tardan mucho tiempo

const ejecutarBucle = () => {
  //Funcion infinita
  while (true) {
    //Proceso infinito
    console.log(1);
  }
};

addEventListener("message", ejecutarBucle);

addEventListener("message", (e) => {
  console.log(e.data); //Devuelve Hola, como estas

  //----Envio de informacion---------
  postMessage("bien y tu?"); //Devuelve el mensaje
});
```

### Service workers

```js
//Archivo index
if (!navigator.serviceWorker) {
  console.log("Tu navegador no soporta service workers");
} else {
  navigator.serviceworker.register("sw.js");
  //Archivo service worker registrado

  navigator.serviceworker.ready.then((res) =>
    res.active.postMessage("Hola como estas")
  );

  navigator.serviceWorker.addEventListener("message", (e) => {
    console.log("mensaje de contestacion:");
    console.log(e.data);
    //Devuelve Bien y tu?
  });
}

//En el archivo sw.js
Let version="version1";
self.addEventListener("install", (e) => {
  console.log("instalado service worker");
  caches.open(version).then(cache=>{ 
      //abrir documentos utilizando el cache
      //Modo offline tambien funciona
      cache.add("index.html").then(res=>{
          console.log("La informacion se ha almacenado en el cache");
      }).catch(e=>{
          console.log(e);
      })
  })
}); // solo se instala una vez

self.addEventListener("activate", () => {
  console.log("el servicio esta activado");
  caches.keys().then(key=>{
      return Promise.all(
          key.map(cache=>{
              if(cache !== version){
                console.log("Almaceno la nueva actualizacion y elimino la antigua del cache");
                return caches.delete(cache);
            }
          })
      )
  })
}); //Nos aseguramos de que ya este activado

self.addEventListener("error", () => {
  console.log("el servicio dio un error");
}); //Escucha cualquier error que se presente

self.addEventListener("fetch", (e) => {
  console.log("interceptando peticion");
  e.respondWith(async function()=>{
      const respuestaEnCache= await caches.match(e.request);
      //utiliza las propiedades del documento para abrirlo desde cache
      if (respuestaEnCache) return respuestaEnCache;
      return e.request; //Si el documento existe en cache, lo inicializa, si no, lo ignora y espera una coneccion a internet para cargar
  });
});

self.addEventListener("message", (e) => {
  console.log("Se recibio el mensaje:");
  console.log(e.data);
  //Devuelve Hola como estas
  e.source.postMessage("Bien y tu?"); //Contestacion
});
```

---

## Objeto navigator

```js
navigator.appCodeName; //nombre del navegador

navigator.appName; //nombre oficial del navegador

navigator.appVersion; //vercion del navegador

navigator.connection; //calidad de coneccion del navegador

navigator.geolocation; //La localizacion donde se encuentra el equipo donde se abre el navegador

navigator.hardwareConcurrency; //Nos da la cantidad de nucleos del procesador logico que hay disponibles

navigator.language; //idioma del navegador

navigator.languages; //los idiomas que el navegador cree que va a entender el usuario

navigator.mimeTypes; //encabezados del navegador

navigator.onLine; //Si detecta conexion online

navigator.userAgent; //informacion del navegador

navigator.cookieEnable; //tiene las cookie activadas

navigator.permissions; //acceder a los permisos del navegador

navigator.platform; //La plataforma del navegador

navigator.plugins; //pligins del navegador y cantidad

navigator.product; //para problemas de compatibilidad, devuelve Gecko en cada navegador

navigator.serviceWorker; //devuelve el servicio worker
```

---

## Memoria

### Memorisacion

```js
let cache = [];
const memorizacion = (funcion) => {
  return (e) => {
    console.log(`valor de e: ${e}`); // es el valor de 9000
    const index = e.toString();
    if (cache[index] == undefined) cache[index] = funcion(e);
    //El valor de 9000 se itroduce como parametro y al realizar la funcion se iguala a cache[index]
    return cache[index]; //Devuelve el valor memorizado
  };
};

const multiplicacion = (repeticion) => {
  const a = 10;
  let b = 0;
  for (let i = repeticion - 1; i >= 0; i--) {
    for (let j = i - 1; j >= 0; j--) {
      b += a * a;
    }
  }
  return b;
};

//Procesos sin memorizacion (los tres tardan igual)
const date = new Date(); //Devuelve una fecha actual
multiplicacion(9000);
console.log(new Date() - date); //Se asigna una nueva fecha y se resta la anterior
const date2 = new Date();
multiplicacion(9000);
console.log(new Date() - date2);
const date3 = new Date();
multiplicacion(9000);
console.log(new Date() - date3);

//Procesos sin memorizacion (El primero es el unico que tarda)
const memo = memorizacion(multiplicacion);
const date4 = new Date(); //Devuelve una fecha actual
memo(9000);
console.log(new Date() - date4); //Se asigna una nueva fecha y se resta la anterior
const date5 = new Date();
memo(9000);
console.log(new Date() - date5);
const date6 = new Date();
memo(9000);
console.log(new Date() - date6);
```

### Memoria Cache

caches._______;

```js
caches.open("archivos web").then(cache=>{
    // crea un cache en cache Storage y despiega sus propiedades
    console.log(cache);

    cache.add("index.html"); //agrega el index.html
    cache.addAll(["index.html","estilo.css","codigo.js"]);// agrega varios archivos

    cache.match("index.html").then(res=>{ console.log(res)});//Devuelve la promesa y nos muestra las propiedades del documento seleccionado
    cache.matchAll("index.html").then(res=>{ console.log(res)});//Devuelve la promesa y nos muestra las propiedades de los documentos que coincidan con el nombre del archivo.

    fetch("index.html").then(res=>{
        cache.put("index.html",res);// modificacion del archivo, preferible usar add
    })

    cache.delete("archivo.html"); //elimina el archivo

    cache.keys().then(res=>{
        console.log(res);
    }); //Devielve toda la data del cache
}
```

## Cookies
```js
let cookies=document.cookie;
document.cookie="user=Jose";//Valor de una cookie

const newFechaUTC=dias=>{
    let fecha=new Date();
    fecha.setTime(fecha.getTime()   + dias * 1000seg * 60min * 60hora * 24dia);
    //Cumbierte la fecha de ms a s
    return fecha.toUTCString();//Formato de fecha
}
const crearCookies= (name,dias)=>{
    expires=newFechaUTC(dias);
    document.cookie=`${name};expires=${exp}`;
}//expires fecha de caducidad de la cookie

crearCookies("user=Jose","4");

const optenerCookie = cookieName =>{
    let cookies = document.cookie;
    cookies = cookies.split(";"); //split separa los resultados en array por el simbolo ;
    for(i=0; cookies.length>i; i++){
        let cookie = cookies[i].trim();//Elimina los espaciados de la cadena string
        if(cookie.startsWith(cookieName)){
            return cookie.split("=")[1]//Separa despues del simbolo igual
        }
    }
    return "no hay cookies con ese nombre";
}

obtenerCookie("nombreCookie");


//Modificar cookie
document.cookie="nombreDeCookie=nuevoValorDeCookie";
```


## Screen
### screen._________;
**width;** Ancho total de la pantalla.

**height;** Altura total de la pantalla.

**availwidth;** Ancho disponible de la pantalla.

**availheight;** Alto disponible de la pantalla.

**pixelDepth;** Resolucion de color de la pantalla.

**colorDepth;** Profundidad de bits de la pantalla.

## Canvas
```html
<canvas id="canvas" width="500px" height="500px"></canvas>
```
En javaScript
```js
const canvas= document.getElementById('canvas');

const dif=canvas.getBoundingClientRect();
//Analisa el espacio de diferencia entre la pocicion y los bordes del canvas

canvas.addEventListener('mousedown',(e)=>{
    let difX = e.clientX - dif.left;
    let difY = e.clientY - dif.Top;
    //Calculamos la diferencia entre la flecha del mause y los bordes del canvas.
})

const ctx=canvas.getContext("2d");//Perspectiva, tambien hay para 3D

ctx.lineWidth="4"; //Determina el grosor de linea de las figuras con solo bordes

ctx.strokeStyle="#48e"; //Colocar al inicio o antes que la creacion de la figura, En este caso el rectangulo con solo bordes. Cambia de color el borde

ctx.strokeRect(50,0,400,200); //Crea un rectangulo solo con bordes y como parametros recibe la pocicion en cada lado con respecto al canvas principal

ctx.fillStyle="#26a"; //Colocar al inicio o antes que la creacion de la figura, En este caso el rectangulo con relleno. Cambia de color el area

ctx.fillRect(10,20,400,200);//Crea un rectangulo pero con relleno, tambien recibe parametros de pocicion.

ctx.lineTo(100,300); //Crea puntos de interceccion y con stroke() une los puntos con linea, estos tienen que ser sucecivos. Los parametros son coordenadas.

ctx.stroke(); //Dibuja la linea uniendo los puntos anteriores, Su pocicion importa ya que este debe ir siempre al final.

ctx.closePath(); //Cierra el siclo de union de lineas, evitando que los proximos puntos intervengan con las lineas ya terminadas

ctx.beginPath(); //Abre un nuevo siclo de puntos independientes

ctx.arc(120,120,100,10,40); //Crea un circulo
```