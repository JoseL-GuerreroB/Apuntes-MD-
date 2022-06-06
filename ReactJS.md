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

class nombreClass extends Component{
    render(){
        return(
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
            <li>{props.objeto.nombre+" - "+props.objeto.apellido}</li>
            <li>{props.arreglo.map(props.funcion)}</li>
            <li>{props.HTMLElemento}</li>
            <li>{props.ComponenteElemento}</li>
          </ul>
        </div>
    )
}

//Componente de clase
class nombreClass extends Component{
  constructor(props){
    super(props);
  }
    render(){
      return(
        <div>
          <h1>Tipos de propiedades</h1>
          <ul>
            <li>{this.props.cadena}</li>
              <li>{this.props.numero}</li>
              <li>{this.props.booleano}</li>
              <li>{this.props.arreglo.join(", ")}</li>
              <li>{this.props.objeto.nombre+" - "+this.props.objeto.apellido}</li>
              <li>{this.props.arreglo.map(this.props.funcion)}</li>
              <li>{this.props.HTMLElemento}</li>
              <li>{this.props.ComponenteElemento}</li>      
          </ul>            
        </div>    
      )  
    }
}
```
---
## Estados

Un estado en React es, entonces, un almacén de datos mutable de componentes y que además son autónomos. O sea, el estado pertenece una clase autónoma que cualquiera pueda importar y usar en su aplicación.

```jsx
export default class Estado extends Component{
    constructor(props){
        super(props);
        this.state={
            contador: 0 //iniciando estado
        }

        setInterval(()=>{ //Actualizacion de estado
            this.setState({
                contador: this.state + 1
            })
        },1000);
    }
    render(){
        return(
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

export default class Estado extends Component{
    constructor(props){
        super(props);
        this.state={
            session: true //session iniciada
        }
    }
    render(){
        return(
            <div>
                <h1>Session</h1>
                {/* Si session existe usar logout para salir, sino login para entrar */}
                {this.state.session ? <Logout/> : <Login/>}
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

export default class Datos extends Component{
    render(){
        const datos = data; //Guarda el json en una constante
        return(
            <div>
                <h1>datos</h1>
                <h2>Dias de la semana</h2>
                <ol>
                    {
                        datos.Dias.map((dia,index) => <li key={index}>Dia: {dia} </li>)
                    }
                </ol>
                <h2>Meses del año</h2>
                <ol>
                    {
                        datos.Meses.map((mes,index) => <li key={index}>Dia: {mes} </li>)
                    }
                </ol>
                <h2>Estaciones del año</h2>
                <ol>
                    {
                        datos.Estaciones.map((est,index) => <li key={index}>Dia: {est} </li>)
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
export default class Estado extends Component{
    render(){
    function sumar(){
        console.log("sumando");
    }
        return(
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
export default class Estado extends Component{
    constructor(params){
        super(params);
        this.state={
            contador: 0
        }
        this.sumar = this.sumar.bind(this); //Enlaza la funcion con la clase
        this.restar = this.restar.bind(this); //Enlaza la funcion con la clase
    }
    sumar(){
        this.setState({
            contador: this.state + 1
        })
    }
    restar(){
        this.setState({
            contador: this.state - 1
        })
    }
    render(){
        return(
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
export default class Estado extends Component{
    state={
        contador: 0
    }
    sumar=()=>{
        this.setState({
            contador: this.state + 1
        })
    }
    restar=()=>{
        this.setState({
            contador: this.state - 1
        })
    }
    render(){
        return(
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
export default class EventoSintetico extends Component{
    datosEvento = (e)=>{
        console.log(e); //Datos del evento
        console.log(e.target); //Datos de la etiqueta del evento
    }
    render(){
        return(
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
export default class EventoNativo extends Component{
    datosEvento = (e)=>{
        console.log(e.nativeEvent); //Datos del evento en su forma nativa
        console.log(e.nativeEvent.target); //Datos de la etiqueta del evento en su forma nativa
    }
    render(){
        return(
            <div>
                <button onClick={this.datosEvento}>Analizar</button>
            </div>
        )
    }
}
```

### Eventos personalizados

```jsx
function Boton({click}) {
    //Desestructuracion
    return <button onClick={click}>Boton de funcion</button>
}

export default class EventoPersonalizado extends Component{
    datosEvento = (e,mensaje)=>{
        console.log(e); //Datos del evento
        console.log(e.target); //Datos de la etiqueta del evento
        console.log(mensaje); //mensaje
    }
    render(){
        return(
            <div>
                <Boton click={(e)=>{
                    this.datosEvento(e,"Parametro extra");
                }}/>
            </div>
        )
    }
}
```
---
## Ciclo de vida de los componentes

```jsx
class Hora extends Component{
    constructor(props){
        super(props);
    }
    componentWillUnmount(){
        console.log(3,"El componente ha sido eliminado del DOM");
    }
    render(){
        return <h3>{this.props.hora}</h3>
    }
}

export default class cicloVida extends Component{
    constructor(props){
        super(props);
        console.log(0,"El componente se inicializa, aun no esta en el DOM");
        this.state={
            hora: new Date().toLocaleTimeString(),
            visible: false
        }
        this.temporizador=null;
    }

    componentDidMount(){
        console.log(1,"El componente ya se encuentra en el DOM");
    }

    componentDidUpdate(prevProps,prevState){
        console.log(2,"El estado de las props del componente a cambiado");
        console.log(prevProps);
        console.log(prevState);
    }

    tiempo = ()=>{
        this.temporizador = setInterval(()=>{
            this.setState({
                hora: new Date().toLocaleTimeString()
            })
        },1000);
    }

    activar = ()=>{
        this.tiempo();
        this.setState({
            visible: true
        })
    }

    desactivar = ()=>{
        clearInterval(this.temporizador);
        this.setState({
            visible: false
        })
    }

    render(){
        console.log(4,"El componente se dibuja o redibuja en el DOM");
        return(
            <div>
                <h2>Ciclo de vida de los componentes</h2>
                {this.state.visible && <Hora hora={this.state.hora}/>}
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
function Pokemon(props){
    return(
        <figure>
            <img src={props.avatar} alt={props.nombre}/>
            <figcaption>{props.nombre}</figcaption>
        </figure>
    );
}
export default class FetchAPI extends Component{
    state={
        pokemons: []
    }

    componentDidMount(){
        const url = "https://pokeapi.co/api/v2/pokemon/";
        fetch(url)
            .then(res => res.json())
            .then(json =>{
                console.log(json); //Muestra en consola el json optenido
                json.result.forEach(pokemon =>{
                    fetch(pokemon.url)
                        .then(res => res.json())
                        .then(json => {
                            console.log(json); //Devuelve la informacion de cada pokemon que se encontraba en la url
                            let pokemon = {
                                id: json.id,
                                nombre: json.name,
                                avatar: json.sprites.front_default
                            }
                            let pokemons = [...this.state.pokemons,pokemon];
                            this.setState({pokemons});
                        })
                })
            })
    }
    render(){
        return(
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
import React, {useState} from "react";

export default function Estado(props){
    const [contador,setContador]=useState(0);
    const sumar = ()=> setContador(contador + 1);
    const restar = ()=> setContador(contador - 1);
    return(
        <div>
            <h1>{props.titulo}</h1>
            <p>{contador}</p>
            <button onClick={sumar}>Sumar</button>
            <button onClick={restar}>Restar</button>
        </div>
    )
}

Estado.defaultProps={
    titulo: "Contador de clicks (Estados con Hooks)"
}
```

### useEffect
```jsx
import React, {useEffect} from "react"; //importacion useEffect

export default function CicloVida(props){
    useEffect(()=>{
        console.log("Fase de montaje");
    },[]);

    useEffect(()=>{
        console.log("Fase de actualizacion");
    },[Variable]); //Si se actualiza la variable

    useEffect(()=>{
        return ()=>{
            console.log("Fase de desmontaje");
        }
    });
    return(
        <div>
            <h1>Ciclo de vida con hooks</h1>
        </div>
    )
}
```
Ejemplo:
```jsx
import React, {useEstate, useEfect} from "react";

function Tiempo(props){
    useEffect(()=>{
        return ()=>{
            console.log(3,"El componente ha sido eliminado del DOM");
        } 
    });
    return <h3>{props.hora}</h3>
}

export default function Cronometro(){
    const [hora,setHora]=useState(new Date().toLocaleTimeString());

    const [visible,setVisible]=useState(false);


    useEffect(()=>{
        let temporizador;
        if(visible){
            temporizador = setInterval(()=>{
                setHora(new Date().toLocaleTimeString())
            },1000);
        }else{
            clearInterval(temporizador);
        }
        return ()=>{
            console.log("Face de desmontaje");
            clearInterval(temporizador);
        }
    },[visible]);

    return(
        <div>
            <h2>Ciclo de vida de los componentes</h2>
            {visible && <Tiempo hora={hora}/>}
            <button onClick={()=> setVisible(true)}>Iniciar</button>
            <button onClick={()=> setVisible(false)}>Detener</button>
        </div>
    )
}
```

### API REST

```jsx
function Pokemon(props){
    return(
        <figure>
            <img src={props.avatar} alt={props.nombre}/>
            <figcaption>{props.nombre}</figcaption>
        </figure>
    );
}
export default function FetchApi(){
    const [pokemons,setPokemons]=useState([]);
    useEffect(()=>{
        const obtenerPokemons = async (url)=>{
            let res = await fetch(url);
            let json = await res.json();
            json.result.forEach(pokemon =>{
                let res = await fetch(pokemon.url);
                let json = await res.json();
                let pokemonI = {
                    id: json.id,
                    nombre: json.name,
                    avatar: json.sprites.front_default
                }
                setPokemons((pokemons)=>[...pokemons,pokemonI]);
            })
        }
        obtenerPokemons("https://pokeapi.co/api/v2/pokemon/");
    },[]);

    return(
        <div>
            <h2>Peticiones asincronas en componentes de clase</h2>
            {
                pokemons.map(pokemon => <Pokemon key={pokemon.id} nombre={pokemon.nombre} avatar={pokemon.avatar} />)
            }
        </div>
    )
}
```