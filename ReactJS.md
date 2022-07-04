# ReactJS
---
Es una libreria de javascript que es utilizada para crear interfaces de usuario.

**Instalación**
```bash
npx creat-react-app nombreapp
```
> El nombre de la app debe tener unicamente minusculas

## JSX 
---
Te permite codificar en javascript con sintaxis HTML.

### Sintaxis basica
```jsx
import React from 'react';//importacion de React (JSX)
import './App.css';//importacion de documento css

//Crea el modulo
function App() {
  return (

  );
}
export default App; //Exportacion del modulo
```
### Sintaxis especial

* Usar className="" en lugar de class="".
* Usar htmlFor="" en lugar de for="".
* Solo se permite usar una etiqueta contenedor <_____></____> o usar <></>.
* Etiquetas como input, img o br, cerrar la etiqueta de esta manera <_______/>
* Usar **{** las llaves **}** para utilizar variables, interpolaciones, funciones, etc dentro de la sintaxis HTML.

```jsx
function App() {
  const valor1 = "cantidad";
  return (
    <>
    <div className='cont'>
      <label className={valor1} htmlFor="inp"> <input id='inp' type="text" /> </label>
      <br />
    </div>
    <div className='cont'>
      <img src="#" alt="imagen" />
      <p> {valor1} </p>
      <br />
    </div>
    </>
  );
}
```

### Creación de elementos con base en un arreglo
```jsx
function App() {
  const estaciones = ["primavera","verano","otoño","invierno"];
  return (
    <div>
      <h2>Estaciones del año</h2>
      <ul>
        {
          estaciones.map((est,index)=>{
            <li key={index}> {est} </li>
          })
        }
      </ul>
    </div>
  );
}
```
---
## Componentes

Son pedasos de codigo reutilizables que pueden interactuar entre sí, de componentes padres a hijos.

> Introduce todos tus componentes en una carpeta components

### Tipos de componentes

De clase:

```jsx
import React, { Component } from 'react';
//Importacion de { Component } en el componente.

class nombreClass extends Component {
  render() {
    return (
      <div>
        Hola mundo
      </div>
    )
  }
}

export default nombreClass;
```
Funcionales:
```jsx
import React from 'react';

export default function nombreFuncion() {
  return (
    <div>
      Hola mundo
    </div>
  )
}
```

### Crear componente

Se crean en un documento Component.js o .jsx. Al crear el documento se recomienda usar CamelCase dede la primera letra.

En component/Component.jsx
```jsx
import React from 'react';

export default function Componente() {
  return (
    <div>
      Hola mundo
    </div>
  )
}
```
En app.js
```jsx
import Componente from './components/Componente'; //importacion del componente
import React from 'react';
import './App.css';

//Crea el modulo
function App() {
  return (
      <Componente></Componente> //Introduce el componente
      <Componente/> //Introduce el componente
  );
}
export default App; //Exportacion del modulo
```

### Propiedades

Valores que recibe un componente hijo de un componente padre.

En app.js
```jsx
<Componente cadena="Hola mundo" numero={9} booleano={true} arreglo={[1,2,3]} objeto={{nombre: "Juan", apellido: "Cardenas"}} funcion={(num)=>num*num} HTMLElemento={<i>Elemento creado</i>} ComponenteElemento={<Componente2/>} />
```
En components/Componente.jsx
```jsx
//Componente funcional
import React from 'react';

export default function Componente(props) {
  return (
    <div>
      <h1>Tipos de propiedades</h1>
      <ul>
        <li>{props.cadena}</li>
        <li>{props.numero}</li>
        <li>{props.booleano}</li>
        <li>{props.arreglo.join(", ")}</li>
        <li>{props.objeto.nombre + " - " + props.objeto.apellido}</li>
        <li>{props.arreglo.map(props.funcion)}</li>
        <li>{props.HTMLElemento}</li>
        <li>{props.ComponenteElemento}</li>
      </ul>
    </div>
  )
}

//Componente de clase
class nombreClass extends Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Tipos de propiedades</h1>
        <ul>
          <li>{this.props.cadena}</li>
          <li>{this.props.numero}</li>
          <li>{this.props.booleano}</li>
          <li>{this.props.arreglo.join(", ")}</li>
          <li>{this.props.objeto.nombre + " - " + this.props.objeto.apellido}</li>
          <li>{this.props.arreglo.map(this.props.funcion)}</li>
          <li>{this.props.HTMLElemento}</li>
          <li>{this.props.ComponenteElemento}</li>
        </ul>
      </div>
    )
  }
}
```
### Prop children
En app.js
```jsx
<Componente>
  <h1>Propiedad hijo</h1>
</Componente>
```
En components/Componente.jsx
```jsx
//Componente funcional
export default function Componente(props) {
  return (
    <div>
      {props.children} 
    </div>
  )
}

//Componente de clase
class nombreClass extends Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        {this.props.children}
      </div>
    )
  }
}
```
> Muestra el h1
---
## Estados

Un estado en React es, entonces, un almacén de datos mutable de componentes y que además son autónomos. O sea, el estado pertenece una clase autónoma que cualquiera pueda importar y usar en su aplicación.

```jsx
export default class Estado extends Component {
  constructor(props) {
    super(props);
    this.state = {
      contador: 0 //iniciando estado
    }

    setInterval(() => { //Actualizacion de estado
      this.setState({
        contador: this.state + 1
      })
    }, 1000);
  }
  render() {
    return (
      <div>
        <h1>Estado</h1>
        {/* Imprecion de estado */}
        <p>El contador se actualiza cada 1s {this.state.contador}</p>
      </div>
    )
  }
}
```

### Renderizado Condicional
```jsx
function Login() {
  <button>Login</button>
}
function Logout() {
  <button>Logout</button>
}

export default class Estado extends Component {
  constructor(props) {
    super(props);
    this.state = {
      session: true //session iniciada
    }
  }
  render() {
    return (
      <div>
        <h1>Session</h1>
        {/* Si session existe usar logout para salir, sino login para entrar */}
        {this.state.session ? <Logout /> : <Login />}
      </div>
    )
  }
}
```

