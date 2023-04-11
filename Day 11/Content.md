# Notes

## API:

In React, you can make API calls to retrieve data from a remote server using a variety of methods, including the Fetch API and the Axios library. You can use these methods to fetch data from a server and then update the state of your React component with the retrieved data.

- Here's an example of how to make an API call in React using the Fetch API:

```js
import React, { useState, useEffect } from "react";

function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch("https://api.example.com/data")
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []);

  return (
    <div>
      {data.map((item) => (
        <p key={item.id}>{item.name}</p>
      ))}
    </div>
  );
}

export default App;
```

## API Call on Button Click:

To make an API call in React on button click, you can add a click event handler to your button and then use one of the API methods mentioned above to fetch data from a server.

- Here's an example of how to make an API call in React on button click using the Axios library:

```js
import React, { useState } from "react";
import axios from "axios";

function App() {
  const [data, setData] = useState([]);

  const handleClick = () => {
    axios
      .get("https://api.example.com/data")
      .then((response) => setData(response.data));
  };

  return (
    <div>
      <button onClick={handleClick}>Fetch Data</button>
      {data.map((item) => (
        <p key={item.id}>{item.name}</p>
      ))}
    </div>
  );
}

export default App;
```

## Conditional Rendering:

Conditional rendering in React is done using conditional statements like if, else, and ternary operators. You can use these statements to conditionally render elements based on the state of your React component.

- Here's an example of how to conditionally render an element in React based on a boolean value:

```js
import React, { useState } from "react";

function App() {
  const [isVisible, setIsVisible] = useState(false);

  const handleClick = () => {
    setIsVisible(!isVisible);
  };

  return (
    <div>
      <button onClick={handleClick}>Toggle Visibility</button>
      {isVisible && <p>Hello World!</p>}
    </div>
  );
}

export default App;
```

## List Rendering:

In React, you can render lists of elements by using the map() function on an array of data. This allows you to dynamically generate elements based on the data in your component's state.

- Here's an example of how to render a list of items in React using the map() function:

```js
import React, { useState } from "react";

function App() {
  const [items, setItems] = useState(["Apple", "Banana", "Orange"]);

  return (
    <ul>
      {items.map((item) => (
        <li key={item}>{item}</li>
      ))}
    </ul>
  );
}

export default App;
```

## Key and Value:

In React, the key and value properties are often used when rendering lists of elements. The key property is a unique identifier for each element in the list, and the value property is the data to be rendered for each element.
Here's an example of how to render a list of items in React with key and value properties:

```js
import React, { useState } from "react";

function App() {
  const [items, setItems] = useState([
    { id: 1, name: "Apple" },
    { id: 2, name: "Banana" },
    { id: 3, name: "Orange" },
  ]);

  return (
    <ul>
      {items.map((item) => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}

export default App;
```

In this example, each item in the list has an `id` and a `name` property, and the `key` property is set to the `id` of each item. This allows React to efficiently update the list when changes are made to the state.

I hope these notes help you better understand the topics of API, API call on button click, conditional rendering, list rendering, key and value in the context of React. Let me know if you have any further questions or if there's anything else I can help you with!

# Assignment

- Create a React component that retrieves data from an API and displays a list of items. The component should include a button that, when clicked, fetches data from the API and updates the list.

- The list of items should be rendered conditionally based on whether or not data has been fetched from the API. If data has been fetched, the list should be rendered using the map() function.

- Each item in the list should have a unique key and display a name and a description.

- Hers is the Api - [Api](https://fakestoreapi.com/products/1)


# Interview Questions : 

1. What is an API and how does it work with React?
2. Can you explain the difference between a GET and POST request in an API call?
3. How do you handle errors in an API call in React?
4. How do you make an API call when a button is clicked in React?
5. What is conditional rendering in React and why is it important?
6. Can you explain the difference between if-else statements and ternary operators for conditional rendering in React?
7. What is list rendering in React and how is it different from conditional rendering?
8. What is the purpose of the "key" prop in list rendering?
9. How do you update a list in React when new data is added?
10. Can you explain the importance of React's virtual DOM in optimizing list rendering performance?