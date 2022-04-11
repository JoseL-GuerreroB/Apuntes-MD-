# CSS

---

## Sintaxis Basica

```css
h1,
.class,
#id {
  box-sizing: border-box;
  display: block;
  position: fixed;
}
```
Añadir a tus proyectos documento normalize.css para corregir todos los errores posibles en navegadores. descargar usando en la terminal:

**npm i normalize.css** solo si tienes node.JS, si no puedes descargarlo desde internet buscandolo por el nombre del documento.

---
## Conocimientos basicos


### Selectores

- Universal: **\*{ }**
- Etiqueta: **h1, p{ }**
- Clase: **.name{ }**
- ID: **#name{ }**
- Atributo **[atributoname="valor"]{ }**
- Decendiente **h2 #id .class{ }**, padre hijo hijo{ }
- Pseudoclase .class **:hover{ }**
- Pseudoelementos #id **::before{ }**

### Especifidad

1. **!important**
2. estilos en linea: atributo **style=""** desde el HTML
3. ID
4. clases, pseudoclases y atributos
5. elementos o pseudoelementos

### Metodologia BEM

En html

```html
<header class="header header--active">
  <!--A la etiqueta padre se le da la clase de su etiqueta, tambien pueden añadirse estados colocando la misma clase y "--funcion"-->
  <h1 class="header__h1">Titulo principal</h1>
  <p class="header__p header__p--active">
    Lorem ipsum dolor sit amet consectetur,
    <span class="header__p__span">adipisicing elit </span>
    . Tenetur, debitis.
  </p>
  <!-- Los hijos adquieren la clase de su padre junto con la de ellos -->
</header>
```

En CSS

```css
.header {
  color: white;
  background-color: #555;
}
.header--active {
  /* Clase perteneciente a un evento*/
  color: black;
  background-color: #94f;
}
.header__p {
  width: 500px;
  display: none;
}
.header__p--active {
  /* Clase perteneciente a un evento*/
  width: 500px;
  display: block;
}
```

### Unidades de medida


**Fijas**
```css
.class{
    width: 100mm;
    font-size: 40px;
    height: 1cm;
}
```
* **px:** Medida en pixeles
* **cm:** Medida en centimetros
* **mm:** Medida en milimetros

**Relativas**
```css
html{
    font-size: 16px;
}
body{
    width: 1vw;
    height: 2vh;
}
#padre{
    font-size: 18px;
    width: 700px;
}
#hijo{
    width: 75%;/*El 75% de 700px, su maxima capacidad*/
    font-size: 2em;/*2em = 2 X 18px = 36px*/
    padding: 3rem; /*3rem = 3 X 16px = 48px*/
}
```
* **em:** 1em= font-size del contenedor padre
* **rem:** 1rem= font-size de la etiqueta raíz "HTML"
* **%:** medida en porcentaje correspondiente a su maxima capacidad
* **vw:** Su medida depende de la medida del viewport (la pantalla) horisontalmente
* **vh:** Su medida depende de la medida del viewport (la pantalla) verticalmente

### Propiedades de texto


* **font-zise:** tamaño de letra
* **font-family:** tipo de letra predeterminado, o puede ser optenido desde google fonts
* **line-height:** tamaño de letra, si aumenta el valor toma los valores escala del
valor inicial de la misma letra. El contenedor cambia, no la letra
* **font-weight:** grosor de la letra

### Propiedades de caja

**Display**

**display:_______**
* **block;** Estado de bloque abarca todo el ancho obligando que el contenido sobrante se despliegue hacia abajo
* **inline;** Este es flexible y si su contenido no abarca todo el espacio, comparte si espacio con otros bloques horizontalmente
* **inline-block;** adapta su contenido como si tuviese d-block, sin embargo, si su espacio no abarca 1vw comparte espacio con sus cajas hermanas.

**Apariencia**