### Renderizado de Elementos

En data.json
```json
{
  "Dias":["Lunes","Martes","Miercoles","Jueves","Viernes","Sabado","Domingo"],
  "Meses": ["Enero","Febrero","Marzo","Abril","Mayo","Junio","Julio","Agosto","septiembre","Octubre","Noviembre","Diciembre"],
  "Estaciones": ["Primavera","Verano","Otoño","Invierno"]
}
```
En app.js
```jsx
import data from '../data.json'; //Importacion de data.json

export default class Datos extends Component {
  render() {
    const datos = data; //Guarda el json en una constante
    return (
      <div>
        <h1>datos</h1>
        <h2>Dias de la semana</h2>
        <ol>
          {
            datos.Dias.map((dia, index) => <li key={index}>Dia: {dia} </li>)
          }
        </ol>
        <h2>Meses del año</h2>
        <ol>
          {
            datos.Meses.map((mes, index) => <li key={index}>Dia: {mes} </li>)
          }
        </ol>
        <h2>Estaciones del año</h2>
        <ol>
          {
            datos.Estaciones.map((est, index) => <li key={index}>Dia: {est} </li>)
          }
        </ol>
      </div>
    )
  }
}
```
---
## Eventos

Los eventos permiten desencadenar funciones cuando se realizan acciones por parte de los usuarios.

```jsx
export default class Estado extends Component {
  render() {
    function sumar() {
      console.log("sumando");
    }
    return (
      <div>
        <button onClick={sumar}>+</button>
      </div>
    )
  }
}
```
> El evento Click ejecutara la funcion sumar y en consola se imprimira "sumando".

### Eventos y Estados

```jsx
export default class Estado extends Component {
  constructor(params) {
    super(params);
    this.state = {
      contador: 0
    }
    this.sumar = this.sumar.bind(this); //Enlaza la funcion con la clase
    this.restar = this.restar.bind(this); //Enlaza la funcion con la clase
  }
  sumar() {
    this.setState({
      contador: this.state + 1
    })
  }
  restar() {
    this.setState({
      contador: this.state - 1
    })
  }
  render() {
    return (
      <div>
        <button onClick={this.sumar}>+</button>
        <button onClick={this.restar}>-</button>
      </div>
    )
  }
}
```

### Property Initializers

```jsx
export default class Estado extends Component {
  state = {
    contador: 0
  }
  sumar = () => {
    this.setState({
      contador: this.state + 1
    })
  }
  restar = () => {
    this.setState({
      contador: this.state - 1
    })
  }
  render() {
    return (
      <div>
        <button onClick={this.sumar}>+</button>
        <button onClick={this.restar}>-</button>
      </div>
    )
  }
}
```

### Eventos sintéticos

Eventos disponibles que puede interpretar React.

```jsx
export default class EventoSintetico extends Component {
  datosEvento = (e) => {
    console.log(e); //Datos del evento
    console.log(e.target); //Datos de la etiqueta del evento
  }
  render() {
    return (
      <div>
        <button onClick={this.datosEvento}>Analizar</button>
      </div>
    )
  }
}
```

### Eventos nativos

Eventos en su forma nativa desde Javascript. (util para eventos que aun no soporta la capa sintética de React).

```jsx
export default class EventoNativo extends Component {
  datosEvento = (e) => {
    console.log(e.nativeEvent); //Datos del evento en su forma nativa
    console.log(e.nativeEvent.target); //Datos de la etiqueta del evento en su forma nativa
  }
  render() {
    return (
      <div>
        <button onClick={this.datosEvento}>Analizar</button>
      </div>
    )
  }
}
```

### Eventos personalizados

```jsx
function Boton({ click }) {
  //Desestructuracion
  return <button onClick={click}>Boton de funcion</button>
}

export default class EventoPersonalizado extends Component {
  datosEvento = (e, mensaje) => {
    console.log(e); //Datos del evento
    console.log(e.target); //Datos de la etiqueta del evento
    console.log(mensaje); //mensaje
  }
  render() {
    return (
      <div>
        <Boton click={(e) => {
          this.datosEvento(e, "Parametro extra");
        }} />
      </div>
    )
  }
}
```
---
## Ciclo de vida de los componentes

```jsx
class Hora extends Component {
  constructor(props) {
    super(props);
  }
  componentWillUnmount() {
    console.log(3, "El componente ha sido eliminado del DOM");
  }
  render() {
    return <h3>{this.props.hora}</h3>
  }
}

export default class cicloVida extends Component {
  constructor(props) {
    super(props);
    console.log(0, "El componente se inicializa, aun no esta en el DOM");
    this.state = {
      hora: new Date().toLocaleTimeString(),
      visible: false
    }
    this.temporizador = null;
  }

  componentDidMount() {
    console.log(1, "El componente ya se encuentra en el DOM");
  }

  componentDidUpdate(prevProps, prevState) {
    console.log(2, "El estado de las props del componente a cambiado");
    console.log(prevProps);
    console.log(prevState);
  }

  tiempo = () => {
    this.temporizador = setInterval(() => {
      this.setState({
        hora: new Date().toLocaleTimeString()
      })
    }, 1000);
  }

  activar = () => {
    this.tiempo();
    this.setState({
      visible: true
    })
  }

  desactivar = () => {
    clearInterval(this.temporizador);
    this.setState({
      visible: false
    })
  }

  render() {
    console.log(4, "El componente se dibuja o redibuja en el DOM");
    return (
      <div>
        <h2>Ciclo de vida de los componentes</h2>
        {this.state.visible && <Hora hora={this.state.hora} />}
        <button onClick={this.activar}>Iniciar</button>
        <button onClick={this.desactivar}>Detener</button>
      </div>
    )
  }
}
```
---
## Conexión API REST

