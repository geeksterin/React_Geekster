# Notes

## Pure Function
A pure function is a function that always returns the same output given the same input, and it does not modify the data outside of its scope. Pure functions are predictable and easy to test, which makes them very useful in functional programming. In React, pure functions are used to render components based on their props and state.

## Side Effects
Side effects are any effects that a function has on the outside world, such as changing the DOM, making API calls, or manipulating global variables. In React, side effects should be handled carefully, as they can cause performance issues and make the code harder to reason about.


## How to Perform Side Effects in React Functional Component
In React, side effects can be performed using the useEffect() hook. The useEffect() hook is a built-in React hook that allows you to perform side effects in functional components. The useEffect() hook takes two arguments: a function that performs the side effect, and an array of dependencies that specify when the side effect should be executed.

- Here is an example of how to use the useEffect() hook to perform a side effect in a React functional component:

```js
import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default MyComponent;
```
In this example, the useEffect() hook is used to update the document title whenever the count state changes.



## Intro to useEffect() Hook
- The useEffect() hook is a built-in React hook that allows you to perform side effects in functional components. It is similar to the componentDidMount(), componentDidUpdate(), and componentWillUnmount() lifecycle methods in class components. The useEffect() hook takes a function as its first argument, which is called after the component has rendered. It also takes an array of dependencies as its second argument, which specifies when the effect should be executed.

- Here is an example of how to use the useEffect() hook in a React functional component:

```js
import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log(`You clicked ${count} times`);
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default MyComponent;
```
In this example, the useEffect() hook is used to log the number of times the button has been clicked whenever the count state changes.

## What is the Lifecycle of Components?
The lifecycle of a component in React refers to the series of stages that a component goes through from the time it is created to the time it is destroyed. There are three main phases in the lifecycle of a component: mount, update, and unmount.

## Phases of the Lifecycle
The lifecycle of a component in React is divided into three phases: mount, update, and unmount.

## Mount Phase
The mount phase is the first phase in the lifecycle of a component. It occurs when a component is created and added to the DOM for the first time. The mount phase has three main methods:

- constructor(): This method is called when a component is first created. It is used to set the initial state and bind event handlers.

- render(): This method is called to render the component on the screen. It returns a React element that represents the component.
- componentDidMount(): This method is called after the component has been mounted to the DOM. It is used to perform any side effects, such as making API calls or setting up event listeners.


- Update Phase
The update phase occurs when a component is updated due to changes in its props or state. The update phase has two main methods:

- render(): This method is called to render the updated component on the screen.
- componentDidUpdate(): This method is called after the component has been updated. It is used to perform any side effects, such as updating the DOM or making API calls.


## Unmount Phase

- The unmount phase occurs when a component is removed from the DOM. The unmount phase has one main method:

- componentWillUnmount(): This method is called before the component is removed from the DOM. It is used to clean up any resources used by the component, such as removing event listeners or cancelling API requests.

## Examples for Demonstrating
### Mount Phase
Here is an example of a component that uses the mount phase to perform a side effect:

```js
import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []);

  if (!data) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      <p>{data}</p>
    </div>
  );
}

export default MyComponent;
```
In this example, the useEffect() hook is used to fetch data from an API when the component is first mounted. The data is stored in state and rendered when it is available.


## Update Phase
Here is an example of a component that uses the update phase to perform a side effect:

```js
import React, { useState, useEffect } from 'react';

function MyComponent(props) {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(`https://api.example.com/data/${props.id}`)
      .then(response => response.json())
      .then(data => setData(data));
  }, [props.id]);

  if (!data) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      <p>{data}</p>
    </div>
  );
}

export default MyComponent;
```
In this example, the useEffect() hook is used to fetch data from an API whenever the props.id changes. This allows the component to update its data when the user selects a different item.

## Unmount Phase
Here is an example of a component that uses the unmount phase to clean up resources:

```js
import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [timerId, setTimerId] = useState(null);

  useEffect(() => {
    const id = setInterval(() => {
      console.log('Tick');
    }, 1000);

    setTimerId(id);

    return () => {
      clearInterval(timerId);
    };
  }, []);

  return (
    <div>
      <p>Timer running...</p>
    </div>
  );
}

export default MyComponent;
```

In this example, the useEffect() hook is used to start a timer when the component is mounted. The timer is cleaned up when the component is unmounted by returning a function from the useEffect() hook that calls clearInterval().


# Assignment

## Solve the given freecodecamp questions: 

1. [freecodecamplink](https://www.freecodecamp.org/learn/front-end-development-libraries/react/use-the-lifecycle-method-componentwillmount)

2. [freecodecamplink](https://www.freecodecamp.org/learn/front-end-development-libraries/react/use-the-lifecycle-method-componentdidmount)

3. [freecodecamplink](https://www.freecodecamp.org/learn/front-end-development-libraries/react/optimize-re-renders-with-shouldcomponentupdate)


# Interview Questions 

1. What is a pure function and how is it different from a function with side effects?
2. How can you perform side effects in a React functional component?
3. What is the difference between useEffect() and componentDidMount() in React?
4. What is the purpose of the key attribute in React list rendering?
5. How can you conditionally render components in React?
6. What is the difference between props and state in React?
7. What are the phases of the React component lifecycle?
8. How can you prevent unnecessary renders in React?
9. How can you bind event handlers in React components?
10. How can you pass data from a parent component to a child component in React?