* **backgraund-color:** color de fondo de la caja
* **padding:** distancia entre el texto y la caja (bottom, top, left, right) su estrictura es padding: 2px 2px 2px 2px (top, right, bottom, left)
* **height:** alto de la caja
* **width:** ancho de la caja
* **box-sizing: content-box;** no respeta sus medidas de la caja y le suma el padding. **:border-box;** prioriza las medidas de la caja y concerba el padding comprimiendo el texto
* **text-aline:** center alinea el texto al centro
* **margin:** distancia que hay entre dos bloques
* **border-radius:** redondea los bordes de la caja
* **border:** Marca el borde de la caja grosor solid(+variantes) color
* **box-shadow:** 2px 4px 5px 0 blue (x,y,z, intencidad, color)
* **text-shadow:** x y z color,(copiar para mas intencidad)
transform: rotate(#deg) rota el bloque o objeto
* **Outline:** muestra los efectos pero no interactua con otros bloques
* **z-index:** muestra primero el objeto con mayor valor en esta propiedad
* **Overflow-x o -y:** Crea un scroll vertical o horisontalmente (auto, hidden, scroll)
* **float:** (left,right,none,inherit) direcciona un bloque

**Posicion**

**position:_______** Permite alterar la posicion de la caja con las propiedades top, left, bottom, right

* **static;** No hay movimiento, posicion predeterminada
* **relative;** Permite alterar su pocicion y conserva su pocicion intacta por otra caja estatica
* **absolute;** Permite alterar su pocicion y su pocicion depende del viewport o de un elemento padre con posicion relativa
* **fixed;** Fija su pocicion a pesar de scrollear la pantalla
* **sticky;** mescla entre fixed y relative
```css
#padre{
    position: relative;
    bottom: 500px
}**
#hijo{
    position: absolute;
    left: 15px; /*Se movera con respecto a la caja padre*/
}
.nav{
    position: fixed;
    /* El nav no desaparecera apesar de recorrer el contenido */
}
```
### Pseudo-elementos

**.class::_________{ }**

* **first-line:** Funciona en bloque, y siempre afecta la primera linea de la clase
* **first-letter:** Funciona en bloque y afecta la primera letra de la clase
* **placeholder:** Como propiedad muestra un campo para escribir y puede ser editado
* **after:** Añade contenido despues del elemento
* **before:** Añade contenido antes del elemento
* **selection:** Altera las propiedades de la seleccion (mause)

### Pseudo-clases

**.class:___________{ }**

* **hover:** si lo toca, muestra sus propiedades
* **first-child:** selecciona el primer hijo de la clase
* **last-child:** selecciona el ultimo hijo de la clase
* **nth-child(num):** selecciona el hijo con la pocicion seleccionada
* **link:** (html- a) cambia de propiedades si el sitio deseado nunca ha sido visitado
* **visited:** cambia de propiedades si el sitio ya se visito
* **active:** apretando la forma cambia sus propiedades (si es input basta con teclear)
se desactiva cuando dejas de apretar el objeto
* **focus:** Muestra sus propiedades al enfocar
* **lang():** modifica la estetica de los bloques si el contenido esta en determinado idioma

### Propiedades de imagen

* **object-fit:_______** Modifica las dimenciones de la imagen
  * **fil;** Por conocer
  * **contain;** la imagen se ajusta a su forma normal, pese a las medidas del contenedor
  * **cover;** la imagen se ajusta a las medidas del contenedor sin perder su forma normal
  * **none;** concerva la resolucion de la imagen original
  * **scale-down;** se queda con el que tenga la resolucion mas baja
* **objet-position:** resoluciones dinamicas segun la caja que lo contenga (left - right - top - buttom
px - em - % - etc.)

### Cursores

**cursor:_______**
pointer; Cursor con forma de selector

codigos para mas cursores en:
[Link para cursores](https://www.w3schools.com/cssref/tryit.asp?filename=trycss_cursor)


### Responsive design

```css
@media only screen and (max-width:800px){
  body{
    font-size: 20px;
  }
}
``` 
condicionante para cambio de resolucion con max-width o min-width


signo > para heredar propiedades a sus etiquetas hijos

---
## Flexbox


**display: flex;** 

El contenido se ajusta con respecto a las dimenciones x y de su caja.
Las cajas hijas del contenedor display flex podran adquirir las siguientes propiedades.

### Flex-flow
Usa las propiedades de flex-direction y wrap al mismo tiempo.
**flex-flow: row, wrap;**

Para usarlas individualmente
* **flex-direction:_______;** Direccion de los elementos
  * **row;** Direccion horizontal
  * **row-reverse;** Direccion horizontal inverso
  * **column;** Direccion en vertical
  * **column-reverse;** Direccion vertical inverso
* **flex-wrap: _______;** 
  * **wrap;** Ajusta las cajas en el espacio sin perder sus propiedades
  * **nowrap;** No hace nada

```css
#caja1{
    display: flex;
    flex-flow: column-reverse wrap;
}
#caja2{
    display: flex;
    flex-direction: column-reverse;
    flex-wrap: wrap;
}
/* Ambas cajas tienen las mismas propiedades */
```

### flex
**flex:_______;** Herramienta para controlar el contenido individual de las cajas hijas.
**flex: numero numero auto;** --> **flex: 1 1 auto;**

Para usarlos por separado utilizar:
* **flex-grow: numero;** La caja con esta propiedad se apropia del espacio sobrante
* **flex-shrink: numero;** La caja con esta propiedad evita que su contenido rompa sus parametros, entre mayor sea su valor, menor sera el espacio que abarcara
* **flex-basis: medida;** Da una medida predeterminada a las cajas, para mayor precicion usar auto como valor
```css
#padre{
    display: flex;
}
#hijo1{
    flex: 2 1 auto;
    order: 3;
}
#hijo2{
    flex-grow: 2;
    flex-shrink: 1;
    flex-basis: auto;
    order: 1;
}
#hijo3{
    flex: 1 1 auto;
    order: 2;
}
/* El hijo 1 y 2 tienen las mismas propiedades
Tambien abarcaran mayor espacio que el hijo 3 */
```
order: Toma la pocicion indicada segun el orden

### Alineacion

**align** : Alineacion Vertical

**align-items:_____;** Es comun usarlo cuando nuetra intencion es alinear todos los elementos hijos en una fila, sus propiedades pueden alterar su naturaleza si se altera el flex-direction.
  * **flex-start;** Alineacion arriba
  * **flex-end;** Alineacion abajo
  * **center;** Alineacion al centro
  * **stretch;** Valor por defecto, los hijos ocupan el 100% del espacio vertical disponible de su contenedor
  * **baseline;** Su punto de referencia es la hubicacion del texto del contenedor

**align-self:_____;** Se usa en las cajas hijas para darles las propiedades por individual
  * **flex-start;** Alineacion arriba
  * **flex-end;** Alineacion abajo
  * **center;** Alineacion al centro
  * **stretch;** Valor por defecto, ocupa el 100% del espacio vertical disponible de su contenedor
  * **baseline;** Su punto de referencia es la hubicacion del texto del contenedor

**align-content____;** Solo usarlo cuando tienes la propiedad **flex-wrap: wrap;** ya que tiene la capacidad de alinear varias filas en un mismo contenedor
  * **flex-start;** Alineacion arriba
  * **flex-end;** Alineacion abajo
  * **stretch;** Valor por defecto, los hijos ocupan el espacio vertical y horisontal disponibles de su contenedor
  * **center;** Alineacion al centro
  * **space-between;** El contenido se distribuye de extremo a extremo, dejando entre cada uno de los elementos un espacio
  * **space-around;** El contenido se distribuye teniendo un espacio intermedio entre los elemento y sin tocar los extremos del contenedor
  * **space-evenly;** El contendido se distribuye concerbando un espacio entre ellos, incluyendo los que estan aun lado de los extremos
```css
#padre{
    display: flex;
    align-items: center;
}
.hijos{
    width: 200px;
}
/* Alinea por linea individual */
#padre2{
    display: flex;
    flex-wrap: wrap;
    align-content: center;
}
.hijos2{
    width: 200px;
}
/* Alinea por conjunto */
#padre3{
    display: flex;
}
.hijos3:nth-child(3){
    align-self: center;
    width: 200px;
}
/* Alinea por separado */
```
**justify** : Alineacion horizontal

**justify-content:_____;** Sus propiedades pueden alterar su naturaleza si se altera el flex-direction.
  * **flex-start;** Alineacion arriba
  * **flex-end;** Alineacion abajo
  * **center;** Alineacion al centro
  * **space-between;** El contenido se distribuye de extremo a extremo, dejando entre cada uno de los elementos un espacio
  * **space-around;** El contenido se distribuye teniendo un espacio intermedio entre los elemento y sin tocar los extremos del contenedor
  * **space-evenly;** El contendido se distribuye concerbando un espacio entre ellos, incluyendo los que estan aun lado de los extremos
```css
#padre{
    display: flex;
    justify-content: center;
}
.hijos{
    width: 200px;
}
/* Alinea por linea individual */
```
---
## Grillas


**display: grid;**

Sistema de grillas para colocar las partes de la web de forma precisa, combinando recuadros para crear areas y regiones donde puedan pocicionarse los elementos de la web.


### Creacion de columnas y filas de la grilla

**grid-template: rows / columns;**

**grid-template: repeat(5,fr) / 200px 10mm 1vh;**

**grid-template-rows:_______;** Creacion del numero de filas.
* **200px 10mm 1vh;** Determina el alto que tendra cada fila
* **minmax(100px, 200px);** Asigna el alto minimo y maximo de la fila
* **min-content;** El alto de la fila dependera del espacio minimo del contenido
* **max-content;** El alto de la fila dependera del espacio maximo del contenido
* **repeat(5,300px);** Divide la grilla en el numero de columnas escogido y con las mismas dimenciones
* **auto-fill;** Aumenta el numero de columnas o filas con respecto al tamaño de ventana
* **auto-fit;** Los escala, si hay espacio los campos se hacen mas grandes

**grid-template-columns:_______;** Creacion del numero de columnas.
* **1fr;** 1 fraccion de la grilla total
* **200px 10mm 1fr;** Determina el ancho que tendra cada columna
* **minmax(500px, 600px);** Asigna el ancho minimo y maximo de la columna
* **repeat(5,fr);** Divide la grilla en el numero de columnas escogido y con las mismas dimenciones
* **auto-fill;** Aumenta el numero de columnas o filas con respecto al tamaño de ventana
* **auto-fit;** Los escala, si hay espacio los campos se hacen mas grandes
```css
#cuerpo{
    display: grid;
    grid-template-columns: repeat(5,fr) ;
    grid-template-rows: 500px minmax(200px,400px) minmax(min-content,max-content) ;
    grid-gap: 5px;
}
```
### Separacion

**grid-grap: anchoDeSeparacion;** separa las celdas establecidas

**grid-row-gap: anchoDeSeparacion;** separa las filas establecidas

**grid-column-gap: anchoDeSeparacion;** separa las columnas

### Grid item: articulo de la grilla

Los items con estas propiedades utilizan las grillas para establecer sus dimenciones.

**grid-row: start/ span end;**

**grid-column: start/ span end;**

```css
/* Hijos de la caja con display grid */
#item1{
    grid-column: 1/ span 3;
    /* ocupa las 3 primeras columnas */
    grid-row: 1;
    /* en la fila 1 */
}
#item2{
    grid-column: 4;
    /* ocupa la columna 4 */
    grid-row: 2 / span 2;
    /* en la fila 2 hasta la 3, recorre dos pociciones */
}
```
### Grid implicito

**grid-auto-columns: unicaMedida;** Crea columnas adicionales si hace falta, con el parametro correspondiente

**grid-auto-rows: unicaMedida;** Crea filas adicionales si hace falta, con el parametro correspondiente

**grid-auto-flow:_____;** El contenido se distribuye de forma acendente
* **row;** Las cajas consecutivas se distribuyen de forma horisontal
* **column;** Las cajas consecutivas se distribuyen de forma vertical
* **dense;** Las cajas se distribuyen de ambas formas con respecto al espacio donde puedan caber, ya sea de forma horizontal con **row dense;** o vertical con **column dense;**
```css
#cuerpo{
    display: grid;
    grid-auto-columns: 500px;
    grid-auto-rows: 1fr;
}
/* Crea columnas y filas automaticamente */
#cuerpo{
    display: grid;
    grid-template-columns: repeat(5,1fr);
    grid-template-rows: repeat(8,1fr);
    grid-auto-flow: dense;
}
/* Ordena los items conforme a la direccion y el espacio */
```
Control de flujo

align-content y justify content solo puedes usarla cuando el cuerpo de la grilla supera en ancho y en alto de la misma grilla.

Align-items y justify-items solo pueden usarse cuando la celda es mas grande que su contenido (ancho y alto), pociciona cada elemento de la grilla dentro de las dimenciones de las casillas de la grilla.

align-self y justify-self se coloca en los items de la grilla y se afectan de forma individual, solo puede usarse cuando la celda es mas grande que su contenido (ancho y alto).

```css
#cuerpo{
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: repeat(3,1fr);
    grid-template-rows: repeat(3,100px);
    justify-content: center;
    align-content: center;
}
.items{
    width: 50px;
    height: 50px;
}
/* Pocicionamiento global de la grilla
 entre su contenedor */

#cuerpo{
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: repeat(3,1fr);
    grid-template-rows: repeat(3,100px);
    justify-items: center;
    align-items: center;
}
.items{
    width: 50px;
    height: 50px;
}
/* Posicionamiento individual de todas las celdas */

#cuerpo{
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: repeat(3,1fr);
    grid-template-rows: repeat(3,100px);
}
.items:nth-child(4){
    width: 50px;
    height: 50px;
    justify-self: center;
    align-self: center;
}
/* Posicionamiento individual de una selda especifica */
```

### Grid area

grid-template-area: " val val val" (" " --> fila)
                    "val1 val2 val2"
                    "val1 val2 val2"
                    "val1 val3 val3";

grid-area: namearea; Se coloca en el item
```css
#cuerpo{
    display: grid;
    grid-template-areas: "nav nav nav"
                        "main main aside"
                        "main main aside"
                        "footer footer footer";
}
.items:nth-child(1){
    grid-area: nav;
}
.items:nth-child(2){
    grid-area: main;
}
.items:nth-child(3){
    grid-area: aside;
}
.items:nth-child(4){
    grid-area: footer;
}
```
---
## Efectos


### Transicion

trancition: all 2s linear .5s;
crea un efecto de trancicion
```css
#contenedor{
    height: 100%;
    width: 100%;
}
.contenidos{
    position: relative;
    left: 0;
    width: 20px;
    height: 20px;
    background-color: blue;
    transition: all 1s linear .5;
}
#contenedor:hover> .contenidos{
    left: 80%;
    color: red;
}
```
Para usarlos por separado:

**trancition-property:_____;** Propiedad a la que se le da trancicion. Necesaria
* **background;** Trancicion al background
* **top, left, bottom, right;** Trancicion de direcciones
* **color;** Color de letra;
* **margin;** Margenes, tambien puedes ser preciso incluyendo las direcciones.
* **all;** Toma todas las propiedades.
* puedes usar casi cualquier propiedad

**trancition-duration: #s;** Duracion de la trancicion. Necesaria
* Usar de .1s a 5s como preferencia

**transition-timing-function:_____;** Curvatura temporal
* **lineal;** trancicion lineal
* **ease;** de rapido a despacion
* **ease-in;** de despacio a rapido
* **ease-out;** de mucho mas rapido a mucho mas despacio
* **ease-in-out;** despacio acelera despacio
* **steps(5,end);** divide la trancicion y se detiene en cada etapa como una especie de lag
    * (5,jump-start) La primera trancicion es mas larga, desde la izquierda
    * (5,jump-end) La ultima trancicion es mas larga, desde la derecha
    * (5,jump-none) No hay tranciciones largas
    * (5,jump-both) La primera y ultima trancicion duran mas
    * (5,jump-end) La ultima trancicion es mas larga, desde la derecha
    * (5,start) Igual que jump-start
    * (5,end) Igual que jump-end
    * step-start --> steps(1, jump-start)
    * step-end --> steps(1, jump-end)
* **cubic-bezier(p1, p2, p3, p4);** tu controlas el tipo de trancicion

**trancition-delay: #s;** tiempo de espera antes del inicio del efecto
* Usar de .1s a 5s como preferencia

### Animaciones

Animacion: **@keyframes name{ from{} to{}}** (from y to puede ser cambniado por un valor en porcentaje 0% a 100%).
```css
@keyframes animacion {
    from {
    } 
    to {
    }
}
@keyframes animacion {
    0% {
    } 
    100% {
    }
}
```
Propiedades

**animation: 3s ease-in .5s 2 reverse both paused slidein;**

Propiedades por separado

**animation-duration: #s;** Duracion total de la animacion. 
* **segundos #s**

**animation-timing-function:_____;** Curvatura temporal de la animacion.
* **Las mismas que las de transition**

**animation-delay: #s;** Tiempo de espera antes de la animacion.
* **segundos #s**

**animation-iteration-count: #;** Numero de veces que se repetira la animacion.
* **numero de veces**
* **infinite;** Infinito

**animation-direction:_____;** Direccion de la animacion.
* **normal;** Conforme al estado natural de la animacion
* **reverse;** Invierte el estado natural de la animacion
* **alternate;** Ida y vuelta, solo funciona con un estado infinito
* **alternative-reverse**

**animation-fill-mode:_____;** Concerba o no las propiedades de la animacion.
* **none;** No concerba las propiedades de la animacion, ni las muestra antes de la animacion
* **forward;** Conserva las propiedades de la animacion al finalisar
* **backwards;** Muestra las propiedades al principio
* **both;** Conserva en ambos estados las propiedades de la animacion

**animation-play-state:_____;** Posobilidad  de pausar o continuar la animacion.
* **paused;** Pausa la animacion
* **runing;** Continua la animacion

**animation-name:_______;** Nombre de la animacion a utilizar.
```css
.caja{
    animation: 3s ease-in .5s 2 reverse both paused animacion;
}
.caja{
    animation-duration: 3s;
    animation-timing-function: ease-in;
    animation-delay: .5s;
    animation-iteration-count: 2;
    animation-direction: reverse;
    animation-fill-mode: both;
    animation-play-state: paused;
    animation-name: animacion;
}
```

### Efectos con cubic-bezier:

Eje Y: Progreso de animacion, El valor de Y debe tener de entre (-1-01 - 1.99).
Eje X: Tiempo total de animacion, El valor de X debe tener de entre (0 - 1).
P1: x1,y1 Parametros de inicio.
P2: x2, y2 Parametros del final.

[Link para cubic-bezier](https://cubic-bezier.com/#.05,1.77,1,-1.01)

### Transformacion
**transform:_____;** Transforma el objeto
* translateX(medidasAbsolutas);
* translateY(medidasAbsolutas);
* translate(medidaX, medidaY);
* scale(#); Escala # veces mas grande en ambas dimenciones
* scaleX(#);
* scaleY(#);
* skew(#deg); Deformacion en grados
* skewX(#deg);
* skewY(#deg);
* rotate(##deg o grad o rad o turn), ritateX o Y o Z o 3D
* Etc...
```css
.caja{
    transition: transform 5s;
}
.caja:hover{
    transform: translateX(200px);
    transform: scaleY(2);
    transform: skew(45deg);
    transform: rotateZ(45deg);
}
```
### Clip-path
(puntoX puntoY, punto2X punto2Y, ....)
[Link para clip-path](https://bennettfeely.com/clippy/)

### Background
****background-image: url(https://...);**** La imagen ocupara el backgraund.

****background-size:_____;**** ajuste de imagen.
* ****100% 300px;**** eje X y Y
* ****cover;**** Ajusta la imagen desde el centro

****background-repeat:_____;**** Repite o no la imagen en el espacio sobrante de la imagen.
* ****repeat;**** Repite la imagen
* ****no-repeat;**** No repite la imagen

****background-position:_______;**** El background tiene que ser mas grande que la imagen.
* ****top left;**** Mueve la imagen a la parte superior izquierda
* ****bottom right;**** Mueve la imagen a la parte inferior derecha
* ****Etc...****

****backgraund-attachment:**** Efecto al hacer scroll.
* ****scroll;**** predeterminado
* ****fixed;**** la imagen se queda fija

****backgraund-clip:_____;**** Muestra la imagen desde un aspecto, se recorta.
* ****border-box;**** se tiene en cuenta el borde, Valor por defecto
* ****padding-box;**** se tiene en cuenta el padding
* ****content-box;**** se tiene en cuenta el contenido

****backgraund-origin:**** origen de la foto, Se crea sobre la propiedad.
* ****border-box;**** se tiene en cuenta el borde, Valor por defecto
* ****padding-box;**** se tiene en cuenta el padding
* ****content-box;**** se tiene en cuenta el contenido

```css
#imagen{
    background-image: url(https://imagen.com);
    background-size: cover;
    background-position: right center;
    background-repeat: no-repeat;
    background-clip: content-box;
    background-attachment: fixed;
    background-origin: padding-box;
}
```
### Variable
:root{
--color-rojo: #f00;
}
```css
:root{
    --color-naranjaR: #f50;
}
.caja{
    background: var(--color-naranjaR);
}
```
### Filtros
**filter:_______;** propiedades para imagen
* **blur(px);** Desenfocar, imagen borrosa
* **brightness(2);** Brillo, se oscurece cuando el numero es inferior a 1
* **contrast(1.5);**  Contraste, uno es contraste normal, si es mayor a 1, se hace mas contraste
* **drop-shadow (10px 10px 5px #000);** Sombra intena en imagenes transparentes
* **grayscale(50%);** Escala de grises
* **hue-rotate(180deg);** Saturador de la gama de colores
* **invert(100%);** Invertir los colores, si el valor es 50% se vuelve gris
* **opacity(80%);** Opacidad de imagen
* **saturate(4);** saturacion, brinda colores mas brillante que el contraste
* **sepia (100%);** sepia
* **url("filters.avg#filter.id");**

```css
#imagen{
    filter: grayscale(50%) contrast(3);
}
```
### Extras
direccion: ltr, rtl, initial, inherit ubicacion del contenido

letter-spacing: espacio de letra

scroll-behavior: smooth, efecto de scroll relentizado

user-selected: permite o no seleccionar

text-shadow: sombra de letra

investigar selectores en pagina oficial