```jsx
function Pokemon(props) {
  return (
    <figure>
      <img src={props.avatar} alt={props.nombre} />
      <figcaption>{props.nombre}</figcaption>
    </figure>
  );
}
export default class FetchAPI extends Component {
  state = {
    pokemons: []
  }

  componentDidMount() {
    const url = "https://pokeapi.co/api/v2/pokemon/";
    fetch(url)
      .then(res => res.json())
      .then(json => {
        console.log(json); //Muestra en consola el json optenido
        json.result.forEach(pokemon => {
          fetch(pokemon.url)
            .then(res => res.json())
            .then(json => {
              console.log(json); //Devuelve la informacion de cada pokemon que se encontraba en la url
              let pokemon = {
                id: json.id,
                nombre: json.name,
                avatar: json.sprites.front_default
              }
              let pokemons = [...this.state.pokemons, pokemon];
              this.setState({ pokemons });
            })
        })
      })
  }
  render() {
    return (
      <div>
        <h2>Peticiones asincronas en componentes de clase</h2>
        {this.state.pokemons.map(pokemon => <Pokemon key={pokemon.id} nombre={pokemon.nombre} avatar={pokemon.avatar} />)}
      </div>
    )
  }
}
```
---
## HOOKS

Estos te permiten usar el estado y otras características de React sin escribir una clase.

### useState
```jsx
import React, { useState } from "react";

export default function Estado(props) {
  const [contador, setContador] = useState(0);
  const sumar = () => setContador(contador + 1);
  const restar = () => setContador(contador - 1);
  return (
    <div>
      <h1>{props.titulo}</h1>
      <p>{contador}</p>
      <button onClick={sumar}>Sumar</button>
      <button onClick={restar}>Restar</button>
    </div>
  )
}

Estado.defaultProps = {
  titulo: "Contador de clicks (Estados con Hooks)"
}
```

### useEffect
```jsx
import React, { useEffect } from "react"; //importacion useEffect

export default function CicloVida(props) {
  useEffect(() => {
    console.log("Fase de montaje");
  }, []);

  useEffect(() => {
    console.log("Fase de actualizacion");
  }, [Variable]); //Si se actualiza la variable

  useEffect(() => {
    return () => {
      console.log("Fase de desmontaje");
    }
  });
  return (
    <div>
      <h1>Ciclo de vida con hooks</h1>
    </div>
  )
}
```
Ejemplo:
```jsx
import React, { useState, useEffect } from "react";

function Tiempo(props) {
  useEffect(() => {
    return () => {
      console.log(3, "El componente ha sido eliminado del DOM");
    }
  });
  return <h3>{props.hora}</h3>
}

export default function Cronometro() {
  const [hora, setHora] = useState(new Date().toLocaleTimeString());

  const [visible, setVisible] = useState(false);


  useEffect(() => {
    let temporizador;
    if (visible) {
      temporizador = setInterval(() => {
        setHora(new Date().toLocaleTimeString())
      }, 1000);
    } else {
      clearInterval(temporizador);
    }
    return () => {
      console.log("Face de desmontaje");
      clearInterval(temporizador);
    }
  }, [visible]);

  return (
    <div>
      <h2>Ciclo de vida de los componentes</h2>
      {visible && <Tiempo hora={hora} />}
      <button onClick={() => setVisible(true)}>Iniciar</button>
      <button onClick={() => setVisible(false)}>Detener</button>
    </div>
  )
}
```

### API REST

```jsx
function Pokemon(props) {
  return (
    <figure>
      <img src={props.avatar} alt={props.nombre} />
      <figcaption>{props.nombre}</figcaption>
    </figure>
  );
}
export default function FetchApi() {
  const [pokemons, setPokemons] = useState([]);
  useEffect(() => {
    const obtenerPokemons = async (url) => {
      let res = await fetch(url);
      let json = await res.json();
      json.result.forEach(pokemon => {
        let res = await fetch(pokemon.url);
        let json = await res.json();
        let pokemonI = {
          id: json.id,
          nombre: json.name,
          avatar: json.sprites.front_default
        }
        setPokemons((pokemons) => [...pokemons, pokemonI]);
      })
    }
    obtenerPokemons("https://pokeapi.co/api/v2/pokemon/");
  }, []);

  return (
    <div>
      <h2>Peticiones asincronas en componentes de clase</h2>
      {
        pokemons.map(pokemon => <Pokemon key={pokemon.id} nombre={pokemon.nombre} avatar={pokemon.avatar} />)
      }
    </div>
  )
}
```

### Hooks personalizados

