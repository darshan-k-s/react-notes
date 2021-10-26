# React

~ Darshan K S :crown:

### Nav:

1. [Intro](#intro)
2. [Setting up environment](#setup)
3. [`index.js` and rendering](#render)
4. [JSX](#jsx)
5. [Components in React](#component)
6. [Using modules in React](#modules)
7. [Wrapping data in components](#wrap)
8. [Handling events](#events)
9. [Conditional Rendering](#conditional)
10. [CSS in React](#css)
11. [SCSS in React](#scss)
12. [Hooks](#hooks)
13. [State Hook](#state)
14. [Effect Hook](#effect)
15. [Fetch requests with React](#fetch)
16. [AJAX with loading and error](#ajax)
17. [Show/Hide conditionally](#showhide)
18. [Forms in React](#form)
19. [useRef](#useRef)
20. [useReducer](#useReducer)
21. [Prop drilling](#propdrilling)
22. [React Context](#usecontext)
23. [Custom hooks](#customhooks)
24. [Prop types](#proptypes)
25. [React router](#reactrouter)
26. 





### Intro:

React is a JavaScript library for building user interfaces created by Facebook(July 2013). React is used to build single page applications. React allows us to create reusable UI components.

React is also supported on CodePen(cool stuff).

[Project based tutorial]([Tutorial: Intro to React – React (reactjs.org)](https://reactjs.org/tutorial/tutorial.html))

[Official docs]([Create a New React App – React (reactjs.org)](https://reactjs.org/docs/create-a-new-react-app.html))



> Extensions:

1. For browser: React developer tools

2. Also to use emmet in react files: 

   Settings > json > Add the following line

   ```json
   "emmet.includeLanguages": {
           "javascript": "javascriptreact"
       },
   ```

3. ES7 extension in VSCode:

   Used to create boilerplate for react apps and more.

    ```
    Emmet snippets:
    rfce
    rafce
    rce
    ```

   This creates the starting boilerplate:

   ```js
   import React from 'react'
   
   function fileName() {
     return (
       <div>
         
       </div>
     )
   }
   
   export default fileName
   ```



> How React works:

React creates a VIRTUAL DOM in memory. 

Instead of manipulating the browser's DOM directly, React creates a virtual DOM in memory, where it does all the necessary manipulating, before making the changes in the browser DOM. 

React only changes what needs to be changed!

React automatically uses Babel and Webpack.

---



### <a name="setup">Setting up environment:</a>

We can setup the whole environment ourselves or we can use tools like Create React App and customize it later(recommended).

You need to have `node.js` and `npm` installed.

### create-react-app

Initially create using `npx`(personal choice). Also advised to uninstall global installation of `create-react-app`. 

```bash
npx create-react-app my-app
```

By default after creation, the CLI will use Yarn to install dependencies(recommended). We can change the package manager during the creation:

```bash
npx create-react-app my-app --use-npm
```

After we use create-react-app, the following folder setup will be done in `my-app` folder:

```
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── serviceWorker.js
    └── setupTests.js
```

Then to start the production server:

```bash
yarn start
# OR
npm start
```

The production port is `3000`. The production server is comparable to the live-server. 



### Folder structure:

The folder structure I prefer.

```
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── index.html
|   └──  manifest.json   
└── src
    |──  assets
    |    ├── images
    |    ├── audio
    |    └──  videos
    ├── css
    |	├── index.css
    |	├── App1.css
    |	...
    ├── scss
    |	├── index.scss
    ├── components
    |	├── App1.js
    |	├── App2.js
    |	...
    └── index.js
```

Here:

1. `node_modules`:

   Folder with all the dependencies.

2. `package.json`:

   The standard package file for the environment including scripts and dependencies for the project.

3. `package-lock.json`:

   `package-lock.json` is automatically generated for any operations. It describes the exact tree that was generated, such that subsequent installs are able to generate identical trees, regardless of intermediate dependency updates.

4. `index.html`: 

   The main HTML file where our react apps will be rendered. You can customize this HTML file for the titlebar appearance, metadata, links to files and CDNs. 

   Also we have a `div` with `id='root'` inside which we render our React app. We can of course name it anything and use any HTML element to render the React apps inside them(just need to setup in the app files). 

5. `index.js`:

   The main JS entry-point file where we import `react-dom` and all the react apps we want and then actually render the apps into the elements in `index.html`. 

6. `css`:

   In this folder, we store all our CSS files for the components(name them componentName.css).

7. `components`:

   This is where we store all our components. We later bring them together in the `index.js` for rendering.

8. `assets`:

   Where we store all media and such files. Just note this about where to put the assets folder. 

   <u>public</u>: anything that is not used by your app when it compiles

   <u>src</u>: anything that is used when the app is compiled

---



### <a name="render">`index.js` and rendering:</a>

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

In the `index.js` we import all the react apps we want along with `react` and `react-dom` and render the apps into the HTML file. 

Also, just like in HTML, just going to a folder name will automatically open up the `index.js` of that folder. 

Here, `ReactDOM.render()` is the method used to render our component or apps into HTML elements in the `index.html` file. The first argument is the components or apps we want to render and for the second argument we fetch the element into which our render has to be injected. 

---



### JSX:

JSX stands for JavaScript XML. JSX allows us to write and add HTML in React. JSX converts HTML tags into react elements and is a syntax extension to JS.

JSX allows us to write HTML elements in JavaScript and place them in the DOM without any `createElement()` or `appendChild()` methods. 

You are not required to use JSX, but JSX makes it easier to write React applications. This funny tag syntax is neither a string nor HTML. 

With and without JSX demo:

```jsx
// With JSX
const myelement = <h1>I Love JSX!</h1>;
// Without JSX
const myelement = React.createElement('h1', {}, 'I do not use JSX!');
```



**<u>Note</u>**: 

JSX should always return a single element. If you want multiple elements, nest them in a parent element which gets returned. Try being more semantic. 

Generally we can't keep returning everything inside a `<div>` or such. Instead we can use React fragments.

> Fragments: 

Fragments let you group a list of children without adding extra nodes to the DOM. Enclose everything between the fragment tags and the children will be directly injected into the rendering element.

```react
// Normal syntax
return (
    <React.Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment>
  );

// Short syntax
return (
    <>
      <ChildA />
      <ChildB />
      <ChildC />
    </>
  );
```



> ###### Embedding expressions in JSX:

With JSX you can write expressions inside curly braces `{ }`. The expression can be a React variable, or property, or any other valid JavaScript expression(functions, comments, ...anything). JSX will execute the expression and return the result. 

```jsx
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}
const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};
const element = (
  <h1> Hello, {formatName(user)}! </h1>
);
```

> ###### Attributes wit JSX:

```jsx
const element = <div tabIndex="0"></div>;
// Embed expressions
const element = <img src={user.avatarUrl}></img>;
```

Don’t put quotes around curly braces when embedding a JavaScript expression in an attribute. You should either use quotes (for string values) or curly braces (for expressions), but not both in the same attribute. 

Also, React DOM uses `camelCase` property naming convention instead of HTML attribute names.

`class` becomes `className`.

> ###### Child elements in JSX:

```jsx
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```



>###### JSX prevents injection attacks:

It is safe to embed user input in JSX:

```jsx
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```

By default, React DOM [escapes](https://stackoverflow.com/questions/7381974/which-characters-need-to-be-escaped-on-html) any values embedded in JSX before rendering them(can use only HTML entities). Thus it ensures that you can never inject anything that’s not explicitly written in your application. Everything is converted to a string before being rendered. This helps prevent [XSS](https://en.wikipedia.org/wiki/Cross-site_scripting) attacks. 



> ###### JSX represents objects:

Babel compiles JSX down to `React.createElement()` calls. The below 2 examples are identical:

```jsx
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

```js
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```



###### `createElement()`:

`React.createElement()` performs a few checks to help you write bug-free code but essentially it creates an object like this:

```js
// Note: this structure is simplified
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```

This came from:

```js
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

 React reads these objects and uses them to construct the DOM and keep it up to date. 



---



### <a name="component">Components in React:</a>

Components let you split the UI into independent, reusable pieces, and think about each piece in isolation. Components are like functions that return HTML elements. 

All components must start with an uppercase so that react can actually recognize components and distinguish them from other DOM tags, functions and classes. 

Components are made using a group of elements(JSX or `createElement`). 

> ###### Creating a component:

The simplest way to define a component is to write a function(function component):

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

These can be any kind of arrow function too. 

> Using Class component:

This is the old way to do stuff. I'd rather use the function way.

This statement creates an inheritance to `React.Component`, and gives your component access to `React.Component` functions. The component also requires a `render()` method, this method returns HTML. 

```react
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}
```

Elements become components using these 2 ways. 



> ###### props:

 `props` (which stands for properties) is an object argument with data that can be used inside the elements of the component. Basically when we pass arguments, all of these arguments will be passed as a single object(`props`) to the component, from where we can access them. 

Calling it `props` is just the convention(we can call it anything we want at the component definition). 

```react
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

ReactDOM.render(
  <Welcome name="Sara" />,
  document.getElementById('root')
);
```

These arguments have to be passed as properties where the component is being used. 

```react
let joke = "yomama";
<Welcome name="Sara" id={1} jk={joke}/>
// Variables and Numbers should be embedded while passing
```

We can pass arguments with any name at the line where we use the component and with the argument, its value. 

Even though this is really flexible, don't start using random argument names and try keeping it consistent across all instances. 

<u>Note:</u> The passed properties must never be altered inside the component(only pure functions can be components). This is a strict rule in React. 

> Accessing the values:

1. Object nesting:

   As `props` is just an object we can access its properties with the `.` operator.

2. Destructuring:

   Just destructure the `props` object to make it simpler to use. We can do this inside the component body or where the parameters are passed to the component function itself. 

   ```react
   const Book(props){
       const {img, title, author:{firstName, lastName}} = props;
   }
   // OR 
   const Book({img, title, author:{firstName, lastName}}){
   }
   ```

   

> ###### Reusing components:

We can treat created components the literal way and use them wherever we want, and even alter `props` as needed. We can even store them in variables. Just referring to the component as a JSX tag will return the whole component at that place, just like a variable. 

```react
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

This is incredibly useful to separate the UI and data extraction part by treating data extraction as one component which will be used inside another to give us the final UI component. 



> ###### Children in components:

We can have multiple independent children inside a component. But these children won't be rendered as long as we don't include them in component definition. 

<u>Using the children:</u>

```react
function BookList(){
    return(
        <Book author="Lorem">
            <p>Description goes here...</p>
            <h3>yomama</h3>
        </Book>
    );
}
function Book(props){
    const {author, children} = props;
    return(
        <>
        {children[1]}
        <h3>{author}</h3>
        {children[0]}
        </>
    );
}
```

The children won't be rendered unless we return them in the component. Just like properties, all the children will be passed as a object `children`, inside `props` itself. We can access the children just like any other property and also access specific children using indexes.

Where the children are rendered has to be decided by us in the component.  



---



### <a name="modules">Using modules in React:</a>

A module can contain variables and functions. A module is nothing more than a chunk of JavaScript code written in a file. 

> ###### Exporting:

Variables and functions within a module should be exported so that they can be accessed from within other files. The `export` keyword can be used to export components in a module. 

There are two ways to export:

1. Named exports:

   This way is used to export only selected components and these components are distinguished by their name. 

   ```js
   //using multiple export keyword
   export component1
   export component2
   ...
   export componentN
   
   //using single export keyword
   export {component1,component2,....,componentN}
   ```

2. Default exports:

   To export only a single value we can use default exports. There can be only one default export per module. 

   ```js
   export default component_name
   ```

   However, a module can have a default export and multiple named exports at the same time. 

   Both can be imported separately. 



> ###### Importing:

We use the `import` keyword. A module can have multiple import statements. 

1. Importing named exports:

   While importing named exports, the names of the corresponding components must match. 

   ```js
   import {component1,component2,...,componentN} from module_name
   ```

   However, while importing named exports, they can be renamed using the `as` keyword.

   ```js
   import {original_component_name as new_component_name } from module_name
   ```

   To import all named exports from a module, use `*` operator.

   ```js
   import * as variable_name from module_name
   ```

   

2. Importing default exports:

   Unlike named exports, a default export can be imported with any name. 

   ```js
   import any_variable_name from module_name
   ```

   The default exported component will automatically be imported as any given variable name. 



> ###### Importing files:

We should import files into our App to use them in React(needed for compilation). 

```js
import './index.css'
import 'data'
```

Here `data` is a JS files. Only JS files can be imported without using their extension. 



---



### <a name="wrap">Wrapping data in components:</a>

```react
const books = [
    {
        id: 1,
        title: "A Game of Thrones",
        author: "George R R Martin"
    },
	{
        id: 2,
        title: "Maze Runner",
        author: "James Dashner"
    },
    {
        id: 3,
        title: "The Secrets of Droon",
        author: "Tony Abbott"
    },
];

function BookList(){
    return(
        <>
        {books.map((book)=>{
        	return <Book key={book.id} book={book}></Book>
    	})}
        </>
    );
}

function Book(props){
    const{title, author} = props.book;
    return(
        <article>
            <h2>{title}</h2>
            <h4>{author}</h4>
        </article>
    );
}

```

Go through the above example. We are displaying every object in the array by using `map` function from ES6. `map` function makes it very easy to iterate over the array. 

The `key` property is something that React uses to identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity. Keys can be strings and numbers. Keys used within arrays should be unique among their siblings. However, they don’t need to be globally unique.

Another way to pass properties is to use the spread operator.

```react
function BookList(){
    return(
        <>
        {books.map((book)=>{
        	return <Book key={book.id} {...book}></Book>
    	})}
        </>
    );
}

function Book(props){
    const{title, author} = props;
    return(
        <article>
            <h2>{title}</h2>
            <h4>{author}</h4>
        </article>
    );
}
```



---



### <a name="events">Handling events:</a>

Handling events with React elements is very similar to handling events on DOM elements. React events are named in camelCase. With JSX you pass a function as the event handler, rather than just arguments like in Vanilla JS. 

```react
function Book(props){
    const{title, author} = props;
    function activateLasers(e){
        e.preventDefault();
        alert("Activated", title, "by", author);
    }
    return(
        <article>
            <h2>{title}</h2>
            <h4>{author}</h4>
            <button onclick={() => activateLasers}>
  			Activate Lasers
			</button>
        </article>
    );
}
// If we don't use the arrow function, we will be invoking the function when the DOM is rendered.
```

When using React, you generally don’t need to call `addEventListener` to add listeners to a DOM element after it is created. Instead, just provide a listener when the element is initially rendered. 



---



### <a name="conditional">Conditional Rendering:</a>

In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state of your application.

Use JavaScript operators like `if` or conditional operators to create elements representing the current state, and let React update the UI to match them.

```react
// Individual components
function MissedGoal() {
  return <h1>MISSED!</h1>;
}
function MadeGoal() {
  return <h1>Goal!</h1>;
}
// main component where conditional rendering takes place
function Goal(props) {
  const isGoal = props.isGoal;
  if (isGoal) {
    return <MadeGoal/>;
  }
  return <MissedGoal/>;
}

ReactDOM.render(
  <Goal isGoal={false} />,
  document.getElementById('root')
);
```

We can have control over the `isGoal` attribute in many ways, including `useState` hook. 

We can also use other conditional constructs in JS to achieve conditional rendering. 

This is pretty simple and yet a very powerful feature in React. 

<u>Note:</u>

If we don't  want a component to render based on a condition, we just return `null`. 

```react
function WarningBanner(props) {
  if (!props.warn) {return null;}
  return (
    <div className="warning">
      Warning!
    </div>
  );
}
```

> ###### Short circuiting:

We can't use conditional constructs embedded inside return statements, since these constructs can't return anything. But we can still use operators(&&, ||, ?:) to setup conditions inside return statements.

```react
return (<>
      // OR operator to skip out on empty text
      <h1>{text || ''}</h1>
      
      <button className='btn' onClick={() => setIsError(!isError)}>
        toggle error
      </button>
      {isError && <h1>Error...</h1>}
      // Using ternary operator
      {isError ? (
        <p>there is an error...</p>
      ) : (
        <div>
          <h2>there is no error</h2>
        </div>
      )}
    </>
  );
```







---



<a name="css">CSS in React:</a>

There are 3 ways to style React with CSS:

- <u>Inline styling:</u>

  To style an element with the inline style attribute, the value must be a JavaScript object:

  ```react
  const Header = () => {
    return (
      <>
        <h1 style={{color: "red"}, backgroundColor: "lightblue"}>Hello Style!</h1>
        <p>Add a little style!</p>
      </>
    );
  }
  ```

  A clever way is to create an object with styling info and refer to it in the style property.

  ```react
  const Header = () => {
    const myStyle = {
      color: "white",
      backgroundColor: "DodgerBlue",
      padding: "10px",
      fontFamily: "Sans-Serif"
    };
    return (
      <>
        <h1 style={myStyle}>Hello Style!</h1>
        <p>Add a little style!</p>
      </>
    );
  }
  ```



- <u>Importing Stylesheets:</u>

  You can write your CSS styling in a separate file, just save the file with the `.css` file extension, and import it in your application. 

  ```react
  import React from 'react';
  import ReactDOM from 'react-dom';
  import './App.css';
  ```



---



<a name="scss">SCSS in React:</a>

Sass files are executed on the server during compilation and sends CSS to the browser. 

We can just install and setup SASS in a React project.

```bash
npm install sass
```

We can just import SCSS files the same way we do CSS stylesheets. 

```react
import React from 'react';
import ReactDOM from 'react-dom';
import './my-sass.scss';
```

The transpilation is handled for us.



---



### <a name="hooks">Hooks:</a>

Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class. Hooks provide a more direct API to the React concepts you already know: props, state, context, refs, and lifecycle. 

> Rules for using Hooks:

- You must `import` Hooks from `react`. 
- Hooks can only be called inside React function components.
- Hooks can only be called at the top level of a component.
- Hooks cannot be placed inside conditional constructs(if-else, loops, functions).

A Hook is a special function that lets you “hook into” React features. For example, `useState` is a Hook that lets you add React state to function components. 

They let us change the UI with specific re-rendering of components. 



---



<a name="state">State Hook:</a>

```react
// Importing the useState Hook from React:
import React, { useState } from 'react';

function Example() {
  // Declare and initialize new state variable  
  const [count, setCount] = useState(0);
  return (
    <div>
      // Using the state variable
      <p>You clicked {count} times</p>
	  // We have an event-handler which is changing the state inside it. 
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```



`useState` is a Hook that lets you add React state to function components. We’ll learn other Hooks later. Hooks should reside within the functional component. 

`const [count, setCount] = useState(0);`

Here, we are declaring a new state variable(`count`) and is used to preserve values between function calls and re-renders. 

`setCount` is the state-handling function, used to update or change the state variable. Professional practice is to name it camelCase with a prefix `set` to the state variable. We should always call this function whenever we want to change the state variable(Don't attempt to change the state directly). 

Calling `useState` declares the state variable, and also sets the default state value as the argument passed. Here, default state value is `0`. 
Looking closely, we can realize that `useState()` is a function that returns an array with 2 items, the state variable and the state-handling function, and we are destructuring the array.   



> Updating the State variable: 

```react
 <button onClick={() => setCount(count + 1)}>
    Click me
  </button>
```

We can have multiple states for the same component.



> Using an Object as state variable:

```react
import { useState } from "react";
import ReactDOM from "react-dom";

function Car() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });

  // Spread operator
  const updateColor = () => {
    setCar(prevState => { 
        return {...prevState, color: "blue"}
    });
  }

  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
      <button
        type="button"
        onClick={updateColor}
      >Blue</button>
    </>
  )
}

ReactDOM.render(<Car />, document.getElementById('root'));
```

Use the JavaScript spread operator to update only the color of the car. 



Also the state-handling function is asynchronous. Hence, in case of timeouts and such, no matter how many time we call it, the function will take the current state value. 

Before the state values are set by the state-handling function, the state value is held by an argument inside the function, which we generally name `prevState`. This way we can have a better hold on the state and the issues that may come up by asynchronity are solved.

```react
function increase(){
    setTimeout(()=>{
     setState((prevState)=> {return prevState + 1});   
    },2000);
}
// If we don't use prevState here, the asynchronous function will take the value(unchanged since previous functions aren't executed completely) for every iteration no matter how many times we click.
```









---



<a name="effect">Effect Hook:</a>

The Effect Hook lets you perform side effects in function components(i.e making changes happen outside the component based on changes to the component). 

****

```react
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

Data fetching, setting up a subscription, timers and manually changing the DOM in React components are all examples of side effects. 

By default, `useEffect()` runs on every render including the initial render of the component it is present in.  Placing `useEffect` inside the component lets us access the state variables (or any props) right from the effect. 

> Function details:

`useEffect` accepts two arguments. The second argument is optional.

```react
useEffect(callback-function, dependency-array);
```

The callback function runs every time `useEffect` is triggered by rendering. It is inside the callback function that we do whatever changes and effects we want to happen.

> <u>Dependency array:</u> 

We can pass dependencies to `useEffect` with this array and hence the callback function will be invoked only if any of the listed dependencies change.

By default, if we don't pass the second argument for the `useState` hook, every part of the component will be a dependency and will run on every render.

An empty array:

```react
useEffect(() => {
    //Runs only on the first render if empty array is passed
  }, []);
```

Passing props or state values:

```react
useEffect(() => {
    //Runs on the first render
    //And any time any dependency value changes
  }, [prop, state]);
```

This will run whenever any of the listed props or state variables of the component changes. 

```react
const UseEffectBasics = () => {
  const [count, setCount]=useState(0);
  const [val, setVal]=useState(10);

// Runs only on initial render as val is not a dependency
  useEffect(()=>{
    console.log(val);
    if(count>0){
      document.title = "Notifications |" + count;
    }
  }, [count]);
  return <>
  <h2>{count}</h2>
  <button onClick={()=>{setVal(val+1)}}>Increase</button>
  </>; 
};
```



> <u>Cleanup function:</u>

For example, we might want to set up a subscription to some external data source. In that case, it is important to clean up so that we don’t introduce a memory leak! 

Timeouts, subscriptions, event listeners, and other effects that are no longer needed should be disposed as some of them may introduce a loop of re-renders which call `useEffect` again and again automatically. 

By using a cleanup function, we are making sure that everything inside the callback function is executed only once until the next triggered render by us and cleans up everything from the previous render if the previous render isn't completed. 

We do this by including a return function at the end of the `useEffect` Hook.   

```react
function Timer() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    let timer = setTimeout(() => {
    setCount((count) => count + 1);
  }, 1000);
  // Cleanup function to clear the setTimeout 
  return () => clearTimeout(timer)
  }, []);

  return <>
        <h1>I've rendered {count} times!</h1>
  		<button onClick={()=>setCount(count+1)}>Increase</button>
      </>;
}
```

The cleanup function is widely use for API calls and HTTP requests.



---



<a name="fetch">Fetch requests with React:</a>

> Basic one time load:

```react
const url = 'https://api.github.com/users';

const UsersProfiles = () => {
  const [users, setUsers] = useState([]);
  useEffect(()=>{
    const getUsers = async()=>{
      const response = await fetch(url);
      const users = await response.json();
      setUsers(users);
    }
    getUsers();
  },[]);

  return <>
  <h3>Github users</h3>
  <ul>
    {users.map((user) => {
        const {id, login, avatar_url, html_url} = user;
        return(
          <li key={id}>
            <img src={avatar_url} alt={login} />
            <div>
              <h4>{login}</h4>
              <a href={html_url}>Profile</a>
            </div>
          </li>
        );
      })
    }
  </ul>
  </>;
};
```



---



<a name="ajax">AJAX with loading and error:</a>

```react
const url = 'https://api.github.com/users/QuincyLarsons';

const MultipleReturns = () => {
  // States for AJAX
  const [isLoading, setIsLoading] = useState(true);
  const [isError, setIsError] = useState(false);
  const [user, setUser] = useState('Guest');

  // AJAX flow
  useEffect(()=>{
    // Fetch request
    fetch(url)
      // Checking what kind of response
      .then((resp)=> {
        // If successful, get the JSON
        if(resp.status >= 200 && resp.status < 300){
          return resp.json();
        }
        else{
          // Show error
          setIsLoading(false);
          setIsError(true);
          throw new Error(resp.status);
        }
      })
      // Using the JSON received
      .then((user)=>{
        const {login} = user;
        setUser(login);
        setIsLoading(false);
      })
      // Do this so that complete error dowsn't pop up on screen 
      .catch((error)=> console.log(error));
  }, []);

  // Conditional render
  if(isLoading){
    return <>
    <h1>Loading... </h1>
    </>;
  }
  if(isError){
    return <>
    <h1>Error fetching </h1>
    </>;
  }
  return <>
  <h1>{user}</h1>
  </>;
};
```



---



<a name="showhide">Show/Hide conditionally:</a>

```react
const ShowHide = () => {
  const [show, setShow] = useState(false);

  return (<>
    <button className='btn' onClick={()=> setShow(!show)}>Show/Hide</button>
    {show && <Item />}
  </>
  );
};

const Item = ()=>{
  const [width, setWidth] = useState(window.innerWidth);

  function checkSize(){
    setWidth(window.innerWidth);
  }
  useEffect(()=>{
    window.addEventListener('resize', checkSize);
    return(() =>{
      window.removeEventListener('resize', checkSize)
    }
    );
  });

  return(<>
    <h1>Window</h1>
    <h3>{width} px</h3>
    </>
  );
};
```



---



<a name="form">Forms in React:</a>

Unchanged JSX forms work the same way they do in plain HTML, the form will submit and the page will refresh. In HTML, form data is usually handled by the DOM. 

But this is generally not what we want to happen in React. We want to prevent this default behavior and let React control the form. It’s convenient to have a JavaScript function that handles the submission of the form and has access to the data that the user entered into the form. In React, form data is usually handled by the components. When the data is handled by the components, all the data is stored in the component state.



> ###### Controlled components:

To have control over the inputs and the submission, we use this technique. 

We first assign each input its own state and match the `value` attribute with the state. We then control the changes in input field by adding adding event handlers with the `onChange` attribute. When we do this, we can now give inputs and the state is updated as we do it. 

```react
function MyForm() {
  const [name, setName] = useState("");
  return (
    <form>
      <label htmlFor="name">Enter your name:
        <input
          type="text" 
          value={name}
          // The event object is accessed to get the input value
          onChange={(e) => setName(e.target.value)}
          id="name"
        />
      </label>
    </form>
  )
}
```

<u>Note</u>: Notice the `htmlFor` instead of `for` used in the label.  



> ###### Submitting forms:

You can control the submit action by adding an event handler in the `onSubmit` attribute for the `<form>`. 

```react
function MyForm() {
  const [name, setName] = useState("");
  const handleSubmit = (e) => {
    // This is important to prevent the default refreshing on submit
    e.preventDefault();
    alert('The name you entered was: ${name}');
  }
  return (
    <form onSubmit={handleSubmit}>
      <label>Enter your name:
        <input 
          type="text" 
          name="name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
      </label>
      <input type="submit" />
    </form>
  )
}
```



> ###### Multiple inputs:

We can handle the `onChange` of multiple inputs using only 1 function with the `name` attribute of each element and 1 combined complex state. We will initialize our state with an empty template object. 

```react
function MyForm() {
  const [inputs, setInputs] = useState([]);
  const [person, setPerson] = useState({name:'', age:''});

  const handleChange = (event) => {
    const name = event.target.name;
    const value = event.target.value;
    // Spread operator
    setPerson(person => ({...person, [name]: value}))
  }

  const handleSubmit = (event) => {
    event.preventDefault();
    // Append to list
    setInputs(...inputs, person);
    // Reset person
    setPerson({name:'', age:''});
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>Enter your name:
      <input 
        type="text" 
        name="username" 
        value={person.name || ""} 
        onChange={handleChange}
      />
      </label>
      <label>Enter your age:
        <input 
          type="number" 
          name="age" 
          value={person.age || ""} 
          onChange={handleChange}
        />
        </label>
        <input type="submit" />
    </form>
  )
}
```



> ###### Textarea in React:

In HTML the value of a textarea was the text between the start tag `<textarea>` and the end tag `</textarea>`. In React the value of a textarea is placed in the value attribute of `e.target`. 



>###### Select tag:

in HTML, the selected value in the drop down list was defined with the `selected` attribute. 

```react
<select>
  <option value="Ford">Ford</option>
  <option value="Volvo" selected>Volvo</option>
  <option value="Fiat">Fiat</option>
</select>
```

In React, the selected value is defined with a `value` attribute on the `select` tag just like textarea. 



---



<a name="useRef">useRef:</a>

The `useRef` Hook allows you to persist values between renders, just like useState, but doesn't trigger re-renders when updated unlike useState. Generally used when we want to target a DOM element directly. 

> ###### Usage with useEffect:

If we tried to count how many times our application renders using the `useState` Hook, we would be caught in an infinite loop. We could use `useRef` instead. 

```react
function App() {
  const [inputValue, setInputValue] = useState("");
  const count = useRef(0);

  useEffect(() => {
    count.current = count.current + 1;
  });

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h1>Render Count: {count.current}</h1>
    </>
  );
}
```



> ###### Using as a means of reference to elements:

The `useRef` hook returns one object called `current`. This object can then directly refer to a DOM element if we specify the reference in the HTML tag with the `ref` attribute.

```react
<input type='text' ref={refContainer} />
```

 We need to have created `refContainer = useRef()` before hand. Now this `current` object will reference the DOM element we specified and help us manipulate it directly.

The `current` object has an attribute of `value`. This is literally the value property of that DOM element and we can access it `refContainer.current.value` and change it whenever we want. We initialize this value in the hook creation `useRef(value)`. 



> Examples:

1. Persisting form data:

```react
const Persist = () => {
    const refContainer = useRef('');
    const handleSubmit = (e) => {
        e.preventDefault();
	}
    return(<>
        <form onSubmit={handleSubmit}>
            <div>
                <input type='text' ref={refContainer} />
                <button type='submit'>Submit</button>
            </div>
        </form>
    </>);
}
```



2. Focus on input field on every render:

```react
function App() {
  const inputElement = useRef();
  const handleSubmit = (e) => {
        e.preventDefault();
	}
  
  useEffect(()=>{
    inputElement.current.focus();      
  });

  return (
    <>
      <input type="text" ref={inputElement} />
      <button type="submit">Submit</button>
    </>
  );
}
```



---



<a name="useReducer">useReducer:</a>

The `useReducer` hook is similar and a improvement over the `useState` hook. It allows for custom state logic. If you find yourself keeping track of multiple pieces of state that rely on complex logic, `useReducer` may be useful. 

Syntax:

```react
defaultState = {
  people: [],
  isModalOpen: false,
  modalContent: 'hello world'
}
// Reducer function
const reducer = (state, action) =>{
  if(action.type === 'ADD_ITEM'){
    const newPeople = [...state.people, action.payload]
    return {...state, people: newPeople, isModalOpen: true, modalContent:"Added item"}
  }
  if(action.type === "EMPTY_SUBMIT"){
    return {...state, isModalOpen:true, modalContent: "Enter a name"};
  }
}
// Component
const Index = ()=>{
    const [name, setName] = useState("");
    // Declaration inside component
	const [state, dispatch] = useReducer(reducer, defaultState);
	// Form submit handler
    const handleSubmit= (e)=>{
    e.preventDefault();
    if(name){
      const newItem = {name};
      // dispatch call
      dispatch({type: 'ADD_ITEM', payload: newItem});
      setName("");
    }
    else{
      dispatch({type: 'EMPTY_SUBMIT'});
    }
  }
 
  return <>
    {state.isModalOpen && <Modal modalContent = {state.modalContent}/>}
    <form onSubmit={handleSubmit} className='form'>
      <div>
        <input type="text" value={name} onChange={(e)=>setName(e.target.value)} />
      </div>
      <button type='submit'>Add</button>
    </form>
    </>;
}

```

> ###### Working:

The hook takes 2 arguments(reducer & defaultState) and returns two objects(state & dispatch). 

1. `defaultState`:

   This is the default state value we need to pass while creating the hook so as to make a template of the complex state we are going to use. With this the state can be a complex object.

2. `state`:

   The state is the state object variable at any given point of time and its structure is built upon the `defaultState` passed.

3. `dispatch`:

   `dispatch` is a function which needs to be called in order to invoke the reducer function. It helps setting up conditional rendering by the reducer function with its `type` property. `type` is a user-defined name given to a case that has to be handled by the reducer. We can also pass arguments to the reducer function with the `payload` property of `dispatch`. These 2 properties will be passed to the `reducer` function as an object named `action`(convention).   

4. `reducer` function:

   The `reducer` function contains your custom state logic. It has the arguments `state` and `action`- contains the properties defined in dispatch call. The reducer function should always return a state value, no matter whether modified or not and has to match the initial state template. We can perform conditional actions based on the `type` and `payload` values in the `action` object. 

This a really good way to handle complex state logic. 



---



<a name="propdrilling">Prop drilling:</a>

Prop drilling is basically a situation when the same data is being sent at almost every level due to requirements in the final level. If the smaller component needs a property that is on a high scope, that property has to passed to all the upper level components(even though not used), in order to reach the needed. 

This is avoided using `useContext` hook or redux. Commonly occurs when there are a lot of components.



---



<a name="usecontext">React Context:</a> 

React Context is a way to manage state globally. It can be used together with the `useState` Hook to share state between deeply nested components more easily than with `useState` alone and solves the problem of prop drilling. 

> ###### Usage:

```react
import { useState, createContext, useContext } from "react";
import ReactDOM from "react-dom";

const PersonContext = createContext()
```

Next we'll use the `Context Provider` to wrap the parent(topmost to avoid prop drilling) component return and pass `value` to it(a global object). This value can now be accessed globally by all components in the same tree directly by using `useContext`. 

```react
const ContextAPI = () => {
  // ... 
  return (
    // Wrap the return of the topmost parent and pass values that we need to be global 
    <PersonContext.Provider value={{ removePerson, people }}>
      <h3>Context API / useContext</h3>
      <List />
    </PersonContext.Provider>
  );
};
const SinglePerson = ({ id, name }) => {
  // Accessing the Context value with useContext hook
  const { removePerson } = useContext(PersonContext);
  return (
    <div className='item'>
      <h4>{name}</h4>
      <button onClick={() => removePerson(id)}>remove</button>
    </div>
  );
};
export default ContextAPI;
```

In order to use the Context in a child component, we need to access it using the `useContext` Hook. 

> ###### Example:

```react
import { useState, createContext, useContext } from "react";
import ReactDOM from "react-dom";

const UserContext = createContext();

function Component1() {
  const [user, setUser] = useState("Jesse Hall");
  return (
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}

function Component2() {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 />
    </>
  );
}

function Component3() {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 />
    </>
  );
}

function Component4() {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 />
    </>
  );
}

function Component5() {
  const user = useContext(UserContext);
  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}

ReactDOM.render(<Component1 />, document.getElementById("root"));
```



---



<a name="customhooks">Custom hooks:</a>

Hooks are just reusable functions. When you have component logic that needs to be used by multiple components, we can extract that logic to a custom Hook. 

Custom Hooks start with `use`. Example: `useFetch`.

Instead of putting everything in a single component like this:

```react
const url = 'https://course-api.com/javascript-store-products'

const Example = () => {
  const [loading, setLoading] = useState(true)
  const [products, setProducts] = useState([])

  const getProducts = async () => {
    const response = await fetch(url)
    const products = await response.json()
    setProducts(products)
    setLoading(false)
  }

  useEffect(() => {
    getProducts()
  }, [url])
  console.log(products)
  return (
    <div>
      <h2>{loading ? 'loading...' : 'data'}</h2>
    </div>
  )
}
```

We can create a hook for the logic and make it reusable.

Move the fetch logic to a new file to be used as a custom Hook:

```react
// useFetch.js
import { useState, useEffect, useCallback } from 'react';

export const useFetch = (url) => {
  const [loading, setLoading] = useState(true);
  const [products, setProducts] = useState([]);

  const getProducts = async () => {
    const response = await fetch(url);
    const products = await response.json();
    setProducts(products);
    setLoading(false);
  };

  useEffect(() => {
    getProducts();
  }, [url]);
  return { loading, products };
};
```

Refactor the component to use our custom hook:

```react
import React, { useState, useEffect } from 'react'
import { useFetch } from './2-useFetch'

const url = 'https://course-api.com/javascript-store-products'

const Example = () => {
  const { loading, products } = useFetch(url)
  console.log(products)
  return (
    <div>
      <h2>{loading ? 'loading...' : 'data'}</h2>
    </div>
  )
}
```

It is as simple as that.



---



<a name="proptypes">Prop types:</a>

When we make API calls and other fetch requests, we can never assume that the received data is perfect and will have to prepare for anomalies and missing data.

This can be better handled by prop-types, which come built in with Create React App initialization. We can use it for runtime checking of received data, required condition, data type and set default values in case of anomalies.

> Importing:

```react
import { PropTypes } from 'prop-types';
```

> The main component:

```react
const Product = ({image, price, name}) => {
  return <article className='product'>
    <img src={image.url} alt={name} />
    <h4>{name}</h4>
    <p>${price}</p>
  </article>;
};
```

> Setting up prop-types for the component:

```react
Product.setTypes = {
  // property names with data types and isRequired 
  image:PropTypes.object.isRequired,
  name:PropTypes.string.isRequired,
  price:PropTypes.number.isRequired,
}
```

> Setting default values(for failure):

```react
Product.defaultProps = {
  name: 'default name',
  price: 5.99,
  image: {
    url: "https://developers.google.com/maps/documentation/streetview/images/error-image-generic.png"
  }
}
```

Combine all of them to have effective usage of `prop-types`. 



---



<a name="reactrouter">React Router:</a>











[Back to top](#nav)
