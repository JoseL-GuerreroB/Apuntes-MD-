# HTML

---

## Sintaxis basica

```html
<html>
  <head>
    <title>Titulo de la WEB</title>
  </head>
  <body></body>
</html>
```

---
## Dentro de la etiqueta Head


### Meta datos

```html
<meta charset="UTF-8" />
<!--Permite la escritura de acentos y otros simbolos-->

<meta http-equiv="X-UA-Compatible" content="IE=edge" />
<!--Permite compatibilidad en navegadores antiguos-->

<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<!-- Sirve para definir qué área de pantalla está disponible al renderizar un documento -->

<meta name="keyword" content="Palabras Clave" />
<!--Para el navegador, palabras para busqueda-->

<meta
  name="description"
  content="Pagina de ensayo"
/><!--Describe lo esencial de la pagina-->

<meta
  name="autor"
  content="autor de la pagina"
/><!--Datos del autor de la pagina web-->

<meta
  name="copyright"
  content="dueño de los derechos de la pagina"
/><!--Datos del dueño de los derechos de la pagina-->

<meta name="robots" content="index o noindex" />
<!--Paginas ocultas o no ocultas-->
```

### Titulo, icono y font-awesome

```html
<link rel="icon" href="icono.ico" />
<!--Coloca en el href la direccion del icono a mostrar-->

<title>Document</title
><!--Muestra el nombre de la web-->

<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.0/css/all.min.css"
  integrity="sha512-10/jx2EXwxxWqCLX/hHth/vu2KY3jCF70dCQB8TSgNjbCVAC/8vai53GfMDrO2Emgwccf2pJqxct9ehpzG+MTw=="
  crossorigin="anonymous"
  referrerpolicy="no-referrer"
/>
<!--Para aplicar iconos de font-awesome-->
```

### Conexión con archivos CSS y JS

```html
<script src="main.js"></script>
<!-- conecta con javascript, coloque de preferencia en el body -->

<link rel="stylesheet" href="/style.css" />
<!-- conectar con css -->
```

---
## Dentro de la etiqueta Body

### Encabezados

```html
<!-- h1 al h6 - sirven para escribir los 	titulos, dependiendo de su importancia se espera que sean mas o menos utilizadas -->
<h1>Encabezado</h1>
<h2>Encabezado</h2>
<h3>Encabezado</h3>
<h4>Encabezado</h4>
<h5>Encabezado</h5>
<h6>Encabezado</h6>
```

### Etiquetas de contenido

```html
<!-- lorem para generar texto -->
<p>
  Este parrafo:
  <b>Negrita</b>
  <i>Inclinada</i>
  <strike>Tachada</strike>
  <small>Pequeña</small>
</p>

<div>Caja de contenido global</div>

<a href="/link" target="_BLANK">El link</a>
<!-- "_BLANK" apartado para abrir el enlace desde otra pestaña sirve tanto para rutas locales C: o globales https// -->

<br />
<!--Funciona como un salto de linea-->

<hr />
<!--Funciona como un separador (crea una linea)-->
```

### Atributos especiales

```html
<div class="" id=""></div>
```

- Las clases son selectores que pueden asignarse a dos o mas elementos segun el nombre de la clase.
- Los ID son selectores de un unico elemento segun el nombre del id.

### Listas

```html
<ul>
  <!--Lista desordenada-->
  <li>lista</li>
  <li>lista</li>
  <li>lista</li>
</ul>

<ol>
  <!--Lista ordenada-->
  <li>lista</li>
  <li>lista</li>
  <li>lista</li>
</ol>
```

### Multimedia

```html
<img src="/direccion" alt="IMG" title="mensaje" />
```

- **src=""** En el se coloca la direccion de la imagen.
- **alt=""** remplaza el contenido erroneo por un mensaje.
- **title=""** Le da un titulo a la imagen

```html
<video src="/direccion" autoplay controls></video>
```

- **src=""** En el se coloca la ubicacion del video.
- **autoplay** Es para que se reprodusca el video una vez este listo.
- **controls** Permite al usuario acceder a los atributos del video.

```html
<audio src="/direccion" autoplay controls></audio>
```

- **src=""** En el se coloca la ubicacion del audio.
- **autoplay** Es para que se reprodusca el audio una vez este listo.
- **controls** Permite al usuario acceder a los atributos del audio.

### Formularios

```html
<form action=""></form>
```

- **action="Post"** Envia los datos de forma segura
- **action="Get"** Envia los datos por la URL

### Input

Etiqueta para la entrada de datos

```html
<input type="color" name="" required value="" />
```

- **type=""** Se introduce el tipo de input
  - **Text** Escritura de texto generico
  - **password** Especial para contraseñas
  - **number** Escritura solo numeros
  - **email** Valida correos electronicos
  - **color** Escala de colores
  - **range** Establece un rango, usar atributo:
    - **min=""** Para el minimo valor
    - **max=""** Para el maximo valor
  - **date** Fecha
  - **time** Hora
  - **button** Forma de boton
  - **submit** Envio de datos del formulario
- **name=""** Le da un nombre al input
- **required** Sirve para establecer un campo requerido
- **value=""** Sirve para asignar un valor por defecto

### Textarea

Etiqueta para area de texto, tambien funciona como input.

```html
<textarea name="" cols="30" rows="10" readonly></textarea>
<!--readonly evita que se pueda interactuar con el text area y solo permite lectura-->
```

### Etiquetas semanticas

```html
<html>
  <head>
    <title>Titulo de la WEB</title>
  </head>

  <body>
    <header>
      <nav>
        <ul>
          <li>Opcion 1</li>
          <li>Opcion 2</li>
          <li>Opcion 3</li>
        </ul>
      </nav>
      <hgroup>
        <h1>Titulo</h1>
        <h2>Eslogan</h2>
      </hgroup>
    </header>

    <main>
      Contenido Principal
      <article>
        <header>Encabezado del articulo</header>
        <section>
			Lorem ipsum dolor sit amet consectetur
		</section>
        <section>
			Lorem ipsum dolor sit amet consectetur
		</section>
        <section>
			Lorem ipsum dolor sit amet consectetur
		</section>
        <footer>pie del articulo</footer>
      </article>
      <article>...</article>
      <article>...</article>
    </main>
    <aside>
      Lorem ipsum dolor, sit amet consectetur
      adipisicing elit. Nisi, a?
    </aside>
    <footer>Pie de pagina</footer>
  </body>
</html>
```

**main** contiene el contenido principal de la pagina
**aside** es para contenido adicional

**hgroup** funciona para agrupar varios encabezados

Un articulo puede tener encabezado y pie; tambien puede tener muchas secciones.


### Tablas

Estructura de tabla

```html
<table>
  <caption>
    Pie de tabla
  </caption>
  <thead>
    <!--Encabezado de tabla-->
    <tr>
      <!--Define el row-->
      <th>Columna</th>
      <!--Encabezado por columna-->
      <th>Columna</th>
      <th>Columna</th>
      <th>Columna</th>
    </tr>
  </thead>
  <tbody>
    <!--Contenido de tabla-->
    <tr>
      <td>Contenido</td>
      <!--Contenido por grilla-->
      <td>Contenido</td>
      <td>Contenido</td>
      <td>Contenido</td>
    </tr>
  </tbody>
  <tfoot>
    <!--pie de tabla-->
    <tr>
      <th>Columna</th>
      <!--pie por columna-->
      <th>Columna</th>
      <th>Columna</th>
      <th>Columna</th>
    </tr>
  </tfoot>
</table>
```
---