[**Resuelve tus dudas**](https://es.reactjs.org/docs/hooks-custom.html)

Crear una carpeta **hooks** para almacenar los hooks personalizados. En este caso crearemos el archivo **usarFetch.jsx**.

En hooks/usarFetch.jsx
```jsx
import { useState, useEffect } from "react";

export const usarFetch = (url) => {
  const [data, setData] = useState(null);
  const [isPending, setIsPending] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const getData = async (url) => {
      try {
        let res = await fetch(url);
        if (!res.ok) {
          throw {
            err: true,
            status: res.status,
            statusText: !res.statusText ? "Ocurrio un error" : res.statusText
          }
        }
        let data = await res.json();
        setIsPending(false);
        setData(data);
        setError(err: false);
      } catch (err) {
        setIsPending(true);
        setData(null);
        setError(err);
      }
    }
    getData(url);
  }, [url]);
  return { data, isPending, error }
}
```
En component/ImplementacionHook.jsx
```jsx
import { usarFetch } from "./hooks/usarFetch.jsx";

export default function ImplementacionHook() {
  let url = "https://pokeapi.co/api/v2/pokemon/";

  let { data, isPending, error } = usarFetch(url);
  return (
    <>
      <h1>Resultado de peticion</h1>
      <p>{JSON.stringify(isPending)}</p>
      <p>{JSON.stringify(error)}</p>
      <p>{JSON.stringify(data)}</p>
    </>
  )
}
```
---
## Referencias

### Uso en javaScript
```jsx
import React from "react";

export default function Referencias() {
  const displayClick = (e) => {
    const menu = document.querySelector("#menu");
    if (e.target.textContent === "Mostrar") {
      e.target.textContent = "Ocultar";
      menu.style.display = "block";
    } else {
      e.target.textContent = "Mostrar";
      menu.style.display = "none";
    }
  }
  return (
    <>
      <h1>Aparecer y desaparecer menu</h1>
      <button onClick={displayClick}>Mostrar</button>
      <nav id="menu" style={{ display: "none" }}>
        <a href="#">ItemNav</a><br />
        <a href="#">ItemNav</a><br />
        <a href="#">ItemNav</a><br />
        <a href="#">ItemNav</a><br />
      </nav>
    </>
  )
}
```
### Uso en React en componente de clase

```jsx
import React, { createRef, Component } from "react";

export default class Referencias extends Component {
  render() {
    let refMenu = createRef(), refMenuBtn = createRef();

    const displayClick = () => {
      if (refMenuBtn.current.textContent === "Mostrar") {
        refMenuBtn.current.textContent = "Ocultar";
        refMenu.current.style.display = "block";
      } else {
        refMenuBtn.current.textContent = "Mostrar";
        refMenu.current.style.display = "none";
      }
    }
    return (
      <>
        <h1>Aparecer y desaparecer menu</h1>
        <button ref={refMenuBtn} onClick={displayClick}>Mostrar</button>
        <nav ref={refMenu} style={{ display: "none" }}>
          <a href="#">ItemNav</a><br />
          <a href="#">ItemNav</a><br />
          <a href="#">ItemNav</a><br />
          <a href="#">ItemNav</a><br />
        </nav>
      </>
    )
  }
}
```
### Uso en React en componente de función

```jsx
import React, { useRef } from "react";

export default function Referencia() {
  let refMenu = useRef(), refMenuBtn = useRef();

  const displayClick = () => {
    if (refMenuBtn.current.textContent === "Mostrar") {
      refMenuBtn.current.textContent = "Ocultar";
      refMenu.current.style.display = "block";
    } else {
      refMenuBtn.current.textContent = "Mostrar";
      refMenu.current.style.display = "none";
    }
  }
  return (
    <>
      <h1>Aparecer y desaparecer menu</h1>
      <button ref={refMenuBtn} onClick={displayClick}>Mostrar</button>
      <nav ref={refMenu} style={{ display: "none" }}>
        <a href="#">ItemNav</a><br />
        <a href="#">ItemNav</a><br />
        <a href="#">ItemNav</a><br />
        <a href="#">ItemNav</a><br />
      </nav>
    </>
  )
}
```
---
## Formularios

Para formularios pequeños
```jsx
export default function Formulario() {
  const [nombre, setNombre] = useState("");
  const [mascota, setMascota] = useState("");
  const [lenguaje, setLenguaje] = useState("");
  const [terminos, setTerminos] = useState(false);
  return (
    <div>
      <h1>Formulario</h1>
      <form onSubmit={() => alert("El formulario se ha enviado")}>
        <input id='nom' type="text" name='nombre' value={nombre} onChange={(e) => setNombre(e.target.value)} />
        <label htmlFor="nom">Nombre</label>
        <h2>Escoge una mascota</h2>
        <input type="radio" name="mascota" id="gat" value="gato" onChange={(e) => setMascota(e.target.value)} defaultChecked />
        {/* Usar defaultChecked en lugar de checket cuando uses estados */}
        <label htmlFor="gat">Gato:</label>
        <input type="radio" name="mascota" id="per" value="perro" onChange={(e) => setMascota(e.target.value)} />
        <label htmlFor="per">Perro:</label>
        <input type="radio" name="mascota" id="din" value="dinosaurio" onChange={(e) => setMascota(e.target.value)} />
        <label htmlFor="din">Dinosaurio:</label>
        {console.log(mascota)}
        <h2>Escoge un lenguaje de programación</h2>
        <select name="lenguaje" onChange={(e) => setLenguaje(e.target.value)} defaultValue="">
          { /* Usar defaultValue en lugar de selected cuando uses estados */}
          <option value="">---</option>
          <option value="JavaScript">JavaScript</option>
          <option value="PHP">PHP</option>
          <option value="Python">Python</option>
          {console.log(lenguaje)}
        </select>
        <h2>Terminos</h2>
        <label htmlFor="ter">Acepto terminos y condiciones:</label>
        <input type="checkbox" name="terminos" id="ter" onChange={(e) => setTerminos(e.target.checked)} />
        {console.log(terminos)}
        <input type="submit" value="Enviar" />
      </form>
    </div>
  )
}
```
Para formularios grandes
```jsx
export default function Formulario() {
  const [form, setForm] = useState({});

  const manejandoCambio = (e) => {
    setForm({
      ...form,
      [e.target.name]: e.target.value
    })
  }

  return (
    <div>
      <h1>Formulario</h1>
      <form onSubmit={() => alert("El formulario se ha enviado")}>
        <input id='nom' type="text" name='nombre' value={form.nombre} onChange={manejandoCambio} />
        <label htmlFor="nom">Nombre</label>
        <h2>Escoge una mascota</h2>
        <input type="radio" name="mascota" id="gat" value="gato" onChange={manejandoCambio} defaultChecked />
        <label htmlFor="gat">Gato:</label>
        <input type="radio" name="mascota" id="per" value="perro" onChange={manejandoCambio} />
        <label htmlFor="per">Perro:</label>
        <input type="radio" name="mascota" id="din" value="dinosaurio" onChange={manejandoCambio} />
        <label htmlFor="din">Dinosaurio:</label>
        <h2>Escoge un lenguaje de programación</h2>
        <select name="lenguaje" onChange={manejandoCambio} defaultValue="">
          <option value="">---</option>
          <option value="JavaScript">JavaScript</option>
          <option value="PHP">PHP</option>
          <option value="Python">Python</option>
        </select>
        <h2>Terminos</h2>
        <label htmlFor="ter">Acepto terminos y condiciones:</label>
        <input type="checkbox" name="terminos" id="ter" onChange={manejandoCambio} />
        <input type="submit" value="Enviar" />
      </form>
    </div>
  )
}
```
---
## Estilos

### Estilos CSS en React
En Componente.css
```CSS
h3{
  background-color: #ff0;
  margin: 15px;
}
```
En Componente.jsx
```jsx
import "./Componente.css";
```

### Atributo Style
```jsx
export default function Estilos() {
  let myStyles = {
    backgroundColor: "#ff0",
    margin: "15px"
  }
  return (
    <div>
      <h2>Tareas</h2>
      <h3 style={myStyles}>Tarea de fisica</h3>
      <h3 style={{
        backgroundColor: "#f0f",
        margin: "15px"
      }}>Tarea de matematicas</h3>
    </div>
  );
}
```

### Agregando normalize.css

En index.css

```CSS
@import-normalize;
```

### Estilos con modulos
En Componente.module.css

```CSS
.reprobada{
  background-color: "#dc3545"
}
.aprobada{
  background-color: "#198754"
}
```
En Componente.jsx
```jsx
import moduleStyle from "./Componente.module.css";
export default function Estilos() {
  return (
    <div>
      <h2>Tareas</h2>
      <h3 className={moduleStyle.reprobada}>Tarea de fisica</h3>
      <h3 className={moduleStyle.aprobada}>Tarea de matematicas</h3>
    </div>
  );
}
```

### React + SASS

Instalar SASS
```bash
npm i -g sass
```

En Componente.scss
```SCSS
$amarillo: #fd0;
$amarilloOscuro: #fb0;

h3{
  background-color: $amarillo;
  &:hover{
    background-color: $amarilloOscuro;
  }
}
```

En Componente.jsx
```jsx
import "./Componente.scss";
```

### React + Bootstrap

Instalación
```bash
npm i bootstrap
```

En index.js
```jsx
import 'bootstrap/dist/css/bootstrap.min.css';
```
---
## CRUD simple

En App.js
```jsx
import React from 'react';
import { useState } from 'react';
import CRUDForm from './components/CRUDForm';
import CRUDTable from './components/CRUDTable';

let idMas=4;
const datosIniciales = [{
  id: 1,
  nombre: "Tanjiro",
  respiracion: "Solar"
},{
  id: 2,
  nombre: "Zenitsu",
  respiracion: "Rayo"
},{
  id: 3,
  nombre: "Inosuke",
  respiracion: "Bestial"
}]
function App() {
  const [db,setDB] = useState(datosIniciales);
  const [dataToEdit,setDataToEdit] = useState(null);

  const crearPersonaje = (personaje) =>{
    personaje.id = idMas;
    idMas++;
    setDB([...db,personaje]);
  }
  const editarPersonaje = (personaje) =>{
    let nuevosDatos = db.map(el => el.id === personaje.id ? personaje : el);
    setDB(nuevosDatos);
  }
  const eliminarPersonaje = (id) => {
    let confirmar = window.confirm("¿Estas seguro de eliminar el personaje ",id,"?");
    if (confirmar){
      let nuevosDatos = db.filter(el => el.id !== id);
      // Si el elemento coincide con la condicion, se almacena, y si no, se discrimina
      setDB(nuevosDatos);
    }
  }
  return (
    <>
      <h2>CRUDApp</h2>
      <CRUDForm crear={crearPersonaje} editar={editarPersonaje} dte={dataToEdit} sdte={setDataToEdit} />
      <CRUDTable datos={db} eliminar={eliminarPersonaje} sdte={setDataToEdit} />
    </>
  )
}
export default App;
```
En components/CRUDForm.jsx
```jsx
import React, {useState, useEffect} from 'react';

const estructuraForm={
  id: null,
  nombre: "",
  respiracion: ""
}

export default function CRUDForm({crear,editar,dte,sdte}) {
  const [form,setForm] = useState(estructuraForm);

  useEffect(()=>{
    if(dte){
      setForm(dte);
    }else{
      setForm(estructuraForm);
    }
  },[dte])

  const handleChange = (e)=>{
    setForm({
      ...form,
      [e.target.name]: e.target.value
    })
  }
  const handleSubmit = (e) => {
    e.preventDefault();
    if(!form.nombre || !form.respiracion){
      alert("Los campos estan vacios");
      return;
    }
    if(form.id === null) crear(form);
    else editar(form);
    handleReset();
  }
  const handleReset = () => {
    setForm(estructuraForm);
    sdte(null);
  }

  return (
    <div>
      <h3>{dte ? "Editar" : "Agregar"} Personaje</h3>
      <form onSubmit={handleSubmit}>
        <input type="text" name='nombre' placeholder='Nombre del personaje' onChange={handleChange} value={form.nombre} />
        <input type="text" name='respiracion' placeholder='Estilo de respiracion' onChange={handleChange} value={form.respiracion} />
        <input type="submit" value="Enviar" />
        <input type="reset" value="Limpiar" onClick={handleReset}/>
      </form>
    </div>
  )
}
```
En components/CRUDTable.jsx
```jsx
import React from 'react';

export default function CRUDTable({datos, eliminar, sdte}) {
  return (
    <div>
      <h3>Tabla de datos</h3>
      <table>
        <thead>
          <tr>
            <th >Nombre</th>
            <th >Respiracion</th>
            <th >Acciones</th>
          </tr>
        </thead>
        <tbody>
        {
          datos.length > 0 ? ( 
            datos.map(elem => 
              <tr key={elem.id}>
                <td >{elem.nombre}</td>
                <td >{elem.respiracion}</td>
                <td >
                  <button onClick={()=> sdte(elem)}> Actualizar </button>
                  <button onClick={()=> eliminar(elem.id)}> Eliminar </button>
                </td>
              </tr>
            )
          ):(
              <tr>
                <td colSpan="3">No hay datos que mostrar</td>
              </tr>
          )
        }
        </tbody>
      </table>
    </div>
  )
}
```

## CRUD API con json server

Se reutilizaran los componentes **CRUDForm y CRUDTable**.

Instalacion de json-server
```bash
npm i -g json-server
```
Correr el servidor con un script
```json
"scripts": {
    "api-falsa": "json-server --watch src/API/data.json --port 4000"
  }
```

En API/datos.json
```json
{
  "Espadachines": [{
      "id": 1,
      "nombre": "Tanjiro",
      "respiracion": "Solar"
    },
    {
      "id": 2,
      "nombre": "Zenitsu",
      "respiracion": "Rayo"
    },
    {
      "id": 3,
      "nombre": "Inosuke",
      "respiracion": "Bestial"
    }]
}
```

En helpers/helpHttp.js
```js
export const helpHttp = () => {
  const customFetch = (ruta,opt) => {
    const defaultHeaders = {
      accept: "application/json"
    }
    // Sirve para anular la peticion 
    const controller = new AbortController();
    opt.signal = controller.signal;
    // https://developer.mozilla.org/en-US/docs/Web/API/AbortController

    opt.method = opt.method || "GET";

    // Por si el usuario brinda más cabeceras
    opt.headers = opt.headers
      ? {...defaultHeaders,...opt.headers}
      : defaultHeaders;

    // Si manda o no un json
    opt.body = JSON.stringify(opt.body) || false;
    if(!opt.body) delete opt.body;

    // console.log(opt);

    // Anula la petición
    setTimeout(()=> controller.abort(),3000);

    return fetch(ruta,opt).then(res=>res.ok?res.json():Promise.reject({
      err: true,
      status: res.status || "00",
      statusText: res.statusText || "Ocurrio un error"
    })).catch(err=>err);
  }

  const get = (url,options={}) => customFetch(url,options);
  const post = (url, options = {}) => {
    options.method= "POST";
    return customFetch(url, options);
  }
  const put = (url, options = {}) => {
    options.method = "PUT";
    return customFetch(url, options);
  }
  const del = (url, options = {}) => {
    options.method = "DELETE";
    return customFetch(url, options);
  }
  return {
    get,
    post,
    put,
    del
  }
}
```

En App.jsx
```jsx
import React from 'react';
import { useState, useEffect } from 'react';
import { helpHttp } from '../helpers/helpHttp';
import CRUDForm from './components/CRUDForm';
import CRUDTable from './components/CRUDTable';
import Loader from './components/Loader';
import Message from './components/Message';

function App() {
  const [db, setDB] = useState(null);
  const [dataToEdit, setDataToEdit] = useState(null);
  const [error,setError] = useState(null);
  const [loading, setLoading] = useState(false);

  let api = helpHttp();
  let url = "http://localhost:4000/Espadachines";

  useEffect(()=>{
    setLoading(true);
    helpHttp().get(url).then(res=>{
      if(!res.err){
        setDB(res);
        setError(null);
      }else{
        setDB(null);
        setError(res);
      }
      setLoading(false);
    });
  },[url]); 
  const crearPersonaje = (personaje) => {
    personaje.id = db[db.length-1].id + 1;
    let opciones = {
      body: personaje,
      headers: {"content-type": "application/json"}
    }
    api.post(url,opciones).then(res=>{
      if(!res.err){
        setDB([...db, res])
      }else{
        setError(res);
      }
    })
  }
  const editarPersonaje = (personaje) => {
    let ruta=`${url}/${personaje.id}`;

    let opciones = {
      body: personaje,
      headers: { "content-type": "application/json" }
    }
    api.put(ruta, opciones).then(res => {
      if (!res.err) {
        let nuevosDatos = db.map(el => el.id === personaje.id ? personaje : el);
        setDB(nuevosDatos);
      } else {
        setError(res);
      }
    })
  }
  const eliminarPersonaje = (id) => {
    let confirmar = window.confirm("¿Estas seguro de eliminar el personaje ", id, "?");
    if (confirmar) {
      let ruta = `${url}/${id}`;
      let opciones = {
        headers: { "content-type": "application/json" }
      }
      api.del(ruta,opciones).then(res=>{
        if (!res.err) {
          let nuevosDatos = db.filter(el => el.id !== id);
          // Si el elemento coincide con la condicion, se almacena, y si no, se discrimina
          setDB(nuevosDatos);
        } else {
          setError(res);
        }
      })
    }else{
      return;
    }
  }
  return (
    <>
      <h2>APIcrud</h2>
      <CRUDForm crear={crearPersonaje} editar={editarPersonaje} dte={dataToEdit} sdte={setDataToEdit} />
      {loading && <Loader/>}
      {error && <Message msg={`Error ${error.status}: ${error.statusText}`}/>}
      {db && <CRUDTable datos={db} eliminar={eliminarPersonaje} sdte={setDataToEdit} />}
    </>
  )
}
export default App;
```

En component/Loader.jsx
```jsx
import React from 'react';

export default function Loader() {
  return (
    <h3>Loading...</h3>
  )
}
```
En component/Message.jsx
```jsx
import React from 'react';

export default function Message({msg}) {
  return (
    <div>
      <h3>Mensaje</h3>
      <p>{msg}</p>
    </div>
  )
}

```
---
## CRUD API rest con async-await

Reutilizaremos los componentes **Loader y Message**, y tambien helpHttp.js

En App.js
```js
import React, {useState, useEffect} from 'react';
import { helpHttp } from '../helpers/helpHttp';
import Loader from './components/Loader';
import SongDetalls from './components/SongDetalls';
import SongForm from './components/SongForm';

function App() {
  const [search,setSearch] = useState(null);
  const [lyric, setLyric] = useState(null);
  const [bio,setBio] = useState(null);
  const [loading,setLoading] = useState(false);

  useEffect(()=>{
    if (search === null) return;
    const fetchData = async ()=> {
      const {artist,song} = search;
      const artistURL = `https://www.theaudiodb.com/api/v1/json/2/search.php?s=${artist}`;
      const songURL = `https://api.lyrics.ovh/v1/${artist}/${song}`;
      setLoading(true);
      const [artistRes,songRes]=await Promise.all([helpHttp().get(artistURL),helpHttp().get(songURL)]);
      setBio(artistRes);
      setLyric(songRes);
      setLoading(false);
      console.log(artistRes,songRes);
    }
    fetchData();
  },[search]);

  const handleSearch = (data) => {
    setSearch(data);
    console.log(bio);
  }
  return (
    <div>
      <h2>SongSearch</h2>
      <SongForm formBuscador={handleSearch}/>
      {search && !loading && <SongDetalls busqueda={search} biog={bio} letra={lyric} />}
      {loading && <Loader/>}
    </div>
  )
}
export default App;
```

En components/SongForm.jsx
```jsx
import React, {useState} from 'react';

