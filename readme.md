# React Basics

React Documentation: https://reactjs.org/docs/getting-started.html

React is a JavaScript library for building user interfaces. It was developed by Facebook and has gained widespread adoption in the web development community due to its simplicity, efficiency, and flexibility.

## Required Knowledge

Before starting with React, this guide expect you to have a knowledge of HTML and JavaScript. You don't *have* to, but it will make your life a whole lot easier.

## Why React?

- **Reusable Components** 
    - React allows you to break down your UI into reusable components, making it easier to manage and maintain your codebase.
- **Virtual DOM** 
    - React uses a virtual DOM to efficiently update the *actual* DOM, resulting in faster rendering and improved performance.
- **Declarative Syntax** 
    - React uses a declarative syntax, which makes it easier to understand and write UI components.
- **Component-Based Architecture** 
    - React promotes a component-based architecture, enabling developers to build complex UIs by composing smaller, reusable components.
- **Large Ecosystem** 
    - React has a large ecosystem of libraries, tools, and community support, making it easy to integrate with other technologies and solve various development challenges.

### Popularity

React has become one of the most popular JavaScript libraries for building user interfaces, and it is widely used in both small-scale projects and large-scale applications. Many companies, including Facebook, Instagram, Airbnb, and Netflix, use React to power their web applications.

## Explaining Components in React: A Tale of Building Blocks
>Once upon a time, in the bustling town of Webville, there lived a group of craftsmen known as Web Developers. These developers were tasked with creating marvelous structures called Web Applications that would enchant users far and wide.
>
>In the heart of Webville stood a grand workshop, where the most skilled developers gathered to craft their creations. Inside this workshop, there was a special room known as the *Component Forge*.
>
>Now, imagine each web application as a majestic castle, with towers, walls, and courtyards. Just like a castle is made up of various building blocks, a web application is composed of smaller pieces called Components.
>
>In the Component Forge, developers crafted these Components with great care and attention to detail. Each Component had its own unique purpose and functionality, much like the different rooms and chambers within a castle.
>
>Some Components were like sturdy walls, providing structure and stability to the application. Others were like elegant windows, allowing users to glimpse into the inner workings of the application.
>
>As the developers worked tirelessly in the Component Forge, they discovered the power of reusability. They realized that they could create a Component once and use it in multiple places throughout their application, much like using the same architectural design for different parts of a castle.
>
>But the *true* magic of Components lay in their ability to communicate with one another. Just as the inhabitants of a castle would pass messages from one chamber to another, Components could send and receive information, allowing the application to respond dynamically to user interactions.
>
>As time passed, the Component Forge became the heart and soul of Webville. Developers from far and wide came to learn the art of Component crafting, and soon, the town was filled with enchanting web applications built upon the sturdy foundation of Components.
>
>And so, the tale of Components in React serves as a reminder of the power of modularity and reusability in web development. Just as the craftsmen of Webville built magnificent castles with their building blocks, so too can developers create wondrous web applications with the magical Components of React.
>
>May your journey through the Component Forge be filled with creativity, innovation, and endless possibilities.

### Components in a Nutshell

Components in React are modular, reusable building blocks used to create user interfaces. They encapsulate UI elements and functionality into self-contained units, allowing you to break down complex UIs into smaller, manageable parts. Each component can have its own state, properties, and lifecycle, enabling dynamic and interactive user experiences.

## JSX

JSX (JavaScript XML) is a syntax extension used in React to define the structure of user interfaces by mixing HTML-like syntax with JavaScript code. It allows developers to write UI components in an intuitive and declarative manner, resembling the structure of HTML, while still leveraging the power of JavaScript for dynamic functionality. 

JSX makes it easier to visualize and understand the structure of the UI, as it closely resembles the final HTML that will be rendered in the browser. Also, JSX enables the embedding of JavaScript expressions within curly braces `{}` directly within the markup, facilitating dynamic content generation and logical operations within the UI components. 

## Virtual DOM

React uses a *virtual DOM* (Document Object Model) to efficiently update the actual DOM, resulting in faster rendering and improved performance. Here's how it works:

1. **Virtual DOM Representation**

When a React component's state or properties change, React doesn't immediately update the *actual* DOM. Instead, it creates a virtual representation of the DOM called the virtual DOM. This virtual DOM is a lightweight copy of the actual DOM, represented as a tree structure of React elements.

2. **Reconciliation Algorithm**

React then compares the current virtual DOM with the previous one to identify the differences, or "diffs," between the two. It determines which parts of the virtual DOM need to be updated based on the changes in component state or properties.


3. **Minimal DOM Updates**

Once the differences are identified, React calculates the *most efficient* way to update the actual DOM to reflect these changes. Rather than updating the entire DOM tree, React *only* updates the specific parts of the DOM that have changed, minimizing the number of DOM manipulations required.


4. **Batched Update**

React batches multiple DOM updates into a single batch, optimizing performance by reducing unnecessary re-renders and minimizing layout thrashing. This ensures that updates are processed in an efficient and predictable manner, resulting in smoother and faster rendering.

5. **Asynchronous Rendering**

React also utilizes asynchronous rendering techniques to prioritize and schedule updates based on their priority and importance. This allows React to maintain a responsive UI by ensuring that high-priority updates are processed quickly, while lower-priority updates are deferred until the browser is idle.

## What does a component look like?

Good question. Here's a very basic example - this doesn't compile, it's just to show you about a component, JSX and the virtual DOM!

```js
// Component example
class MyComponent extends React.Component {
  render() {
    return <h1>Hello, World!</h1>;
  }
}

// JSX example
const element = <div>Hello, {name}</div>;

// Virtual DOM example
ReactDOM.render(element, document.getElementById('root'));
```

---

Let's start working with React by creating a simple app.

[Chapter 1 - Creating A React App >>](chapter1.md)