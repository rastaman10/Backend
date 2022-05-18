![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png  "logotipo de The Bridge")
# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)
# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)
### JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

## Intro a TypeScript

![img](../../assets/react/introTS/typescript-logo.png)

TypeScript es un lenguaje de programación fuertemente tipado basado en JavaScript.

- [Why and How to use TypeScript in your React App?](https://blog.bitsrc.io/why-and-how-use-typescript-in-your-react-app-60e8987be8de)
- [5 Reasons to Use TypeScript with React](https://blog.bitsrc.io/5-strong-reasons-to-use-typescript-with-react-bc987da5d907)

### TypeScript con React

Para crear nuestra app de React con create-react-app:

```javascript
npx create-react-app my-app --template typescript
```

- [CheatSheet React TypeScript](https://react-typescript-cheatsheet.netlify.app/docs/basic/setup)

Necesitamos tipar todo lo que vayamos a utilizar. En el caso de tipar objetos usaremos interfaces:

```javascript
interface Jedi {
    name: string,
    age: number,
    isMaster: boolean,
    enemies: string[]
};
```

Para tipar variables de tipo primitivo lo haremos de la siguiente manera: 

```javascript
const name: string = 'Yoda';
const age: number = 897;
const isMaster: boolean = true;
```

- [Type vs Interface](https://blog.logrocket.com/types-vs-interfaces-in-typescript/)

### Enlaces de interés

- [Migrando una aplicación de JavaScript a TypeScript](https://goncy.netlify.app/react-javascript-typescript)
- [Ejemplo estructura proyecto TypeScript-React](https://dev.to/djamaile/how-i-structure-my-react-ts-applications-160g)
- [TypeScript handbook](https://www.typescriptlang.org/docs/handbook/intro.html)

![img](../../assets/react/introTS/bob-type.jpg)