const formInicial={
  artist: "",
  song: ""
}

export default function SongForm({formBuscador}) {
  const [form,setForm]=useState(formInicial);

  const handleChange = (e) =>{
    setForm({
      ...form,
      [e.target.name]: e.target.value
    })
  }

  const handleSubmit = e => {
    e.preventDefault();

    if(!form.artist || !form.song){
      alert("Los campos estan incompletos");
      return;
    }

    formBuscador(form);
    setForm(formInicial);
  }

  return (
    <div>
      <h3>Buscar Artista y Canción</h3>
      <form onSubmit={handleSubmit}>
        <input type="text" name="artist" placeholder='Teclea el artista' value={form.artist} onChange={handleChange} />
        <input type="text" name="song" placeholder='Teclea la canción' value={form.song} onChange={handleChange} />
        <input type="submit" value="Enviar" />
      </form>
    </div>
  )
}
```

En components/SongDetalls.jsx
```jsx
import React from 'react';
import Message from './components/Message';

export default function SongDetalls({busqueda,biog,letra}) {
  if(!biog || !letra) return null;
  return (
    <div>
      <h3>Información</h3>
      {
        letra.err || letra.name === "AbortError" ? <Message msg={`Error: La cancion ${busqueda.song} no existe o no esta registrada.`}/> : (
          <section>
            <h4>Información de la canción</h4>
            <h5>{busqueda.song}</h5>
            <blockquote style={{whiteSpace: "pre-wrap"}}>{letra.lyrics}</blockquote>
          </section>
        )
      }
      {
        biog.artists ? (
          <section>
            <h4>Información del artista</h4>
            <h5>{biog.artists[0].strArtist}</h5>
            <img src={biog.artists[0].strArtistThumb} alt={biog.artists[0].strArtist} />
            <p>{biog.artists[0].intBornYear} - {biog.artists[0].intDiedYear || "Presente"}</p>
            <p>{biog.artists[0].strCountry}</p>
            <p>{biog.artists[0].strGenre} - {biog.artists[0].strStyle}</p>
            <a href={`http://${biog.artists[0].strWebsite}`} target="_blank" rel='noreferrer'>Sitio web oficial</a>
            <p>{biog.artists[0].strBiographyEN}</p>
          </section>
        ) : <Message msg={`Error: El artista ${busqueda.artist} no existe o no esta registrado.`} /> 
      }
    </div>
  )
}
```
## Portales
En index.html
```html
<body>
  <noscript>You need to enable JavaScript to run this app.</noscript>
  <div id="model"></div>
  <!-- Div portal -->
  <div id="root"></div>
