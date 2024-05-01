# Components

In React, there are two types of component: class-based and function-based. We've see a function-based component in our `App.jsx` file. But what are they and when do you use them?

The React community has largely shifted towards using function-based components with hooks as the preferred way to define components. Many libraries, tutorials, and examples now use this approach, making it easier to find resources and get support.

If you're working on a legacy project or an older codebase that primarily uses class components, you may need to continue using class components for consistency and compatibility.

For new projects or projects with modern requirements, function-based components with hooks are *generally preferred* due to their simplicity.

Let's have a look at the code.

## Function-based components

```jsx
import React, { useState } from 'react';

const MyComponent = () => {
  const [name, setName] = useState('World');
  return <h1>Hello, {name}!</h1>;
}
```

### Key Points

- Defined using JavaScript functions that return JSX.
- Can use React hooks such as `useState`, `useEffect`, `useContext`, etc., to manage state and side effects.
- Are simpler and more concise compared to class components.
- With the introduction of React hooks in React 16.8, function-based components gained more popularity and became the preferred way to define components in React.

## Class-based components

```jsx
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    return <h1>Hello, World!</h1>;
  }
}

```

### Key Points

- Defined using ES6 classes that extend `React.Component`.
- Have a `render()` method that returns JSX to define the component's UI.
- Can have state managed using `this.state` and lifecycle methods such as `componentDidMount`, `componentDidUpdate`, etc.
- Prior to React 16.8, class components were the primary way to define stateful components in React.


## The same component, two ways

Since we've seen a counter, let's look at breaking that out and making it a separate component. We'll start with the function-based counter, as this is the modern approach.

What you *should* notice, is that both have very different methods for telling you when a component was *mounted* (loaded), or updated, and how they maintain state.

Function-based utilises React hooks, like `useEffect` or `useState`, whilst class-based utilises the arcane `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` lifecycle methods.

### Function-based Counter

```jsx
import React, { useState, useEffect } from 'react';

const Counter = () => {
  // Initialize state using useState hook
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Component mounted');
    // Cleanup function (optional)
    return () => {
      // Code to execute on component unmount
      console.log('Component unmounted');
    };
  }, []); // Empty dependency array means it only runs once after initial render

  useEffect(() => {
    console.log('Component updated');
    console.log('Previous count:', count); 
  }, [count]); // Run the effect whenever the 'count' state changes

  // Increment count
  const incrementCount = () => {
    setCount(prevCount => prevCount + 1);
  };

  // Decrement count
  const decrementCount = () => {
    setCount(prevCount => prevCount - 1);
  };

  return (
    <div>
      <h2>Counter: {count}</h2>
      <button onClick={incrementCount}>Increment</button>
      <button onClick={decrementCount}>Decrement</button>
    </div>
  );
};

export default Counter;

```

### Hooks

While function-based components don't have explicit *lifecycle* methods like class components, hooks enable function components to achieve the same functionality in a more modular and composable way. 

**useState Hook**
- Equivalent to `this.state` in class components.
- Allows functional components to have local state.
- Replaces the need for `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` lifecycle methods related to state management.

**useEffect Hook**
- Equivalent to `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` lifecycle methods combined.
- Allows functional components to perform side effects (such as data fetching, subscriptions, or DOM manipulation) after render.
- Accepts a function that contains the code to execute after render, and can optionally specify cleanup code.

**Other Hooks**
- React provides additional hooks like `useContext`, `useReducer`, `useCallback`, `useMemo`, etc., which offer functionality similar to specific lifecycle methods or address other aspects of component behavior.

### Class-based Counter

```jsx
// Counter.jsx

import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    // Initialize state
    this.state = {
      count: 0
    };
  }

  // Lifecycle method: componentDidMount
  componentDidMount() {
    console.log('Component mounted');
  }

  // Lifecycle method: componentDidUpdate
  componentDidUpdate(prevProps, prevState) {
    console.log('Component updated');
    console.log('Previous count:', prevState.count);
    console.log('Current count:', this.state.count);
  }

  // Increment count
  incrementCount = () => {
    this.setState(prevState => ({
      count: prevState.count + 1
    }));
  }

  // Decrement count
  decrementCount = () => {
    this.setState(prevState => ({
      count: prevState.count - 1
    }));
  }

  render() {
    return (
      <div>
        <h2>Counter: {this.state.count}</h2>
        <button onClick={this.incrementCount}>Increment</button>
        <button onClick={this.decrementCount}>Decrement</button>
      </div>
    );
  }
}

export default Counter;

```

#### Lifecycle

Lifecycle methods in React are special methods that are automatically invoked at specific points in a component's *lifecycle*. A lifecycle can be absolutely thought of in exactly the same terms of any living thing - from birth to death.

These methods allow developers to hook *(and lifecycle events hare replaced with named hooks in function-based components!)* into various stages of a component's lifecycle and perform tasks - such as setting up initial state, fetching data from APIs, updating the DOM in response to changes, and cleaning up resources when a component is removed from the DOM. 

In React, lifecycle methods follow a consistent naming convention where they are formatted as component-verb-action. The prefix "component" indicates that the method belongs to a React component, followed by a verb that describes the action being performed, and an optional action or event.

React tends to use the verb "Did" to check something happened after an event, and "Will" to do something before an event.

There are quite a few lifecycle events, but a few key ones are:

**componentDidMount**

This method is called immediately *after* a component is mounted (i.e., inserted into the DOM). It is commonly used to perform tasks such as fetching data from APIs, setting up event listeners, or initializing third-party libraries. componentDidMount is particularly useful for initializing components and fetching data that the component needs to render.

**componentDidUpdate**

This method is called immediately *after* a component's props or state have been updated, and the component has been re-rendered. It is commonly used to perform tasks such as updating the DOM in response to state or prop changes, fetching new data when props change, or triggering side effects based on state changes. componentDidUpdate allows developers to respond to changes in the component's data and update the UI accordingly.

**componentWillUnmount**

This method is called immediately *before* a component is unmounted (i.e., removed from the DOM). It is commonly used to perform cleanup tasks such as removing event listeners, clearing timers, or unsubscribing from observables. componentWillUnmount allows developers to clean up resources and prevent memory leaks when a component is no longer needed.

---

Okay, so we've seen how components are made, and two different ways. At the moment we only have one page though, so we'll need to fix that so we can start using more than one component.

Let's look at [routing >>](chapter4.md)