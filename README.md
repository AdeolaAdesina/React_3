# React Components

## React Components

React applications are made of components.

What’s a component?

A component is a small, reusable chunk of code that is responsible for one job. That job is often to render some HTML (or JSX) and re-render it when some data changes.

Take a look at the code below. This code will create and render a new React component:

```
import React from 'react';
import ReactDOM from 'react-dom/client';

function MyComponent() {
  return <h1>Hello world</h1>;
}

ReactDOM.createRoot(
document.getElementById('app')
).render(<MyComponent />);
```


A lot of these look unfamiliar but do not worry. We are going to unpack that code, one small piece at a time. By the end of this lesson, you’ll understand how to build a React component!



## Import React

The first React component we created in the last exercise started with importing react. The line that did this is:

```
import React from 'react';
```

This creates an object named React, which contains methods necessary to use the React library. React is imported from the 'react' package, which should be installed in your project as a dependency. With the object, we can start utilizing features of the react library!

By importing the library, we can use important features such as Hooks, which we’ll explore in detail later.



## Import ReactDOM

Another import we need in addition to React is ReactDOM:

```
import ReactDOM from 'react-dom/client';
```

The methods imported from 'react-dom' interact with the DOM.

The methods imported from 'react' do not deal with the DOM at all. They don’t engage directly with anything that isn’t part of React.

To clarify: the DOM is used in React applications, but it isn’t part of React. After all, the DOM is also used in countless non-React applications. Methods imported from 'react' are only for pure React purposes, such as creating components or writing JSX elements.



## Create a Function Component.

You’ve learned that a React component is a small, reusable chunk of code that is responsible for one job, which often involves rendering HTML and re-rendering it whenever some data changes.

It’s useful to think of components as smaller pieces of our interface. Combined, they are the building blocks that make up a React application. In a website, we can create a component for the search bar, another component for the navigation bar, and another component for the dashboard content itself.

Here’s another fact about components: we can use JavaScript functions to define a new React component. This is called a function component.

In the past, React components were defined using Javascript classes. But since the introduction of Hooks (something we’ll discuss later), function components have become the standard in modern React applications.

After we define our functional component, we can use it to create as many instances of that component as we want.

Let’s take a look at the example from the first exercise:

```
import React from 'react';

function MyComponent() {
  return <h1>Hello, I'm a functional React Component!</h1>;
}

export default MyComponent;
```

On the third line, a function is defined with the name MyComponent. Inside, the function returns a React element in JSX syntax:

```
return <h1>Hello, I'm a functional React Component!</h1>;
```


Combined, this makes a basic React functional component.

On the last line of the above code block, MyComponent is exported so it can be used later.

A lot of it is still unfamiliar, but you can understand more than you could before! Let’s keep going!



## Name a Functional Component

Good! Creating a JavaScript function is the way to declare a new functional component.

When you declare a new functional component, you need to give that component a name. On our finished component, our component’s name was MyComponent:

```
function MyComponent() {
  return <h1>Hello world</h1>;
}
```

Function component names must start with capitalization and are conventionally created with PascalCase! Due to how JSX tags are compiled, capitalization indicates that it is a React component rather than an HTML tag.

This is a React-specific nuance! If you are creating a component, be sure to name it starting with a capital letter so it interprets it as a React component. If it begins with a lowercase letter, React will begin looking for a built-in component such as div and input instead and fail.



##  The Return Keyword in Functional Components

When we define a functional component, we essentially define a factory that can build the appropriate combination of elements every time we reference its name. It builds it by consulting a set of instructions that you must provide.

If you’re thinking, “That sounds just like what a regular Javascript function is for”, then you’re right! Functional components can be thought of in a very similar vein to regular Javascript functions, except that their job is to assemble a portion of the interface based on instructions given!

Let’s talk a bit more about these instructions.

For starters, these instructions should take the form of a function declaration body. That means that they will be delimited by curly braces, like this:

```
function Button() {
  // Instructions go here, between the curly braces.
}
```

Our instructions can include a combination of markup, CSS, and JavaScript to produce the desired result. The one thing we must always include is a return statement.

The function is expected to produce JSX code that can be used to render something onto the browser screen. Thus, when we define functional components, we must return a JSX element.

```
function BackButton() {
 return <button>Back To Home</button>;
}
```


Of course, this doesn’t quite make ``` <button>Back To Home</button> ``` render onto the browser screen yet. We’ve only defined our component.

Let’s keep going so we can see how to render it and why the return statement was necessary!



## Importing and Exporting React Components

There’s a little bit more work we have to do before we can use our defined component and have it rendered onto the DOM.

We previously mentioned that a React application typically has two core files: App.js and index.js. 

App.js file is the top level of your application, and index.js is the entry point.

So far, we’ve defined the component inside of App.js, but because index.js is the entry point, we have to export it to index.js to render.

Components in React are great because they are reusable. We can keep our component pieces separated, organized, and reusable by putting them into separate files and exporting them to where we need them.

To export them, we can prefix it with the export declaration and specify if it is a default or named export. In this case, we’ll stick with default. If you need a refresher on export, peruse the MDN web docs.

After the function component definition, in App.js, we can default export our component like so:

```
export default MyComponent;
```

We can head into our index.js file to import our component from './App':

```
import MyComponent from './App';
```

This will allow us to use MyComponent in index.js.


E.g

![Screenshot 2023-11-17 at 05 00 42](https://github.com/AdeolaAdesina/React_3/assets/29931071/17d74e20-441f-4f7b-994c-83710a3d93d9)

![Screenshot 2023-11-17 at 05 00 47](https://github.com/AdeolaAdesina/React_3/assets/29931071/40b025b9-d75b-4fb6-b7d8-19ab4d35ef5b)



## Using and Rendering a Component

Now that we have a defined function component, we can start using it.

We can use it with an HTML-like syntax that resembles a self-closing tag:

```
<MyComponent />
```

If you need to nest other components in between, you may also use an opening and corresponding closing tag structure:

```
<MyComponent>
  <OtherComponent />
</MyComponent>
```

However, to render our component to the browser, we must rely on the ```.createRoot()``` and ```.render()``` methods from the react-dom library. This should be done in our entry point, index.js.

First, we call the createRoot method to create a React root container for displaying content. React applications typically have a single root DOM node, and everything inside it is managed by React DOM.

In other words, we give createRoot a DOM element to render in, and React will take over managing the DOM inside it.

Here’s an example:

```
ReactDOM.createRoot(document.getElementById('app'));
```

Great! Let’s break it down a bit further:

- document.getElementById('app') returns a DOM element from index.html.
- .createRoot() receives the DOM element as the first argument and creates a root for it.
- .createRoot() returns a reference to the root container on which you can call methods like .render().
  
After the root is created, all that’s left to do is call the .render() method on the returned root and display the React component like so:

```
ReactDOM.createRoot(document.getElementById('app')).render(<MyComponent />);
```

From here, React will display ```<MyComponent />``` in the root and make it appear on the screen.

In an application fully built with React, you will only need to do this once. Once this is set up, React will manage the DOM of your application, and any updates to the UI is taken care of efficiently. Adding more components should take place in your top-level App.js file.

E.g

![Screenshot 2023-11-17 at 05 08 03](https://github.com/AdeolaAdesina/React_3/assets/29931071/bd5ff5d4-e5e8-4ca2-8205-c86718aad72b)

![Screenshot 2023-11-17 at 05 08 07](https://github.com/AdeolaAdesina/React_3/assets/29931071/82120734-809d-4609-b081-74594bedc580)

![Screenshot 2023-11-17 at 05 08 18](https://github.com/AdeolaAdesina/React_3/assets/29931071/257effb0-10a4-4f42-8808-be90dd20a8df)