<body>
```
En ModalPortal.jsx
```jsx
import React from 'react';
import ReactDOM from 'react-dom';

export default function ModalPortal() {
  return ReactDOM.createPortal (
    <div>
      <h1>Contenido</h1>
    </div>,document.getElementById("model");
  )
}
```
> El contenido se asigna al nuevo div.model
---
## React-Router
Libreria para crear rutas en react.

Instalación
```bash
npm i react-router-dom
```

### Estructura basica
```jsx
import {BrowserRouter,NavLink,Routes,Route} from "react-router-dom"; // Importacion de los componentes de react router
import Home from './pages/Home';
import About from './pages/About';
// Importacion de los componentes

<BrowserRouter>
  <header>
    <NavLink to={'/'}>Home</NavLink>
    <NavLink to={'/about'}>About</NavLink>
  </header>
  <Routes>
    <Route path="/" element={<Home/>}/>
    <Route path="/about" element={<About/>}/>
  </Routes>
</BrowserRouter>
```
* **BrowserRouter:** Envuelve todo el contenido de las rutas.
* **Routes:** Asigna unicamente una ruta por consulta. Evita que dos rutas o más aparescan al mismo tiempo.
* **Route:** En el se asigna el nombre de la ruta y el componente que representara la pagina de navegación.
* **NavLink:** Se utiliza para realizar el menú de navegación.

### Ruta de error 404
```jsx
<Route path="*" element={<NotFoundPage/>}/>
```
> Tiene que ser la ultima ruta

### Diferencia entre NavLink y Link
```jsx
<NavLink activeclassname="active" to="/">Home</NavLink>
// Permite dar estilos css al estar seleccionada
<Link activeclassname="active" to="/">Home</Link>
// Solo tiene su funcion predeterminada
```

### Redireccionar ruta
```jsx
import { Navigate } from 'react-router-dom';
<Route path="/acerca" element={<Navigate to="/about" />} />
```

### Rutas dinamicas

```jsx
import Usuario from './pages/Usuario';
<Route path="/usuario/:id/:nombre" element={<Usuario/>}/>
```

**Hook useParams**

```jsx
import React from 'react';
import {useParams} from 'react-router-dom';

