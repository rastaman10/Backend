![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png  "logotipo de The Bridge")
# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)
### JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

## Clase 43

### Redux

![react redux](../../assets/react/clase43/reactredux.jpg)

Redux es una libreria externa (no pertenece a react) que se define como un contenedor predecible del estado de aplicaciones JavaScript.

Esta basado en la arquitectura Flux de Facebook aunque mas sencilla.


![Comparing with Redux and without Redux](../../assets/react/clase43//Bildschirmfoto-2017-12-01-um-08.53.32.png)

![Schema Redux flow](../../assets/react/clase43/Bildschirmfoto-2017-12-01-um-08.56.48.png)

![ReduxDataFlowDiagram](../../assets/react/clase43/ReduxDataFlowDiagram.gif)

Recursos
- [understanding-redux-the-worlds-easiest-guide-to-beginning-redux](https://www.freecodecamp.org/news/understanding-redux-the-worlds-easiest-guide-to-beginning-redux-c695f45546f6/)
- [Tutorial Redux](https://www.valentinog.com/blog/redux/)
- [Vídeo tutorial Redux](https://www.youtube.com/playlist?list=PLC3y8-rFHvwheJHvseC3I0HuYI2f46oAK)
- [Ejemplos Redux](https://redux.js.org/introduction/examples)
- [Ejemplo de carrito](https://medium.com/@ayabellazreg/make-a-simple-shopping-cart-app-using-react-redux-1-3-fefde93e80c7)
- [react-redux](https://react-redux.js.org/)
- [Redux | introducción](https://redux.js.org/introduction/getting-started)


Estado:
- El estado se define como un simple objeto
- El estado es global
- El estado no se puede modificar (se genera uno nuevo a partir del anterior a través de acciones)

Principios de Redux:
- Única fuente de la verdad
- Estado inmutable (de solo lectura)
- Los cambios se realizan con funciones puras (reducers)

### Actions

Las Actions son objetos de Javascript que tienen una propiedad "type" que indica el tipo de acción y pueden contener otras propiedades que sirven como 'payload' para poder realizar la acción

```js
{
    type: "ADD_TODO",
    text: "Aprender a tocar el piano"
}
```

### Action Creators

Funciones puras que devuelven Actions. No son obligatorias de usar pero son muy útiles poque de esta manera evitamos escribir mal el nombre de los tipos y los objetos a mano.

```js
function addTodo(text){
 return {
        type: "ADD_TODO",
        payload: {
            text
        }
    }
}
```

### Reducers

Función pura que recibe el estado anterior y la acción, y a partir de ellas, crea un nuevo estado de la aplicación.

```js
(previousState, action) => nextState
```

Ejemplo de un reducer.
```js
function todoApp(state = initialState, action){
  switch (action.type) {
    case ADD_TODO:
      return Object.assign({}, state, {
        todos: [
          ...state.todos,
          {
            text: action.text,
            completed: false
          }
        ]
      })
      default:
        return state
  }
} 
```

### Store

Almacena el estado global de la aplicación.
Permite que el estado sea leído, que te puedas suscribir a sus cambios y que envíes acciones para crear un nuevo estado global.

```js
import { createStore } from 'redux'
import reducers from './reducers'

const store = createStore(reducers)
```


Ejemplo de un store
```js
import { createStore } from 'redux'

function todos(state = [], action){
  switch (action.type) {
    case ADD_TODO:
      return state.concat([action.text])
    default:
        return state
  }
} 

const store = createStore(todos)

export default store
```

Después para obtener el state actual podemos hacerlo de la siguiente forma:

```js
import store from './store'

console.log(store.getState());
```

Suscribirse a cambios de la store:

```js
import store from './store'
// al suscribirse a la store, te devuelve una funcion para ejecutarla y desuscribirse mas tarde
const unsubscribe = store.subscribe(() => {
    // esta funcion se ejecuta cuando haya cambios en el state
    console.log(store.getState());

    // ahora podemos actualizar nuestra app con la nueva info
    const { usuario } = store.getState()
    document.getElementById('usuario').innerHTML = usuario
});

// ahora podemos usar el método unsuscribe para eliminar la suscriptión a la store
document.getElementById('cerrar').addEventListener('click', () => unsubscribe())

```

Para enviar Actions para actualizar la store debemos llamar al método 'dispatch' de la store:

```js
import store from './store'

store.dispatch({
    type: 'ADD_TODO',
    text: 'Aprender a desarrollar videojuegos con Unity'
})
```

también podriamos hacer esto usando actions creators:

actions.js
```js
export function addTodo(text){
 return {
        type: "ADD_TODO",
        payload: {
            text
        }
    }
}
```

```js
import store from './store'
import { addTodo } from './actions'

store.dispatch(addTodo('Aprender a desarrollar videojuegos con Unity'))
```


### Redux en React

Separaremos los componentes en dos clases:

- Componentes presentacionales: Estos reflejarán los cambios en la interfaz

- Contenedores: Se ocupan de la lógica y la gestión del estado

#### Libreria react-redux

Instalaremos la libreria react-redux, esta librería nos facilita la conexión de React con Redux.

```
npm install --save redux react-redux
```

Esta librería nos facilita varias cosas:

- Evitar la gestión manual de tener que pasar la store a todos nuestros componentes

- Leer el estado global desde cualquier lugar de nuestro árbol de elementos

- Llamar a acciones desde cualquier componente

#### Patrón Contenedor-Contenido


|   | Componentes de Presentación  | Componentes Contenedores  |
|---|---|---|
| Propósito  | Como se ven las cosas (markup,stilos)  | Como funcionan las cosas (búsqueda de datos, actualizaciones de estado)  |
| Pertinente a Redux  | No  | Si  |
| Para leer datos  | Lee datos de las props  | Se suscribe al estado en Redux  |
| Para manipular datos  | Invoca llamada de retorno (callback) desde las props  | Envia acciones a Redux  |
| Son escritas  | Manualmente  | Usualmente generados por React Redux  |


react-redux nos proporciona dos utilidades para crear la conexión entre Redux y nuestra aplicación de React:

'connect()' y 'Provider'

#### connect

Sirve para conectar un componente de React a la store de Redux. Devuelve una función que recibe como parámetro el componente que queremos conectar.

```js
connect([mapStateToProps], [mapDispatchToProps])
```

#### mapStateToProps

Función que devuelve el trozo de estado al que queremos que el componente se suscriba. Es opcional. Si no se indica, el componente no se suscribirá a la store

recibe dos parámetros:
- [state] el estado global actual
- [ownProps] las props que recibe el componente

```js
const mapStateToProp = (state, ownProps) => {
    // en este caso, el componente recibirá counter como prop
    return {counter: state.counter}
}
```

#### mapDispatchToProps

Función que devuelve las accionees que podrá despachar nuestro componente a la store. Es la única forma cómo podremos generar una actualización del state de la store.

recibe dos parámetros:
- [dispatch] método para llamar a las actions
- [ownProps] las props que ha recibido el componente

```js
const  mapDispatchToProp = (dispatch, ownProps) => {
    // nombre de las props para ejecutar y llamar a una action
    return {
        increment: () => dispatch({ type: 'INCREMENT' }),
        decrement: () => dispatch({ type: 'DECREMENT' }),
        reset: () => dispatch({ type: 'RESET' }),
    }
}
```

Una vez que tenemos todo lo necesario montado ahora ya podemos llamar al método connect pasando como parametros estos dos métodos creados antes.

```js
const createConnect = connect(mapStateToProps, mapDispatchToProps)

const ComponentWithConnectionToRedux = createConnect(Counter)

export default ComponentWithConnectionToRedux
```

Todo esto visto anterior mente, osea, el componente y el código visto anterior mente, seria la parte contenedor del patrón contenedor-contenido visto anteriormente.

```js
const mapStateToProp = (state, ownProps) => {
    // en este caso, el componente recibirá counter como prop
    return {counter: state.counter}
}

const  mapDispatchToProp = (dispatch, ownProps) => {
    // nombre de las props para ejecutar y llamar a una action
    return {
        increment: () => dispatch({ type: 'INCREMENT' }),
        decrement: () => dispatch({ type: 'DECREMENT' }),
        reset: () => dispatch({ type: 'RESET' }),
    }
}

const createConnect = connect(mapStateToProps, mapDispatchToProps)

const ComponentWithConnectionToRedux = createConnect(Counter)

export default ComponentWithConnectionToRedux

```

Tranquilos, redux trae muchos conceptos nuevos que hay que asimilar poco a poco.

Esto sería el ejemplo de un contador de cómo controlaríamos el estado antes de utilizar Redux. Estamos usando el state local del componente. 

```js
import React, { useState } from 'react';

const Counter = () => {
  
    const [count, setCount] = useState(0)
  
    const handleAddClick = () => {
       setCount(count + 1)
    }

    const handleSubClick = () => {
        setCount(count - 1)

    }

    return (
        <>
            <button name='add' onClick={handleAddClick} >+</button>
            <button name='sub' onClick={handleSubClick} >-</button>
            <h1>The value is: {count}</h1>

        </>
    );
    
}
 
export default Counter
```

A continuación haremos las modificaciones necesarias para poder trabajar con Redux

#### Componente Provider <Provider store>

Hace que la store esté disponible en todo nuestro árbol de elementos. Tendremos que envolver nuestra aplicación con este componente para poder utilizar el método connect en cualquier descendiente.


```js
// App.js

import React from 'react';
import {Provider} from 'react-redux'
import store from './redux/store'
import './App.css';
import Footer from './components/Footer/Footer';
import Header from './components/Header/Header';
import Main from './components/Main/Main';

function App() {
  return (
    <Provider store={store}>
    <div className="App">
        <Header/>
        <Main/>
        <Footer/>
    </div>
    </Provider>
  );
}

export default App;

```

Vamos a crear una app sencilla con redux. Una vez que tengamos instalado react-redux vamos a crearnos el reducer en el directorio redux/counter:

redux/counter/counterTypes.js
```js
export const INCREMENT = 'INCREMENT'
export const DECREMENT = 'DECREMENT'
export const RESET = 'RESET'
```


Definimos en un fichero las acciones a realizar

redux/counter/counterActions.js
```js
import {INCREMENT,DECREMENT,RESET} from './counterTypes'

export const increment = () =>{
    return {
        type: INCREMENT
    }
}

export const decrement = () =>{
    return {
        type: DECREMENT
    }
}

export const reset = () =>{
    return {
        type: RESET
    }
}
```

Definimos en otro fichero el reducer

redux/counter/counterReducer.js
```js 
 import {INCREMENT,DECREMENT} from './counterTypes';

const INITIAL_STATE = {
    counter: 0
}

export function counterApp(state = INITIAL_STATE, action){
    switch (action.type) {
        case INCREMENT:
            return {
                counter: state.counter + 1
            }
        case DECREMENT:
            return {
                counter: state.counter - 1
            }
        default:
            return state
    }
  }
```

Ahora que ya tenemos nuestro reducer, vamos a definir la store en un fichero:

redux/store.js
```js
import {createStore,applyMiddleware} from 'redux'
import counterReducer from './counter/counterReducer'

const store = createStore(counterReducer));
export default store

```

Definimos en otro fichero un export para que estén disponibles las actions de la store
redux/index.js
```js
export * from './counter/counterActions';
```

Ahora vamos a crear nuestro componente, que va a utilizar la store y va a estar conectado al container de la store:

components/CounterContainer.js
```js
import React from 'react'
import {connect} from 'react-redux';
import { increment,decrement,reset } from '../redux'

function CounterContainer({counter,increment,decrement,reset}) {
    return (
        <>
            <button name='add' onClick={increment} >+</button>
            <button name='sub' onClick={decrement} >-</button>
            <button name='reset' onClick={reset} >reset</button>
            <h1>The value is: {counter}</h1>
        </>
    );
}

const mapStateToProps = state => {
    // en este caso, el componente recibirá counter como prop
    console.log(state.counter)
    return {counter:state.counter}
}

const mapDispatchToProps = dispatch => {
    // nombre de las props para ejecutar y llamar a una action
    return {
        increment: () => dispatch(increment()),
        decrement: () => dispatch(decrement()),
        reset: () => dispatch(reset())
    }
}

export default connect(
    mapStateToProps,
    mapDispatchToProps
)(CounterContainer)

```

Habilitamos una ruta para jugar con Redux en nuestro proyecto y enlazamos dicha ruta al siguiente componente:

components/PruebaRedux.js
```js
import React from 'react'
import CounterContainer from './CounterContainer'

function PruebaRedux() {
    return (
        <div>
            <CounterContainer/>
        </div>
    )
}

export default PruebaRedux
```

Ya tenemos nuestra aplicación tirando de Redux! Podemos comprobarlo poniendo un console.log en el reducer para ver el state y la action que recibimos:

```js
const initialState = {
    counter: 0
}

export function counterApp(state = INITIAL_STATE, action){
    console.log(state, action)
    switch (action.type) {
        case 'INCREMENT':
            return {
                counter: state.counter + 1
            }
        //....
        //....
        default:
            return state
    }
  } 
```
## Instalaciones para monitorizar cambios en Redux:
## Redux Logger
- [redux-logger](https://github.com/LogRocket/redux-logger)
```
npm i --save redux-logger
```
## Redux DevTools extension
- [Redux devtools extension | Chrome](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=es)
- [redux-devtools-extension | GitHub](https://github.com/zalmoxisus/redux-devtools-extension)
```
npm install --save redux-devtools-extension
```

## Async actions

- Acciones síncronas: Nada más llamar a cierta acción, se modifica el estado
- Acciones asíncronas: Llamadas a APIs externas para hacer petición de datos. No sabes el tiempo que va a tardar en responder. Veremos cómo afecta esto en Redux a State, Actions, Reducers.
- Usaremos `Redux Thunk` para manejar Async actions

Recursos:
- [redux-thunk | NPM](https://www.npmjs.com/package/redux-thunk)
- [Acciones asíncronas de Redux con Redux Thunk](https://www.digitalocean.com/community/tutorials/redux-redux-thunk-es)
- [managing-asynchronous-actions-in-redux](https://blog.logrocket.com/managing-asynchronous-actions-in-redux-1bc7d28a00c6/)
- [asynchronous-operations-in-react-redux](https://blog.jscrambler.com/asynchronous-operations-in-react-redux/)

## Combinar múltiples reducers
- [using-combine reducers](https://redux.js.org/usage/structuring-reducers/using-combinereducers)
- [combine-reducers-in-a-react-redux-application](https://dev.to/cesareferrari/combine-reducers-in-a-react-redux-application-580k)


## Action payload
- [what-is-a-payload-in-redux-context](https://stackoverflow.com/questions/51357412/what-is-a-payload-in-redux-context)

## Hooks en React Redux. useSelector(), useDispatch()
**IMPORTANTE: Útil para simplificar código**
- [Redux Hooks](https://react-redux.js.org/api/hooks)
- [react-redux-hooks-useselector-and-usedispatch](https://levelup.gitconnected.com/react-redux-hooks-useselector-and-usedispatch-f7d8c7f75cdd)
- [React Hooks y Redux funcionando juntos](https://latteandcode.medium.com/react-hooks-y-redux-funcionando-juntos-869d2900f0cb)

## EJEMPLO - Acciones asíncronas con Redux

Vamos a montar un ejemplo manejando acciones asíncronas:

redux/user/userActions.js
```javascript
    import axios from 'axios'

    import {FETCH_USERS_REQUEST, 
            FETCH_USERS_SUCCESS, 
            FETCH_USERS_FAILURE} from './userTypes';

    export const fetchUsersRequest = () => {
        return {
            type: FETCH_USERS_REQUEST
        }
    }

    export const fetchUsersSuccess = users => {
        return {
            type: FETCH_USERS_SUCCESS,
            payload: users
        }
    }

    export const fetchUsersFailure = error => {
        return {
            type: FETCH_USERS_FAILURE,
            payload: error
        }
    }

    export const fetchUsers = () => {
        return (dispatch) => {
            dispatch(fetchUsersRequest())
            axios.get('https://jsonplaceholder.typicode.com/users')
            .then(response => {
                const users = response.data;
                dispatch(fetchUsersSuccess(users))
                
            })
            .catch(error => {
                const errorMsg = error.message
                dispatch(fetchUsersFailure(errorMsg))

            })
        }
    }

```

redux/user/userReducer.js
```javascript
    import {FETCH_USERS_REQUEST, 
        FETCH_USERS_SUCCESS, 
        FETCH_USERS_FAILURE} from './userTypes';

    const initialState = {
        loading:false,
        users: [],
        error:''
    }


    const reducer = (state = initialState, action) =>{
        switch(action.type){
            case FETCH_USERS_REQUEST: 
            return {
                ...state,
                loading:true,
            }

            case FETCH_USERS_SUCCESS: return {
                loading:false,
                users: action.payload,
                error:''
            }

            case FETCH_USERS_FAILURE: return {
                loading:false,
                users: [],
                error:action.payload
            }
            default: return state
        }
    }

    export default reducer
```

redux/user/userTypes.js
```javascript
    export const FETCH_USERS_REQUEST = 'FETCH_USERS_REQUEST'
    export const FETCH_USERS_SUCCESS = 'FETCH_USERS_SUCCESS'
    export const FETCH_USERS_FAILURE = 'FETCH_USERS_FAILURE'
```
![react redux](../../assets/react/clase43/redux_example.jpeg)


### Más ejemplos de Redux
- [Ejemplos Redux](https://redux.js.org/introduction/examples)

![react redux](../../assets/react/clase43/reduxmeme.jpg)




