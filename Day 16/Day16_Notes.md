# Props Drilling

In React, props drilling refers to the process of passing props down through multiple layers of components to reach a specific component that needs access to that prop. This can result in code that is difficult to read and maintain, especially as the number of components and props grows.

Here's an example of props drilling:

```
function GrandParent(props) {
  return (
    <Parent name={props.name}>
  );
}

function Parent(props) {
  return (
    <Child name={props.name}>
  );
}

function Child(props) {
  return (
    <div>{props.name}</div>
  );
}

function App() {
  return (
    <GrandParent name="John" />
  );
}
```
- In this example, the name prop is passed down through two layers of components (GrandParent and Parent) before it reaches the Child component where it is finally used. This can make it difficult to trace where a particular prop is coming from and where it's being used.

# Context API

- Explanation
The Context API is a feature of React that allows data to be passed down the component tree without the need for props drilling. It provides a way to share data between components that are not directly related to each other, without having to pass the data through every intermediate component.

- Context is essentially a global object that can hold any data that needs to be shared across multiple components. It consists of three main parts:

1. Context object
2. Provider component
3. Consumer component

- The problem Context API solves
Context API solves the problem of props drilling. When props need to be passed through multiple layers of components, it can lead to code that is hard to read, understand, and maintain. Context API provides an elegant solution to this problem by allowing data to be shared directly between components without having to pass it through intermediate components.

# Context API Setup
- Here's how you can set up the Context API:

1. Create
First, create a new context object using the createContext() function:

```
const MyContext = React.createContext(defaultValue);

```

- The createContext() function creates a new context object. The defaultValue parameter is optional and specifies the default value for the context. If a component tries to consume the context without a matching provider, it will use the default value.

2. Provide
Next, use the Provider component to provide the context to the child components:

```
<MyContext.Provider value={/* some value */}>
  {/* child components */}
</MyContext.Provider>
```
- The Provider component makes the context available to all child components.


3. Consume
Finally, use the Consumer component to consume the context in a child component:

The Consumer component provides access to the context value in a child component.

Alternatively, you can use the useContext() hook to consume the context in a child component:

```
const value = useContext(MyContext);
```
- The useContext() hook provides access to the context value in a functional component.

# useContext()

- useContext() is a React hook that allows you to consume a context object in a functional component. It takes a context object as an argument and returns the current context value.

- Here's an example of using useContext() to consume a context object:
```
const MyContext = React.createContext();

function ChildComponent() {
  const contextValue = useContext(MyContext);

  return <div>{contextValue}</div>;
}

function ParentComponent() {
  return (
    <MyContext.Provider value="Hello, world!">
      <ChildComponent />
    </MyContext.Provider>
  );
}
```
- In this example, the MyContext object is created using createContext(), and a value of "Hello, world!" is provided using the Provider component. The ChildComponent component consumes the context value using useContext(), and renders the value inside a div. Finally, the ParentComponent component provides the context to its child components using the Provider component.


# Theme Context

- One common use case for the Context API is to create a "theme" context that can be used to style components throughout an application. Here's an example of how this might work:

```
const ThemeContext = React.createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme(theme === "light" ? "dark" : "light");
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

function Button() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <button onClick={toggleTheme} style={{ background: theme === "light" ? "#fff" : "#000", color: theme === "light" ? "#000" : "#fff" }}>
      Toggle Theme
    </button>
  );
}

function App() {
  return (
    <ThemeProvider>
      <Button />
    </ThemeProvider>
  );
}
```
- In this example, a ThemeProvider component provides a ThemeContext object to its child components. The ThemeProvider component also keeps track of the current theme using useState(), and provides a toggleTheme function that can be used to toggle the theme between "light" and "dark". The Button component consumes the theme and toggleTheme values from the ThemeContext using useContext(), and uses them to toggle the theme and style the button accordingly. Finally, the App component renders the ThemeProvider and Button components.

# Auth Context
- Another common use case for the Context API is to create an "auth" context that can be used to manage user authentication throughout an application. Here's an example of how this might work:

```
const AuthContext = React.createContext();

function AuthProvider({ children }) {
  const [user, setUser] = useState(null);

  const login = (email, password) => {
    // make API request to authenticate user
    setUser({ email });
  };

  const logout = () => {
    // make API request to log out user
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
}

function PrivateRoute({ component: Component, ...rest }) {
  const { user } = useContext(AuthContext);

  return (
    <Route {...rest} render={props => (user ? <Component {...props} /> : <Redirect to="/login" />)} />
  );
}

function LoginPage() {
  const { login } = useContext(AuthContext);
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  const handleSubmit = e.preventDefault();
login(email, password);
};

return (

  <form onSubmit={handleSubmit}>
    <input type="email" value={email} onChange={e => setEmail(e.target.value)} />
    <input type="password" value={password} onChange={e => setPassword(e.target.value)} />
    <button type="submit">Login</button>
  </form>
);

function App() {
return (
<AuthProvider>
<Router>
<Switch>
<Route path="/login" component={LoginPage} />
<PrivateRoute path="/" component={HomePage} />
</Switch>
</Router>
</AuthProvider>
);
}

```
- In this example, an `AuthProvider` component provides an `AuthContext` object to its child components. The `AuthProvider` component also keeps track of the current user using `useState()`, and provides `login` and `logout` functions that can be used to authenticate and deauthenticate the user. The `PrivateRoute` component consumes the `user` value from the `AuthContext` using `useContext()`, and renders a private route that requires the user to be authenticated. The `LoginPage` component consumes the `login` function from the `AuthContext` using `useContext()`, and provides a form for the user to log in. Finally, the `App` component renders the `AuthProvider`, `Router`, `Switch`, `Route`, `PrivateRoute`, `LoginPage`, and `HomePage` components.

### Usage

The Context API can be used in a variety of situations where data needs to be passed down the component tree without manually passing it through each intermediate component. Some common use cases include:

- Theming: use a "theme" context to provide a consistent visual style throughout an application.
- Authentication: use an "auth" context to manage user authentication and authorization throughout an application.
- Language: use a "language" context to provide translations and internationalization throughout an application.
- Settings: use a "settings" context to manage user preferences and application settings throughout an application.
- Data: use a "data" context to provide shared data and state throughout an application.

- In general, the Context API should be used sparingly and only for data that needs to be shared across multiple components in the tree. Overuse of the Context API can lead to a complex and hard-to-maintain codebase, and can make it difficult to reason about the flow of data through the application.