export default function Usuario() {
  const [nombre] = useParams();
  return 
  <div>
    <p>Bienvenido {nombre}</p>
  </div>
}
```
> Los parametros ingresados en la ruta Usuarios se pueden desestructurar con useParams y utilizar sus valores como sea comveniente.

**Hooks useLocation y useNavigate**
```jsx
import { useLocation, useNavigate } from 'react-router-dom';

export default function Productos() {
  // URL + ?inicio=1&fin=20
  const limit = 20;
  let {search} = useLocation(); //Localizacion de la ruta
  let query = new URLSearchParams(search); //Busca los parametros de la ruta
  let start = parseInt(query.get("inicio")) || 1;
  let end = parseInt(query.get("fin")) || limit;
  // Almacena las variables de la URL inicio=1 fin=20

  let navigate = useNavigate();
  // Desde el punto donde se invoca, cambia la ruta
  const handlePrev = () => {
    navigate(`?inicio=${start - limit}&fin=${end - limit}`);
  }
  const handleNext = () => {
    navigate(`?inicio=${start + limit}&fin=${end + limit}`);
  }
  return (
    <div>
      <h2>Productos</h2>
      <p>Productos del {start} al {end}</p>
      {start>limit && <button onClick={handlePrev} >Anterior</button>}
      <button onClick={handleNext} >Siguiente</button>
    </div>
  )
}
```

### Rutas Anidadas
En App.jsx dentro del Rout raiz
```jsx
<Route path='rutas/' element={<RutaAnidada/>} >
  <Route path='ruta0' element={<Ruta0 />} />
  <Route path='ruta1/' element={<Ruta1 />}>
    <Route path='ruta11' element={<Ruta1s1 />} />
    <Route path='*' element={<NotFoundPage />} />
  </Route>
  <Route path='*' element={<NotFoundPage />} />
