## Introduction to State in ReactJS:

In ReactJS, a "state" is an object that holds information about the current state of a component. It represents the data that the component needs to render itself and respond to user interactions.

A state can be initialized with default values when a component is first created, and it can be updated over time in response to events such as user input, network requests, or other changes in the application's state.

Updating the state of a component causes React to re-render the component and any child components that depend on its state. This allows the UI to update dynamically based on changes in the underlying data.

States in ReactJS are typically managed using the useState hook, which is a built-in function that allows functional components to manage state. Class-based components can also manage state using the this.state object and the setState method.
 
### Benefits and use cases:
The main benefit of using state in ReactJS is that it allows us to build dynamic and interactive user interfaces. State enables components to change their behavior or appearance based on the user input or other events, without having to reload the entire page. It also makes it easier to manage the data flow between components and to share data between them.

### Re-rendering explanation:
When a component's state changes, ReactJS automatically re-renders the component and any child components that depend on its state. This is because ReactJS uses a virtual DOM (Document Object Model), which is a lightweight representation of the actual DOM. The virtual DOM is updated based on changes in state and then ReactJS compares the new virtual DOM with the previous one to determine the minimal changes needed to update the actual DOM. This makes the UI updates efficient and fast.

Simple Counter using events and state using multiple components:
Here's an example of a simple counter component that uses state:

```
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const handleIncrement = () => {
    setCount(count + 1);
  };

  const handleDecrement = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
    </div>
  );
}

export default Counter;
```

In this example, we use the useState hook to create a count state variable and a setCount function to update it. We also define two event handlers, handleIncrement and handleDecrement, which update the count state variable when the corresponding buttons are clicked. Finally, we render the current count value and the two buttons that trigger the event handlers.

### Calling different event handlers using onClick:
To call different event handlers using onClick, we can pass a different function to the onClick prop for each button. Here's an example:

```
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const handleIncrement = () => {
    setCount(count + 1);
  };

  const handleDecrement = () => {
    setCount(count - 1);
  };

  const handleReset = () => {
    setCount(0);
  };

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
      <button onClick={handleReset}>Reset</button>
    </div>
  );
}

export default Counter;
```

In this example, we define a new event handler handleReset that resets the count state variable to zero. We then add a new button that calls this function when clicked.