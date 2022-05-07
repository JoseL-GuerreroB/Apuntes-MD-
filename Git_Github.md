# Git y Github
---
## Descripción

Git es un sistema de control de verciones descentralizado, permite a distintos programadores trabajar en un mismo proyecto. 

Github es un portal creado para alojar el código de las aplicaciones de cualquier desarrollador. (El espacio donde se aloja un proyecto se conoce como repositorio).

### Instalación

Git se instala descargadolo en su [pagina oficial](https://git-scm.com/downloads).

Github es un portal que puede ser usado desde la web y puedes registrarte en su [pagina oficial](https://github.com/) para utilizarlo.

### Configuración global

Versión de Git *(tu version de git)*
```bash
git --version
```
Nobre de usuario *(git)*
```bash
git config --global user.name "nomreUsuario"
```
Correo de usuario *(git)*
```bash
git config --global user.email emailUsuario@correo.correo
```
Editor de codigo predeterminado *(git-VSCode)*
```bash
git config --global core.editor "code --wait"
```
Ver nuestro archivo de configuracion global
```bash
git config --global -e
```
**Saltos de linea (CR --> Carriage Return, LF -->  Line Feed)**

*SO Windows, CR y LF como marcadores de salto de linea*

*Al subir al repositorio se anula el marcador CR y al descargar el repositorio se añade.*
```bash
git config --global core.autocrlf true
```

*SO linux/mac, LF como marcador de salto de linea*

*Usar en caso de contar con un caracter CR*
```bash
git config --global core.autocrlf input
```
> Util cuando dos o más programadores trabajan en el mismo proyecto y tinen distintos sistemas operativos

Ver configuraciones disponibles
```bash
git config -h
```
---
## Comandos de Git

### Comandos basicos

**ls --> Muestra la ruta y los documentos de la carpeta en la que te encuentras**
```bash
ls
```
* C:\Users\userName\Desktop\Carpeta
* Documentos o archivos de carpeta

**pwd --> Sirve para ver en que ruta de nuestro sistema esta posicionado el terminal (carpeta)**
```bash
pwd
```
* C:\Users\userName\Desktop\Carpeta

**cd --> Sirve oara moverse entre carpetas**
```bash
cd Carpeta2
```
* C:\Users\userName\Desktop\Carpeta\Carpeta2

```bash
cd ..
```
* C:\Users\userName\Desktop\Carpeta

**mkdir nombreCarpeta -->  Crea una carpeta desde la terminal**
```bash
mkdir nombreCarpeta
```

### Comandos de inicio

**Inicializar un proyecto Git** *(Solo una vez por proyecto)*
```bash
git init
```
> Area de computador: En el se encuentran los archivos nuevos y modificados fuera del seguimiento de git

**Ver que archivos concidera git para su seguimiento y cuales todavia no.** *Tambien nos da las branch (por defecto es main).*
```bash
git status
```
Git status resumido
```bash
git status -s
```

**Añadir archivos para conciderar en el proyecto ( . -->todos)**
```bash
git add nombreArchivo.txt
git add Archivo1.txt Archivo2.txt
git add .txt
git add .
```
* Seguir 1 archivo especifico
* Seguir 2 o más archivos especificos
* Sigue todos los archivos de una extencion (en este caso, solo archivos.txt)
* Todos los archivos existentes (mala practica, usar en caso de estar 100% conciente de los archivos).

>Area de paso: En el se encuentran los archivos en los que git hace su seguimiento. Tambien se debe hacer seguimiento de archivos borrados.

**Realizar un commit del proyecto** *(Nombrar adecuadamente)*
```bash
git commit -m "Nombre del commit"
```

> Area comprometida: En esta area se encuentran todos los cambios comprometidos (commits). Al hacer un commit se lebera el area de paso.

**Eliminar archivos y conciderar el cambio en el seguimiento de git**
```bash
rm archivo2.txt
git add archivo2.txt
```
* Elimina archivo2.txt
* Adiere la eliminacion al seguimiento

Tambien puedes usar
```bash
git rm archivo2.txt
```
* Elimina el archivo y lo adiere al seguimiento

**Sacar un archivo del area de paso**
```bash
git restore --staged archivo1.txt
```

**Restaurar el archivo en el area de trabajo**
```bash
git restore archivo1.txt
```

**Renombrar archivo y conciderar el cambio en el seguimiento de git**
```bash
git mv archivo1.txt archivo.txt
```
* Renombre archivo1.txt y ahora es archivo.txt

**Ver diferencia** entre *commit anterior y los cambios actuales sin seguimiento*. Tambien funciona con *seguimientos anteriores y cambios actuales sin seguimiento.*
```bash
git diff
```
```bash
git diff --staged
```
> Salir de la comparacion con la tecla "q"

**Historial de commits**
```bash
git log --oneline
```

Mostrar el contenido de un archivo
```bash
cat archivo1.txt
```

### Gitignore
Se utiliza para ignorar archivos o carpetas que no deceas conciderar en el seguimiento de git. Crea el archivo y nombralo **.gitignore**

```
.env
node_modules/
```

* Ignorar archivos con extencion **env** *(variables globales)*
* Ignorar la carpeta **node_modules** y su contenido

**IMPORTANTE:**
Añadir .gitignore

```bash
git add .gitignore
git commit -m "Gitignore implementado en el commit"
```

### Git branch

**Muestra las ramas existentes** del proyecto y muestra en cual nos encontramos.
```bash
git branch
```
* **main** (rama por defecto)

**Crear una nueva rama** y entra en ella
```bash
git checkout -b ramab
```
* main
* **ramab**

**Eliminar ramas existentes**
```bash
git branch -d nombreRama
```

**Moverse entre ramas existente**
```bash
git checkout main
```

**Fusionar ramab con la rama principal**

*Estando en la rama principal (main*
```bash
git merge ramab
```
---
## Repositorios en Github

### Subir un proyecto a github
```bash
git remote add origin urlDelRepositorio
git push -u origin main
```
* Se establece la url que conectara tu proyecto con el repositorio
* Envia el proyecto (**git push**)

>La rama main no se encuentra en github, se crea la rama en el origen por medio de  " **-u origin main** "

### Subir una rama del proyecto a github
Una vez ya teniendo la rama principal en github
```bash
git checkout -b ramaC
git push -u origin ramaC
```

### Git PULL (git fetch + git merge)
El comando git pull se emplea para extraer y descargar contenido desde un repositorio remoto y actualizar al instante el repositorio local para reflejar ese contenido.

Hacer commit antes de un pull.
```bash
git pull
```

> Repara los errores al hacer git push y tambien permite obtener documentos del repositorio en tu proyecto local.

### Git fetch
Detecta los cambios en el repositorio remoto.
Se descargan todos los cambios hechos en el repositorio de github en nuestro proyecto.
```bash
git fetch
```

> Sirbe para obtener documentos y ramas del repositorio de github en el proyecto local, sin fusionar las ramas.

**Obtener ramas del repositorio de github**
```bash
git fetch
git branch -r
git checkout ramaExterna
```
* Optiene los datos del repositorio de github
* Muestra todas las ramas, incluyendo las obtenidas por el git fetch
* Introduce a la rama especifica

### Git Tags
Identifica un commit para hacer un control de versiones.

**Crear un tag**
```bash
git tag v0.0.1 -m "primera version"
```
Dar un tag a un commit existente
```bash
git tag idCommit -m "primera version"
```
> el idCommit lo obtienes con git log

**Enviar los tags a github**
```bash
git push --tags
```

**Entrar a un commit o un tag especifico**
```bash
git checkout idCommit
git checkout v0.0.1
```

**Mostrar todos los tags**
```bash
git tag
```

**Eliminar un tag**
```bash
git tag -d vercionTag
```

### Git Clone

**Clonar un repositorio**
```bash
git clone urlRepositorio
```


**Clonar un repositorio con nombre**
```bash
git clone urlRepositorio nombreRepositorio
cd nombreRepositorio
```

**Crear commit vasio en una rama y subirla al repositorio** *(necesitas crear un nuevo repositorio)*
```bash
git commit --allow-empty -m "Commit inicial de la rama"
git push --set-upstream origin nombreRepositorio
```

### Fork
Clona el repositorio de un extraño en un repositorio tuyo.