</Route>
```
Los NavLinks de las rutas raiz no deben contener "/"
```jsx
<NavLink className="item" to='ruta0'>Ruta0.0</NavLink>
<Outlet/>
//Hace referencia a los hijos de las rutas raiz
```
### Rutas Privadas
```jsx
<Route path='pagePrin' element={registrado ? <PagePrin /> : <Navigate to={'/login'}/>} />
```
> Si el usuario esta registrado lo envia a la pagina principal, sino, lo redirecciona al login

### HashRouter
Se coloca en lugar del BrowserRouter para resolver el problemas de los enlaces en una SPA.
```jsx
import { HashRouter } from 'react-router-dom';
<HashRouter>
{
  // Contenido
}
</HashRouter>
```
---
## Memorización
Solo usar cuando el renderizado constante gaste más recursos que la misma memorización.
### Memo React
Sirve para memorizar componentes completos y evita renderizados inecesarios.

**Componente Padre**
```jsx
import React, { useState} from 'react';
import ContadorHijo from './ContadorHijo';

export default function Contador() {
  const [clicks, setClicks] = useState(0);

  const sumar = () => setClicks(clicks + 1);
  const restar = () => setClicks(clicks - 1);

  return (
    <div>
      <h2>clicks</h2>
      <button onClick={sumar}>sumar</button>
      <button onClick={restar}>restar</button><br />
      <ContadorHijo valor={clicks} sumar={sumar} restar={restar} />
    </div>
  )
}
```
Componente hijo
```jsx
import React, {memo} from 'react';
//Importacion de memo
function ContadorHijo() {
  console.log("Renderizados");
  return (
    <div >
      <h2>Componente hijo</h2>
    </div>
  )
}
export default memo(ContadorHijo); //memorizacion
```

### useCallback
Sirve para memorizar funciones. Su uso es conveniente cuando estas pasan como atributos a los componentes hijos y evitan que los componentes hijos se rendericen.
```jsx
import React, {useCallback} from 'react';
// Importacion de useCallback
const sumar = useCallback(() => setClicks(clicks + 1),[clicks]);
const restar = useCallback(() => setClicks(clicks - 1), [clicks]);
//En el componente hijo
<ContadorHijo sumar={sumar} restar={restar} />
```
> Cada vez que cambie el valor de clicks, este hoock volvera a memorizar la funcion.
### useMemo
Se usa para memorizar procesos muy tardados.
```jsx
import React, {useMemo} from 'react';
const superNum = useMemo(()=>{
    let numero=0;
    for (let i = 0; i < 1000000000; i++) {
      numero++;
    }
    return numero;
  },[]);
```
> Este hook puede o no depender del cambio de una variable para rememorizar
---
## Context
Permite distribuir valores o funciones por todos los componentes que sean necesarios sin importar su localizacion en el arbol del DOM.

En context/ColorContext.js
```jsx
import { createContext, useState } from 'react';

const ColorContext = createContext(); //Creación de contexto
const colorInicial = "dia";

 //Componente que brindara los datos a todas las ramas del DOM
function ColorProvider({children}) { //Elementos hijos
  const [color,setColor]=useState(colorInicial);
  const manejandoColor = (e)=> {
    if (e.target.value === "dia") setColor("dia")
    else setColor("noche");
  }
  const data = {color,manejandoColor};
  return <ColorContext.Provider value={data} > {children} </ColorContext.Provider>
}
// Exportacion del contexto y el componente del context
export {ColorProvider};
export default ColorContext;
```

En App.js
```jsx
import { ColorProvider } from './context/ColorContext';

//Envuelve todos los componentes que quieras conciderar
function App() {
  return (
    <div className="App">
      <ColorProvider>
        <Componente/>
        <Componente2/>
        <Componente3/>
      </ColorProvider>
    </div>
  );
}
```

En cualquier componente envuelto
```jsx
import React, { useContext } from 'react';
import ColorContext from '../context/ColorContext';

export default function Componente() {
  //Utiliza el context y desestructura los valores que vayas a utilizar
  const { color, manejandoColor } = useContext(ColorContext);

  // Utiliza los valores
  return (
    <header className={color}>
      <h2>Selecciona el color</h2>
      <label htmlFor="blanco">blanco</label>
      <input type="radio" name="color" id="blanco" onClick={manejandoColor} value="dia" defaultChecked />
      <label htmlFor="negro">negro</label>
      <input type="radio" name="color" id="negro" onClick={manejandoColor} value="noche" />
    </header>
  )
}
```
> Utiliza solo cuando los tengas que pasar valores a componentes nietos en adelante.