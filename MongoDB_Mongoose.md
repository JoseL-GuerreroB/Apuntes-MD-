# MongoDB y Mongoose

---

## Descripción

MongoDB es un gestor de bases de datos no relacional y Mongoose es un modulo de apoyo para usar MongoDB en proyectos de node de una forma más sensilla.

### Instalacíon

**MongoDB** se descarga desde su [pagina oficial](https://www.mongodb.com/try/download).

> Colocar **"C:\Program Files\MongoDB\Server\5.0\bin\"** en tus variables de entorno

Una vez instalado, podras ejecutar el servidor en la terminal ejecutando en la misma **mongod** y para comenzar a crear y gestionar bases de datos, en otra terminal ejecuta **mongo** para activar el cliente, en esta terminal sera la unica que utilizaras.

```js
mongod; //servidor

mongo; //cliente
```

Coneccion el la nube

Tambien puedes crear bases de datos y utilizarlas desde la nube, utilizando mongoDB Atlas registrandote en la [pagina oficial](https://www.mongodb.com/cloud/atlas/lp/try2?utm_content=controldbaasterms&utm_source=google&utm_campaign=gs_americas_mexico_search_core_brand_atlas_desktop&utm_term=cloud%20mongodb&utm_medium=cpc_paid_search&utm_ad=e&utm_ad_campaign_id=12212624326&adgroup=115749706063). Sigue las instrucciones para crear y utilizar las bases de datos.

**Mongoose** se instala desde la terminal con npm.

```
npm i mongoose
```

---

## Bases de datos

### Consultas basicas

Mostrar bases de datos

```
show databases;
```

Usar o crear la base de datos decignada

```
use nombreBaseDeDatos;
```

### Una vez dentro de la base de datos

Usar o crar una colleccion con contenido

```js
db.nombreColeccion.insert(objetoJSON);
//{"nombre":"luis","nivel": 3, "edad":23} se almacena en la coleccion nombreColeccion de la base de datos
```

Desplegar el contenido de la coleccion especifica

```js
db.nombreColeccion.find();
```

Su forma de Tabla

| Nombre | Nivel | Edad |
| ------ | ----- | ---- |
| Luis   | 3     | 23   |

Su forma en JSON

```json
objetoJSON = {
    "Nombre": "Luis",
    "Nivel": 3,
    "Edad": 23
}
```

---

## CRUD

### Creacion de datos "C"

**Creacion unica**

El id se crea por defecto y es un valor aleatorio

```js
db.usuarios.insertOne(usuario1); //valores que devuelve en la CMD
//{ "acknowledged" : true, "insertedId" : ObjectId("************")}
```

Contenido usuario1

```json
usuario1 = {
    "Nombre": "Luis",
    "Correo": "nom1@email1.com",
    "Edad": 19,
    "Estudiando" : true
}
```

Su forma de Tabla

| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       |

**Creacion multiple**

```js
db.usuarios.insertMany([usuario2,usuario3,usuario4]);
//valores que devuelve en la CMD
//{
//    "acknowledged" : true,
//    "insertedIds" : [
//            ObjectId("621aa7eb8c9ed42e85174d3d"),
//            ObjectId("621aa7eb8c9ed42e85174d3e"),
//            ObjectId("621aa7eb8c9ed42e85174d3f")
//    ]
//}
```

Contenido usuario 2, 3 y 4

```json
usuario2 = {
    "Nombre": "Maria",
    "Correo": "nom2@email2.com",
    "Edad": 18
}
usuario3 = {
    "Nombre": "Luis",
    "Correo": "nom3@email3.com",
    "Edad": 20,
    "Estudiando": false
}
usuario4 = {
    "Nombre": "Paula",
    "Correo": "nom4@email4.com",
    "Edad": 18
}
```

Su forma de Tabla

| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       |
| IDrandom2  | Maria  | nom2@email2.com | 18   |false      |
| IDrandom3  | Luis   | nom3@email3.com | 18   | 
| IDrandom4  | Paula  | nom4@email4.com | 20   |

### Lectura de datos "R"

**Consulta todos los documentos que coincidan con:**
```js
db.usuarios.find(
    {
        "Nombre": "Luis" //Hay dos usuarios
    }
)
```
Retorna

| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       |
| IDrandom3  | Luis   | nom3@email3.com | 18   | 


**Consulta el primer documento que coincida con:**
```js
db.usuarios.findOne( //Solo el primer documento
    {
        "Nombre": "Luis"
    }
)
```
Retorna

| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       | 

**Consulta los documentos que cumplan la condicion**
Usuarios mayores o igual a 19 años
```js
//gt: >, gte: >=, lt: <, lte: <=, ne: !=.

db.usuarios.find(
    {
        "Edad": {$gte: 19} //Mayor o igual a 19
    }
)
```
retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       | 
| IDrandom4  | Paula  | nom4@email4.com | 20   |


**Consulta los documentos que cumplan con todas las condiciones asignadas "Y"**

Nombre Luis y edad < 19años
```js
db.usuarios.find(
    $and:[ //"Y"
        { "nombre": "Luis" },//igual a Luis
        { "Edad": {$lt: 19} }//menor a 19
    ]
)
```
Retorna

| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom3  | Luis   | nom3@email3.com | 18   |

**Consulta los documentos que cumplan una o mas condiciones asignadas "O"**

Nombre Paula o edad == 18
```js
db.usuarios.find(
    $or:[ //"O"
        { "nombre": "Paula" },//igual a Paula
        { "Edad": 18 }//igual a 18
    ]
)
```
Retorna

| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom2  | Maria  | nom2@email2.com | 18   |false      |
| IDrandom3  | Luis   | nom3@email3.com | 18   | 
| IDrandom4  | Paula  | nom4@email4.com | 20   |

**Consulta los documentos que cumplan una o mas condiciones asignadas "IN"**

```js
db.usuarios.find({ // para listas más extensas
    "Edad": {$in: [20,19]} //listado de edad
});
```
Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       |
| IDrandom4  | Paula  | nom4@email4.com | 20   |

**Consulta los usuarios que registraron si estan estudiando o no**
```js
db.usuarios.find({
    "Estudiando": {$exists: true} //Existe Estudiando
});
```
Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       |
| IDrandom2  | Maria  | nom2@email2.com | 18   |false      |

**Ordena los documentos de mayor a menor con respecto a la edad**
```js
db.usuarios.find().sort({ //ordenar
    "edad": -1 //De mayor a menor
});
```

Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom4  | Paula  | nom4@email4.com | 20   |
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       |
| IDrandom2  | Maria  | nom2@email2.com | 18   |false      |
| IDrandom3  | Luis   | nom3@email3.com | 18   |

**Consulta el documento con menor edad**
```js
db.usuarios.find().sort({ //ordenar
    "edad": +1 //De menor a mayor
}).limit(1);//Mostrar 1
```
Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom2  | Maria  | nom2@email2.com | 18   |false      |

**Cuantos documentos contiene una coleccion**
```js
db.usuarios.find().count();
//Devuelve 4
```

**Consulta los documentos despues del segundo documento**
```js
db.usuarios.find().skip(2);
```

Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom3  | Luis   | nom3@email3.com | 18   |
| IDrandom4  | Paula  | nom4@email4.com | 20   |

**Consulta por caracteres**

**Iniciales (correo: nom2)**
```js
db.usuarios.find({
    "Correo": /^nom2/
});
```
Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom2  | Maria  | nom2@email2.com | 18   |false      |

**finales (correo: .com)**
```js
db.usuarios.find({
    "Correo": /.com$/
});
```
Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       |
| IDrandom2  | Maria  | nom2@email2.com | 18   |false      |
| IDrandom3  | Luis   | nom3@email3.com | 18   |
| IDrandom4  | Paula  | nom4@email4.com | 20   |

**intermedias (nombre: ui)**
```js
db.usuarios.find({
    "Nombre": /ui/
});
```

Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 19   | true       |
| IDrandom3  | Luis   | nom3@email3.com | 18   |

**Recolectar los documentos de una coleccion mostrando unicamente el atributo designado**
```js
db.usuarios.find().forEach( user => print(user.Correo)); //devuelve solo los atributos deseados de toda la coleccion
```
Retorna
| insertedId | Correo          |
| ---------- | --------------- |
| IDrandom1  | nom1@email1.com |
| IDrandom2  | nom2@email2.com |
| IDrandom3  | nom3@email3.com |
| IDrandom4  | nom4@email4.com |

>El ID Aparece por defecto

**Recolectar los documentos usando proyexiones**
```js
db.usuarios.find(
	{}, //condiciones
	{
        "_id": false, //Descarta el ID
        "Correo": true
    }  //proyecciones, El atributo que se muestra por defecto es "_id": true 
	a menos que se indique lo contrario
);
```
Retorna
| Correo          |
| --------------- |
| nom1@email1.com |
| nom2@email2.com |
| nom3@email3.com |
| nom4@email4.com |

### Actualización de datos "U"

**Actualizar un documento** 

Cambia el correo al documento con ID IDrandom3 y agraga en atributo Estudiando como false.

```js
db.usuarios.updateOne( // funciona con un solo documento y el primero
	{
        "_id": "IDrandom3" //objectId("**********")
    }, //condiciones a evaluar, uso de ID recomendado
	{
	    $set:{
            "Correo": "luis25@gmail.com",
            "Estudiando": false
        }
	}
);
```
> Set: permite cambiar los valores del los atributos seleccionados. Tambien permite añadir nuevos atributos.

Nuevo valor al seleccionarlo

| insertedId | Nombre | Correo           | Edad | Estudiando |
| ---------- | ------ | ---------------- | ---- | -----------|
| IDrandom3  | Luis   | luis25@gmail.com | 18   | false      |

Elimina el atributo de Estudiando del ID IDrandom3

```js
db.usuarios.updateOne( // funciona con un solo documento y el primero
	{
        "_id": "IDrandom3" //objectId("**********")
    }, //condiciones a evaluar, uso de ID recomendado
	{
	    $unset:{
            "Estudiando": true
        }
	}
);
//Elimina el atributo Estudiando
```
> Unset: permite eliminar uno o varios atributos.

Nuevo valor al seleccionarlo

| insertedId | Nombre | Correo           | Edad | Estudiando |
| ---------- | ------ | ---------------- | ---- | -----------|
| IDrandom3  | Luis   | luis25@gmail.com | 18   |


**Actualizar varios documentos**

Suma 1 año en edad a todos los documentos de la colección.

```js
db.usuarios.updateMany( 
	{
        //Sin condiciones
        //Se le pueden añadir condiciones
    },
	{
	    $inc:{
            "Edad": 1
        }
	}
);
```
> Inc: incrementa en un valor, los datos numericos

Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom1  | Luis   | nom1@email1.com | 20   | true       |
| IDrandom2  | Maria  | nom2@email2.com | 19   |false      |
| IDrandom3  | Luis   | nom3@email3.com | 19   |
| IDrandom4  | Paula  | nom4@email4.com | 21   |

### Eliminar datos "D"
**Eliminar los documentos que en Nombre == Luis y Edad == 20**
```js
db.usuarios.remove( 
	{
        $and:[
            { "Nombre": "Luis" },
            { "Edad": 20 }
        ]
    }
);
```
Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|
| IDrandom2  | Maria  | nom2@email2.com | 19   |false      |
| IDrandom3  | Luis   | nom3@email3.com | 19   |
| IDrandom4  | Paula  | nom4@email4.com | 21   |

**Elimina todos los documentos de una colección**

```js
db.usuarios.remove({ });
```
Retorna
| insertedId | Nombre | Correo          | Edad | Estudiando |
| ---------- | ------ | --------------- | ---- | -----------|

> Sin documentos

**Eliminar colección y base de datos.**

```js
db.usuarios.drop(); //Elimina la coleccion
db.dropDatabase(); //Elimina la base de datos
```
---
## Documentos anidados

```js
use BaseDeDatosCLi; //Crea y se introduce el la base de datos

db.clientes.insertMany([cliente1,cliente2,cliente3]);
//Crea e introduce 3 documentos en la nueva colección
```

Documentos

```json
cliente1={
    "nombre": "Jose",
    "email": "jcorreo@gcorreo.com",
    "edad": 21,
    "conectado": "activo",
    "direccion": {
        "codigoPostal": 55406,
        "pais": "Mexico"
    },
    "cursos": ["MongoDB","Node","Express","React"],
    "comentarios": [{
            "texto": "buenos cursos",
            "like": true,
            "expectativas": ["MongoDB","Node"]
        },{
            "texto": "muy agradables",
            "like": true,
        },{
            "texto": "No es gran cosa"
        },{
            "texto": "mal curso",
            "like": false,
            "expectativas": ["React","Node"]
        }
    ]
}

clinte2={
    "nombre": "Oscar",
    "email": "Ocorreo@Acorreo.com",
    "edad": 19,
    "conectado": "inactivo",
    "cursos": ["MongoDB","Express"],
    "comentarios": [{
            "texto": "muy agradables",
            "like": true,
        },{
            "texto": "mal curso",
            "like": false,
            "expectativas": ["Node","Express"]
        }
    ]
}

clinte3={
    "nombre": "Lisa",
    "email": "Lcorreo@Scorreo.com",
    "edad": 21,
    "conectado": "activo",
    "direccion": {
        "pais": "Mexico"
    },
    "comentarios": [{
            "texto": "muy agradables"
        },{
            "texto": "buen curso",
            "expectativas": ["Express", "MongoDB"]
        }
    ]
}
```

### Obten los documentos que tengan como pais Mexico
```js
db.clientes.find({
	"direccion.pais": "Mexico"
}); // atributo1.atributo11.atributo111... etc.
```
```js
"direccion": {
        "pais": "Mexico"
    }
// 2 documentos cumplen con la condición
```
**Retorna los documentos**
* cliente1
* cliente3

### Cambia el codigo postal de cliente1
```js
db.clientes.updateOne({
    "_id": objectId("**********");
    //Id del documento
},{
    $set:{
        { "direccion.codigoPostal" = 55321 }
    }
})
```
```json
"direccion": {
        "codigoPostal": 55321
    } 
//El dato se actualizo
```

### Encuentra los ducumentos en los que en el listado de cursos se encuentre Express y Node
```js
db.clientes.find({
	"cursos": {
        $all:["Express","Node"]
    }
}); 
```
> All: Si el documento cumple con un requerimiento de esta propiedad, entra en la categoria.

```json
"cursos": ["Node","Express"]
// 2 documentos cumplen con los requirimientos
```
**Retorna los documentos**
* cliente1
* cliente2

### Encuentra los ducumentos en los que el listado de cursos contenga 4 valores

```js
//Arreglo de 4 valores
db.clientes.find({
	"cursos": {
        $size: 4
    }
}); 
```
> Size: Si el atributo del documento contiene un arreglo con el total de valores requeridos, entra en la categoria.

```json
"cursos": ["MongoDB","Node","Express","React"]
// 1 documento cumple con los requirimientos
```
**Retorna los documentos**
* cliente1


### Encuentra los ducumentos que tengan comentarios positivos (like : true)
```js
db.clientes.find({
	comentarios: {
        $elemMatch:{
            "like": true
        }
    }
}); 
```
```json
"comentarios": [{
            "like": true
        }];
//Dos documentos cumplen con los requerimientos
```
**Retorna los documentos**
* cliente1
* cliente2

### Añade un nuevo comentario al cliente2

```js
db.clientes.updateOne({
    "_id": objectId("**********");
    //Id del documento
},{
    $push:{
        comentarios: {
            "texto": "Es un buen curso",
            "like": true
        }
    }
});
```
```json
"comentarios": [{
        "texto": "muy agradables",
        "like": true,
    },{
        "texto": "mal curso",
        "like": false,
        "expectativas": ["Node","Express"]
    },{
        "texto": "Es un buen curso",
        "like": true
    }
]
```

### Añade un curso al cliente3

```js
db.clientes.updateOne({
    "_id": objectId("**********");
    //Id del documento
},{
    $push:{
        "cursos": "React"
    }
});
```
```json
"cursos": ["React"],
```

### Añade una nueva expectativa al primer comentario del cliente2

```js
db.clientes.updateOne({
    "_id": objectId("**********");
    //Id del documento
},{
    $push:{
        "comentarios.0.expectativas": "Python"
    }
});
```
```json
"comentarios": [{
        "texto": "muy agradables",
        "like": true,
        "expectativas": ["Python"]
    },{
        "texto": "mal curso",
        "like": false,
        "expectativas": ["Node","Express"]
    },{
        "texto": "Es un buen curso",
        "like": true
    }
]
```

### Cambia a negativo las propiedades de el tercer comentario del cliente1

```js
db.clientes.updateOne({
    "_id": objectId("**********");
    //Id del documento
},{
    $set:{
        "comentarios.2.texto": "Es un mal curso",
        "comentarios.2.like": false
    }
});
```
```json
"comentarios": [{
            "texto": "buenos cursos",
            "like": true,
            "expectativas": ["MongoDB","Node"]
        },{
            "texto": "muy agradables",
            "like": true,
        },{
            "texto": "Es un mal curso",
            "like": false
        },{
            "texto": "mal curso",
            "like": false,
            "expectativas": ["React","Node"]
        }
    ]
```
> Si desconocemos el numero del comentario o si pretendemos cambiar todos los miembros de la lista utilizamos"comments.**$**.tags". 

### Exportar Base de datos

```
sudo mongoexport --db newdb -c restaurants --out newdbexport.json
```
---
## Uso de mongoose
Una vez instalado see crea un documento para configurar la base de datos.
En db.js
```js
const mongoose = require('mongoose'); //importación de mongoose

const urlMongoDBAtlas = "mongodb+srv://<nombreUsuario>:<password>@cluster0.vs8iz.mongodb.net/<nombreDB>";

const urlLocalhost = "mongodb://localhost:27017/<nombreApp>"

const conectarDB = async () => {

    try {
        //Conectar a la base de datos
        await mongoose.connect(urlMongoDBAtlas || urlLocalhost, {
            useNewUrlParser: true,
            useUnifiedTopology: true
            //Opciones de configuracion
        })
        console.log('BD Conectada');
        
    } catch (error) { //Acciones al encontrar un error
        console.log(error);
        process.exit(1); // Detenemos la app
    }

}

module.exports = conectarDB; //Exportacion de la conexión
```
En index.js
```js
const conectarDB = require("./db.js");
//Importación de la base de datos

conectarDB();
//Estableciendo la conexión de la base de datos
```

Se crea una carpeta models para establecer en los archivos internos el esquema que tendran los documentos de la base de datos.

En Models/Estudiante.js

```js
const mongoose = require('mongoose'); //Importacion mongoose
const EstudianteSchema = mongoose.Schema({
    Nombre: { 
        type: String, //Recibira tipo de dato string
        required: true //Dato requerido
    },
    Escuela: {
        type: String,
        required: true
    },
    Grupo: {
        type: String,
        required: true
    },
    Boleta: {
        type: Number, //Recibira tipo de dato number
        required: true
    },
    fechaCreacion: {
        type: Date, //Recibira tipo de dato fecha
        default: Date.now() //Por defecto se asigna como valor la fecha más actual
    }
})
module.exports= mongoose.model('Estudiante',EstudianteSchema); //Se exporta el esquema
// model (nombreDeLaColección, esquemaDelDocumento)
```
> El nombre de la colección debe de ser escrito en singular, ya despues mongoose se encargara de ajustar el nombre poniendolo en minusculas y en plural

En controllers/estudianteControllers.js

```js
const Estudiante = require("../models/Estudiante");
//Requiere el modelo del esquema estudiante

exports.crearEstudiante= async(req,res) =>{ //funcion asincrona (peticion, respuesta)
    try{
        let estudiante;

        //Creamos nuestro estudiante con el cuerpo del esquema
        estudiante= new Estudiante(req.body);
        //Los datos recibidos son evaluados por el esquema y los datos recibidos se colocan en su lugar. Se crea como documento.
        await estudiante.save();
        //Se guarda el documento en la colección y en su base de datos
        res.send(estudiante);
        // Respuesta del servidor exitosa

    }catch(err){ //¿Si hubo un error?
        console.error(err); //Muestra en consola el error
        res.status(500).send('Hubo un error');
        // Respuesta del servidor negativa
    }
}

exports.obtenerEstudiantes= async(req,res) =>{
    try{
        const estudiantes = await Estudiante.find();
        // Se guardan los documentos existentes en la colección de esa estructura
        res.json(estudiantes);
        // El servidor responde con los Json
    }catch(err){
        console.log(err);
        res.status(500).send('Hubo un error');
    }
}

exports.actualizarEstudiante= async(req,res) =>{
    try{
        const { Nombre, Escuela, Grupo, Boleta } = req.body;
        //Es como decir:
        //estudante.Nombre = req.body.Nombre
        // Y asi con las otras 3
        let estudiante = await Estudiante.findById(req.params.id);//params.id detecta el /:id de la tuta
        if (!estudiante){ //Si no existe el estudiante
            res.status(404).json( {msg:'No existe el estudiante'});
        }
        estudiante.Nombre = Nombre;
        estudiante.Escuela = Escuela;
        estudiante.Grupo = Grupo;
        estudiante.Boleta = Boleta;

        //Asignar los valores de las constantes en los parametros del objeto

        estudiante = await Estudiante.findOneAndUpdate({ _id: req.params.id }, estudiante,{new: true});
        //Busca en los documentos el id y actualiza el documento con los valores de estudiante
        //new: true como nuevo valor
        res.json(estudiante);
        //Respuesta del servidor
    }catch(err){
        console.log(err);
        res.status(500).send('Hubo un error');
    }
}

exports.obtenerEstudiante= async(req,res) =>{
    try{
        let estudiante = await Estudiante.findById(req.params.id);
        //Busca a un documnto por su ID
        if (!estudiante){
            res.status(404).json( {msg:'No existe el estudiante'});
        }
        res.json(estudiante);
    }catch(err){
        console.log(err);
        res.status(500).send('Hubo un error');
    }
}

exports.eliminarEstudiante= async(req,res) =>{
    try{
        let estudiante = await Estudiante.findById(req.params.id);
        if (!estudiante){
            res.status(404).json( {msg:'No existe el estudiante'});
        }
        await Estudiante.findOneAndRemove({ _id: req.params.id });
        //Busca y elimina el documento
        res.json({msg: "El estudiante fue eliminado"});
    }catch(err){
        console.log(err);
        res.status(500).send('Hubo un error');
    }
}
```

En routes/rutasEstudiante.js

```js
const express= require('express');
const router= express.Router();
//Importar router express
const estudianteController=require('../controllers/estudianteControllers');
//Importamos el documento controller de estudiantes

//Definimos ruta principal
router.post('/', estudianteController.crearEstudiante);
//Envia datos para crear documentos en la base de datos

router.get('/', estudianteController.obtenerEstudiantes);
//Devuelve los datos contenidos en los documentos de una collección

router.put('/:id', estudianteController.actualizarEstudiante);
//Busca un documento en particular por su ID para que se actualice

router.get('/:id', estudianteController.obtenerEstudiante);
//Busca un documento en particular por su ID

router.delete('/:id', estudianteController.eliminarEstudiante);
//Busca un documento en particular por su ID para que se elimine

module.exports=router;
```