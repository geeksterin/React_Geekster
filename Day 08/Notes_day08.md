## Introduction to State in ReactJS:

State is a fundamental concept in ReactJS. It represents the internal state of a component and it can be changed over time based on user interactions or other events. In simple terms, state is a JavaScript object that holds some information that can be modified over time, which ultimately updates the UI.

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