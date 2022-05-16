# NodeJS y ExpressJS

---

## Descripción y uso

Node.js nos da la posibilidad de usar JavaScript para construir el lado del servidor de la web ya que es un entorno de ejecucion y Express.js es el framework que potencia este lenguaje, del lado del servidor.

### Instalación

Node.js se instala desde su [pagina oficial](https://nodejs.org/es/) y express.js se descarga utilizando NPM (node package manager), este sistema de gestion de paquetes se instala junto con node.

```
npm install express
npm i express
```

### Ejecución

En archivo **index.js**

```js
console.log("Hola, Buscame en la terminal");
console.log(5 + 2);
```

En la **Terminal (CMD)** desde la carpeta donde almacenaste el archivo **index.js**.

```js
node index.js //node nombreDelArchivo.js
```

Muestra en la CMD

- Hola, Buscame en la terminal
- 7

### Exportación (1 Modulo)

En archivo secundario.js

```js
const Animales = ["conejo", "cangrejo", "gato", "perro"];
module.exports = Animales; //se hace la exportacion
//tambien puedes exportar funciones y clases, etc
```

En index.js

```js
const Animales = require("./secundario.js");
//Se hace la importacion del archivo secundario

Animales.forEach((animal) => {
  console.log(animal);
});
```

En la CMD

```js
node index.js
```

Muestra en la CMD

- conejo
- cangrejo
- gato
- perro

### Exportación (+2 Modulos)

En archivo secundario.js

```js
const Animales = ["conejo", "cangrejo"];
const Mascotas = ["perro", "gato"];
module.exports = {
  Animales: Animales,
  Mascotas, //Cuando la clave y el valor son iguales se puede usar esta exprecion
};
```

En index.js

```js
const { Animales, Mascotas } = require("./secundario");
//En archivos js se puede omitir el .js

Animales.forEach((animal) => {
  console.log(animal);
});
Mascotas.forEach((mascota) => {
  console.log(mascota);
});
```

En la CMD

```js
node index.js
```

Muestra en la CMD

- conejo
- cangrejo
- gato
- perro

### Bases para usar Node

**NPM** es el sistema de gestion de paquetes de node y se utiliza para instalar modulos externos de node, tambien es utilizado para generar archivos importantes y ejecutar algunos comandos integrados en el documento "**package.json**".

Crear documento "**package.json**"

```js
npm init --y
```

Se generara un documento con la mayoria de las caracteristicas de tu aplicacion (**package.json**) y almacena los modulos requeridos para el buen funcionamiento de tu aplicacion (dependencies).

### Modulos Internos

Son los modulos integrados en el mismo node, pueden usarse importandolos en el index.js o en cualquier archivo donde los necesiten.

Sintaxis: const modulo = require('nomModulo);

```js
const OS = require("os"); //para sistema operativo
os.platform(); //en que plataforma nos encontramos windown, linux etc
os.release(); //muestra la ultima vercion de la plataforma en la que me encuentro
os.freemem(); //muestra la cantidad de bits libres de la memoria
os.totalmem(); //muestra la cantidad de bits de la memoria

const fs = require("fs"); //crea archivos del sistema operativo
fs.writeFile("./texto.txt", "linea uno", function (err) {
  //crea archivo, con texto, y una funcion de ejecucion.
  if (err) {
    console.log(err);
  }
  console.log("archivo creado");
});

fs.readFile("./text.txt", function (err, data) {
  //Lee el contenido del documento
  if (err) {
    console.log(err);
  }
  console.log(data);
  console.log(data.toString());
});
```

### Modulos Externos

Son modulos que no estan integrados a node, pero pueden instalarse con npm.

```js
npm i nomModulo //Express.js es un modulo externo
npm i nomModulo@2.19.2 //con vercion
npm i express //ejemplo con vercion actual implicita
```

> Los modulos instalados se almacenan en la carpeta **node_modules**. No alterar el contenido de esta carpeta.

Una vez instalado se añade al package.json como una dependencia.

```json
"dependencies": {
    "express": "^4.18.1" //Vercion
  }
```

Control de verciones por parches "1"

```json
"dependencies": {
    "express": "~4.18.1" //Actualiza 4.18.++1
  } // ~ --> Alt + 126
```

Control de verciones por arreglos "18"

```json
"dependencies": {
    "express": "^4.18.1" //Actualiza 4.++18.1
  } // ^ --> Alt + 94
```

Control de verciones por vercion "4"

```json
"dependencies": {
    "express": "*4.18.1" //Actualiza ++4.18.1
  }
```

> **package-lock.json:**
> Se crea cuando se instala un modulo externo y contiene las verciones de los modulos incorporados.

Actualizar modulos externos

```js
npm update nomModulo
```

Desinstalar modulos externos

```js
npm uninstall nomModulo
```

---

## Dependencias

Almacena el nombre de los Modulos externos instalados junto con sus verciones correspondientes en formato JSON.

```
npm list
```

> Muestra en la consola todas las dependencias de un proyecto

### Dependencias globales

Modulos externos instalados de forma global en el almacenamiento de la computadora.

Instalar, Actualizar y Desinstalar

```
npm i -g nomModulo
npm update -g nomModulo
npm uninstall -g nomModulo
```

> Solo descargar de forma global cuando sean modulos frecuentemente necesitados

```
npm list -g
```

> Muestra en consola las dependencias globales

### Dependencias de desarrollador

Modulos externos instalados con el fin de apoyar unicamente el desarrollo de una aplicacion y no interactua con el funcionamiento del la aplicacion.

Instalar, Actualizar y Desinstalar

```
npm i -D nomModulo
npm update -D nomModulo
npm uninstall -D nomModulo
```

> Solo descargar modulos de esta forma cuando estos no sean necesarios para el funcionamiento de la aplicacion

Se almacenan en el package.json como devDependencies

```json
"devDependencies": {
    "nodemon": "^2.0.15"
  }
```

### NPX

Descarga modulos externos de forma local y en su ultima vercion, almacenando su contenido en la carpeta node_modules. (Es más rapido).

```json
npx i nomModulo
```

---

## Scripts

En el se ejecutan acciones importantes del proyecto.

```json
"scripts": {

  }
```

### Nodemon

Es un modulo que detecta los cambios en el proyecto y actualiza la ejecucion posteriormente.

```
node src/index.js
```

> Esto se tiene que ejecutar en la CMD cada vez que hay una modificacion en nuestro proyecoto

Con nodemon

Una vez instalado, se tendra que modificar el script del documento package.json.

```json
"scripts": {
    "dev": "nodemon src/index.js"
  }
```

En CMD

```
npm run dev
```

> Se ejecuta el script y activa la funcionalidad del modulo.

---

## Creación de servidor HTTP

Permite la transferencia de informacion entre el cliente y el servidor.

## Con node.js

```js
const http = require("http"); //crea un servidor web

http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-type": "text/html" }); //codigos de estados 200, estados del navegador
    //tipo de contenido. abrir en ispeccionar Network.
    res.write("<h1>Hola mundo</h1>"); // muestra en el servidor
    res.end(); //termina el proceso
  })
  .listen(3000, function () {
    //Puerto de ejecucion del servidor
    console.log("Servidor en el puerto 3000");
  });
```

## Con express.js

```js
//Requerimientos
const express = require('express');//importacion express
const app = express();//App adquiere las propiedades de express
const port = 5000; //Puerto


// Rutas
app.get('/',(req,res)=>{
  //('/' --> adicion de ruta, (requiere, responde))
  res.send('Hola mundo desde http://localhost:5000/');//mensaje
});
app.get('/ruta2',(req,res)=>{
  res.send('Hola mundo desde http://localhost:5000/ruta2');//mensaje
})

//Escucha del servidor en el puerto
app.listen(port, ()=>{ //escuchando servidor
  console.log('Servidor conectado en el puerto: ' port);
});
```

---

## Middlewares

Ofrece servicios y funciones comunes para las aplicaciones. Intercepta la peticion antes de la respuesta.

### Lectura de datos externos

```js
app.use(express.text()); //Datos con tipo de cadena String
app.use(express.raw());
```

Desde un formulario html

```js
app.use(express.urlencoded({ extended: true }));
```

Desde una peticion fetch o axios

```js
app.use(express.json()); //Datos de tipo JSON
```

### Archivos estaticos

Para Cambiar los mensajes de respuesta del servidor por archivos html con sus respectivos archivos css y js, se crea una carpeta public y en ella se crean los documentos html junto con sus carpetas de estilos y scripts.

En index.js

```js
app.use(express.static(__dirname + "/public"));
//Archivo htmlprincipal del front end
//app.use(express.static('public/archivo.html'));
```

**Enviar datos por Metodo GET**

> No recomendable para informacion importante como lo son los datos personales y contraseñas, ya que estas pueden ser encontradas en la URL (los datos se envian por este medio).

En public/index.html

```html
<form action="http://localhost:5000/formulario" method="get">
  <input type="text" placeholder="Nombre" name="nombre" />
  <input type="text" placeholder="Recomendacion" name="comentario" />
  <input type="submit" value="Enviar" />
</form>
```

En /index.js

```js
app.get("/formulario", (req, res) => {
  console.log(req.query);
  //Devuelve en la CMD un objeto con los datos {nombre:"Juan", comentario: "buen Curso"}

  res.send(`Gracias por tu comentario ${req.query.nombre}`);
  //En http://localhost:5000/formulario se envia Gracias por tu comentario Juan
});
```

**Enviar datos por metodo POST**

En public/index.html

```html
<form action="http://localhost:5000/formulario" method="post">
  <input type="text" placeholder="Nombre" name="nombre" />
  <input type="password" placeholder="Contraseña" name="comentario" />
  <input type="submit" value="Enviar" />
</form>
```

En /index.js

```js
app.use(express.urlencoded({ extended: true }));
//Necesario para leer el objeto en la consola

app.post("/formulario", (req, res) => {
  console.log(req.body);
  //Devuelve en la CMD un objeto con los datos {nombre:"Juan", contraseña: "miContraseÑA"}

  res.send(`Bienvenido ${req.body.nombre}`);
  //En http://localhost:5000/formulario se envia Bienvenido Juan
});
```

### Archivos dinamicos

Permiten crear sitios web dinamicos, entre ellos estan las plantillas de EJS, PUG y Handlebars.

En el caso de Handlebars (Hbs)

Se crea una carpeta **views** y en ella se crean el achivo principal **home.hbs**(entre otros archivos hbs) y una carpeta **layouts**, en la carpeta layouts se crean la estructura basica de los hbs.

Hbs en nodemon

Nodemon no actualiza los archivos de plantillas. Para permitirlo, se crea un archivo nodemon.js y en el se hace la modificacion incluyendo la plantilla que necesitas o utilizas.

```json
{
  "ext": "js,json,hbs" //En este caso inclui hbs
}
```

Importación

```js
const { create } = require("express-handlebars");
```

Modificaciones

```js
const hbs = create({ //configuracion de extencion HBS
  extname: ".hbs";
});

app.engine(".hbs",hbs.engine); //asigna motor de plantilla
app.set("view engine",".hbs"); //asigna la extencion hbs
app.set("views", "./views"); //estara dentro de la carpeta views
```

**Ruta principal**

En layouts/main.hbs

```hbs
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="index.css" />
    <title>Estructura principal del proyecto</title>
  </head>
  <body>
    {{{body}}}
    <!-- Adquiere el cuerpo del documento direccionado, en este caso, el home.hbs -->
  </body>
  <script src="/index.js"></script>
</html>
```

En home.hbs

```html
<h1>Contenido principal</h1>
<!-- Los otros documentos como este carecen de la estructura basica html -->
```

En index.js

```js
app.get("/", (req, res) => {
  res.render("home"); //home.hbs
});
//En http://localhost:5000/  Aparece <h1>Contenido principal</h1> junto con el cuerpo proporcionado por el main.hbs
```

**Componentes**

Se crea la carpeta **components** y en ella los documentos componentes, en este caso sera un navBar.

En component/navBar.hbs

```hbs
<nav>
  <img src="/logo" alt="img" />
  <ul>
    <li><a href="#">link1</a></li>
    <li><a href="#">link2</a></li>
    <li><a href="#">link3</a></li>
    <li><a href="#">link4</a></li>
    <li><a href="#">link5</a></li>
  </ul>
</nav>
```
En main.hbs
```hbs
{{> navBar}}
<!-- Junto con su diseño base -->
```
---
## Express rutas
Se crea la carpeta **routes** y en ella se asignan las rutas en sus documentos especificos.

### En routes/home.routes.js
```js
const express = require('express');
const router = express.Router();

router.get('/',(req,res)=>{
  res.render('home');
});

module.exports = router;
```

### En index.js
```js
app.use("/", require('.routes/home.routes'));
//Ruta adicional "/" --> no hay ruta adicional
//Importacion de las rutas del documento
```
---
## CRUD con Mongoose
Mas detalles en MongoDB_Mongoose.md
```
npm i mongoose
```
### Variables de entorno (.env)

En el archivo se asignan variables importantes como la conexion a la base de datos, estas variables no deben de compartirse. Se crea un documento **.env** para comenzar y se instala el modulo **dotenv** *(gestiona las variables de entorno)*.

```
npm i dotenv
```
```js
require("dotenv").config(); //Por defecto
//En config(Ruta de la variable)
```

En el archivo **.env**
```env
URLMongoDB = mongodb+srv://<nombreUsuario>:<password>@cluster0.vs8iz.mongodb.net/<nombreDB>
```

### Conectar base de datos
En un archivo db.js dentro de una carpeta database.

En database/db.js
```js
const mongoose = require("mongoose");

mongoose.connect(process.env.URLMongoDB)
  .then(()=> console.log("Base de datos conectada"))
  .catch((e)=> console.log("Fallo la conexión"+e));
```

En index.js
```js
require("./database/db");
```

### Creación de modelo de datos
Se crea un archivo esquema.js dentro de la carpeta models

En models/esquema.js
```js
const {Schema, model} = require('mongoose'); 
const EsquemaDB = mongoose.Schema({
    atributo: {
      type: String, //tipo string
      unique: true, //valor unico verdadero
      required: true, //requerido verdadero
      default: Date.now() //La fecha como valor por defecto
    }
})
module.exports= mongoose.model('Esquema',EsquemaDB); 
```
### CRUD
En controllers/esquemaControllers.js

```js
const Esquema = require("../models/Esquema");
//Requiere el modelo del esquema esquema

exports.crearEsquema= async(req,res) =>{ 

    try{
        let esquema;
        esquema= new Esquema(req.body);
        await esquema.save();
        res.send(esquema);

    }catch(err){
        console.error(err);
        res.status(500).send('Hubo un error');
    }
}

exports.obtenerEsquemas= async(req,res) =>{
    try{
        const esquemas = await Esquema.find();
        res.json(esquemas);
    }catch(err){
        console.log(err);
        res.status(500).send('Hubo un error');
    }
}

exports.actualizarEsquema= async(req,res) =>{
    try{
        const { Nombre, Escuela, Grupo, Boleta } = req.body;
        let esquema = await Esquema.findById(req.params.id);
        if (!esquema){
            res.status(404).json( {msg:'No existe el esquema'});
        }
        esquema.Nombre = Nombre;
        esquema.Escuela = Escuela;
        esquema.Grupo = Grupo;
        esquema.Boleta = Boleta;

        esquema = await Esquema.findOneAndUpdate({ _id: req.params.id }, esquema,{new: true});
        res.json(esquema);
    }catch(err){
        console.log(err);
        res.status(500).send('Hubo un error');
    }
}

exports.obtenerEsquema= async(req,res) =>{
    try{
        let esquema = await Esquema.findById(req.params.id);
        if (!esquema){
            res.status(404).json( {msg:'No existe el esquema'});
        }
        res.json(esquema);
    }catch(err){
        console.log(err);
        res.status(500).send('Hubo un error');
    }
}

exports.eliminarEsquema= async(req,res) =>{
    try{
        let esquema = await Esquema.findById(req.params.id);
        if (!esquema){
            res.status(404).json( {msg:'No existe el esquema'});
        }
        await Esquema.findOneAndRemove({ _id: req.params.id });
        res.json({msg: "El esquema fue eliminado"});
    }catch(err){
        console.log(err);
        res.status(500).send('Hubo un error');
    }
}
```

---

## Crear Middleware

En routes/home.routes.js
```js
const express = require('express');
const router = express.Router();

router.get('/mostrar',Validar, esquemaController.obtenerEsquema);

module.exports = router;
```

En middlewares/Validar.js
```js
const Validar = (req,res,next)=>{
  try{
    if(iniciosession){
      return next();
    }else{
      throw new Error("No ha iniciado sesion");
    }
  }catch(e){
    console.log(e);
  }
}
```
> next( ) pasa a la siguiente ruta, en este caso, esquemaController.obtenerEsquema
