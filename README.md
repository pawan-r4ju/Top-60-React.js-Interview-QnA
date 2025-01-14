# Top-60-React.js-Interview-QnA

### **1\. What is React, and why is it used?**

React is a **JavaScript library** developed by Facebook for building **user interfaces** (UIs), especially for single-page applications (SPAs). It allows developers to create reusable components, manage complex UIs efficiently, and build interactive applications.

Key reasons for using React:

- **Component-Based Architecture**: Breaks the UI into smaller, reusable pieces (components).
- **Virtual DOM**: Optimizes updates to the actual DOM, improving performance.
- **Declarative Syntax**: Developers describe _what_ they want the UI to look like, and React handles the _how_.
- **Large Ecosystem**: Supports tools like Redux, React Router, and more for seamless development.

---

### **2\. What are the main features of React?**

- **Virtual DOM**: React creates an in-memory DOM to improve rendering performance by applying changes only to updated parts of the UI.
- **Components**: Small, self-contained building blocks that represent parts of the UI.
- **JSX**: A syntax that lets you write HTML in JavaScript, making code readable and concise.
- **One-Way Data Binding**: Data flows in one direction, making applications predictable and easier to debug.
- **React Hooks**: Enable state and lifecycle features in functional components without writing classes.

---

### **3\. Explain the Virtual DOM and how it works.**

The Virtual DOM (VDOM) is a lightweight, in-memory representation of the actual DOM.\
**How it works**:

1.  When the state or props of a component change, React updates the virtual DOM instead of the real DOM directly.
2.  React compares the updated VDOM with the previous one (using a process called **diffing**).
3.  It calculates the minimal number of changes and applies those to the actual DOM.

**Advantages**:

- Faster updates since the actual DOM manipulations are minimized.
- Better performance for dynamic applications.

---

### **4\. What are components in React?**

Components are the building blocks of a React application. They are **JavaScript functions or classes** that:

- Take **props** as input.
- Return a piece of UI (JSX).
- Can have their own **state** and **lifecycle** (if class-based).

**Types**:

- **Functional Components**: Stateless by default, use React hooks for state/lifecycle.
- **Class Components**: Stateful, use lifecycle methods and `this` for state handling.

Example of a Functional Component:

```bash
function Greeting({ name }) {
 return <h1>Hello, {name}!</h1>;
}
```

Example of a Class Component:

```bash
class Greeting extends React.Component {
 render() {
   return <h1>Hello, {this.props.name}!</h1>;
 }
}
```

---

### **5\. What is the difference between functional and class components?**

| **Aspect**          | **Functional Component**                          | **Class Component**                       |
| ------------------- | ------------------------------------------------- | ----------------------------------------- |
| **State**           | Uses React hooks (`useState`) for state.          | Manages state with `this.state`.          |
| **Lifecycle**       | Hooks like `useEffect` replace lifecycle methods. | Uses methods like `componentDidMount`.    |
| **Performance**     | Generally faster; no overhead of classes.         | Slower; involves creating `this` context. |
| **Code Simplicity** | Concise and readable.                             | Boilerplate-heavy.                        |
| **Recommended Use** | For most modern React applications.               | Rarely needed for new projects.           |

---

### **6\. What is JSX, and why is it used?**

**JSX** (JavaScript XML) is a syntax extension for JavaScript that resembles HTML. It's used to describe the UI structure in React components.

**Why use JSX?**

- It's more readable and expressive compared to traditional `React.createElement` calls.
- Helps define UI components in a way that's closer to how they appear on the page.
- It allows embedding JavaScript logic directly in the markup.

Example:

```bash
const element = <h1>Hello, World!</h1>;
```

Equivalent without JSX:

```bash
const element = React.createElement('h1', null, 'Hello, World!');
```

---

### **7\. What are props in React?**

**Props** (short for properties) are immutable data passed from a parent component to a child component. They allow components to be **reusable** and **customizable**.

**Key Points**:

- Props are **read-only** and cannot be modified by the child.
- Props can be any data type: strings, numbers, arrays, functions, etc.

Example:

```bash
function Welcome(props) {
 return <h1>Welcome, {props.name}!</h1>;
}

// Using the component
<Welcome name="John" />
```

Here, `name` is a prop passed to the `Welcome` component.

---

### **8\. What is the difference between props and state in React?**

| **Aspect**         | **Props**                                          | **State**                               |
| ------------------ | -------------------------------------------------- | --------------------------------------- |
| **Definition**     | Passed from parent to child to customize behavior. | Managed within the component itself.    |
| **Mutability**     | Immutable (read-only).                             | Mutable (can be updated).               |
| **Responsibility** | Controlled by the parent component.                | Controlled by the component itself.     |
| **Usage**          | Used to pass data to child components.             | Used to manage internal component data. |

---

### **9\. How does React handle events? Provide an example.**

React uses **synthetic events**, which are wrappers around native browser events, providing consistent behavior across browsers.

**Handling Events**:

- Use `onClick`, `onChange`, etc., as props.
- Pass the event handler function directly (no parentheses unless using an inline function).

Example:

```bash
function Button() {
 function handleClick() {
   alert('Button clicked!');
 }

 return <button onClick={handleClick}>Click Me</button>;
}
```

---

### **10\. What are keys in React, and why are they important?**

**Keys** are special attributes used to uniquely identify elements in a list. They help React differentiate between items during updates.

**Why use keys?**

- Improve rendering performance.
- Prevent unnecessary re-renders by ensuring only changed items are updated.

Example:

```bash
const items = ['A', 'B', 'C'];
const list = items.map((item, index) => <li key={index}>{item}</li>);
```

---

### **11\. What is the role of the `render()` method in React?**

The `render()` method is part of class components and is used to define the structure of the UI. It returns React elements (usually JSX), which React converts into DOM nodes.

**Key Points**:

- The `render()` method is **pure** (does not modify state or props).
- It is called during the **mounting** and **updating** phases of a component's lifecycle.

Example:

```bash
class Welcome extends React.Component {
 render() {
   return <h1>Hello, {this.props.name}!</h1>;
 }
}
```

---

### **12\. Explain the React component lifecycle.**

React components have a lifecycle consisting of three phases:

1.  **Mounting** (when a component is added to the DOM):

    - `constructor()`: Initialize state and bind methods.
    - `render()`: Render the component's UI.
    - `componentDidMount()`: Perform side effects (e.g., API calls).

2.  **Updating** (when props or state change):

    - `render()`: Re-renders the UI.
    - `componentDidUpdate()`: Perform operations after DOM updates.

3.  **Unmounting** (when a component is removed):

    - `componentWillUnmount()`: Clean up resources like event listeners or timers.

Lifecycle Example:

```bash
 class Example extends React.Component {
 componentDidMount() {
   console.log('Component mounted');
 }

 componentDidUpdate() {
   console.log('Component updated');
 }

 componentWillUnmount() {
   console.log('Component unmounted');
 }

 render() {
   return <h1>Lifecycle Example</h1>;
 }
}
```

---

### **13\. What is the difference between controlled and uncontrolled components?**

| **Aspect**        | **Controlled Component**                     | **Uncontrolled Component**               |
| ----------------- | -------------------------------------------- | ---------------------------------------- |
| **Data Handling** | Controlled by React state.                   | Managed by the DOM.                      |
| **Example**       | `<input value={state} onChange={handler} />` | `<input ref={inputRef} />`               |
| **Use Case**      | For forms with validation or complex logic.  | For simpler scenarios with less control. |

**Example of Controlled Component**:

```bash
function ControlledInput() {
 const [value, setValue] = React.useState('');

 return (
   <input
     value={value}
     onChange={(e) => setValue(e.target.value)}
   />
 );
}
```

**Example of Uncontrolled Component**:

```bash
function UncontrolledInput() {
 const inputRef = React.useRef();

 return <input ref={inputRef} />;
}
```

---

### **14\. What are React Fragments, and when are they used?**

**React Fragments** allow grouping of multiple elements without adding extra nodes to the DOM.

**Why use them?**

- Prevent unnecessary `<div>` wrappers.
- Improve performance and cleaner markup.

**Syntax**:

```bash
 return (
 <>
   <h1>Heading</h1>
   <p>Paragraph</p>
 </>
);

Equivalent with `React.Fragment`:





return (
 <React.Fragment>
   <h1>Heading</h1>
   <p>Paragraph</p>
 </React.Fragment>
);
```

---

### **15\. How do you conditionally render elements in React?**

React provides several ways to conditionally render elements:

1.  **Ternary Operator**:

    `{isLoggedIn ? <Dashboard /> : <Login />}`

2.  **Logical AND (`&&`)**:

    `{isLoggedIn && <Dashboard />}`

3.  **If-Else Statements**:

    ```bash
    function renderContent() {
     if (isLoggedIn) return <Dashboard />;
     return <Login />;
    }

    return <div>{renderContent()}</div>;
    ```

---

### **16\. How can you create forms in React?**

Forms in React use **controlled components**, where form elements are controlled via React state.

**Example**:

```bash
function FormExample() {
 const [name, setName] = React.useState('');

 const handleSubmit = (e) => {
   e.preventDefault();
   console.log(name);
 };

 return (
   <form onSubmit={handleSubmit}>
     <input
       type="text"
       value={name}
       onChange={(e) => setName(e.target.value)}
     />
     <button type="submit">Submit</button>
   </form>
 );
}
```

---

### **17\. What are default props, and how are they set?**

Default props are values assigned to props if no value is passed by the parent component.

**Setting Default Props**:

```bash
function Greeting({ name }) {
 return <h1>Hello, {name}!</h1>;
}

Greeting.defaultProps = {
 name: 'Guest',
};
```

If no `name` is provided, `Guest` will be used as the default.

---

### **18\. What is `create-react-app`, and what does it do?**

`create-react-app` (CRA) is a command-line tool for setting up a React project with no manual configuration.

**Features**:

- Sets up webpack, Babel, and other tools.
- Provides a development server (`npm start`).
- Preconfigured for JSX, ES6, and CSS/SCSS.

**Usage**:

`npx create-react-app my-app
cd my-app
npm start`

---

### **19\. What are Higher-Order Components (HOCs)?**

An HOC is a function that takes a component and returns a new component, adding extra functionality.

**Purpose**:

- Code reuse.
- Enhancing components with additional features.

**Example**:

`function withLogging(WrappedComponent) {
return function EnhancedComponent(props) {
console.log('Component rendered');
return <WrappedComponent {...props} />;
};
}

const LoggedButton = withLogging(Button);`

---

### **20\. How do you pass data from a parent to a child component?**

Data is passed using **props**.

**Example**:

```bash
function Parent() {
 const name = 'John';

 return <Child name={name} />;
}

function Child({ name }) {
 return <h1>Hello, {name}!</h1>;
}
```

The `Parent` component passes the `name` prop to the `Child` component.

---

### **21\. What are React hooks?**

**React Hooks** are functions introduced in React 16.8 that allow functional components to use state and lifecycle features.

**Why Hooks?**

- Simplify code by avoiding class components.
- Share logic between components without HOCs or render props.

**Common Hooks**:

- `useState`: Manages state in a functional component.
- `useEffect`: Handles side effects like fetching data or subscribing to events.
- `useContext`: Consumes context values without nested render props.
- `useRef`: Accesses DOM nodes or persists values across renders.

Example of `useState`:

```bash
function Counter() {
 const [count, setCount] = React.useState(0);

 return (
   <button onClick={() => setCount(count + 1)}>
     Count: {count}
   </button>
 );
}
```

---

### **22\. What is the purpose of `useState` in React?**

`useState` is a hook that allows you to add state to functional components.

**Syntax**:

`const [state, setState] = React.useState(initialValue);`

- `state`: Current state value.
- `setState`: Function to update the state.
- `initialValue`: Initial state value.

**Example**:

```bash
function Counter() {
 const [count, setCount] = React.useState(0);

 const increment = () => setCount(count + 1);

 return (
   <div>
     <p>Count: {count}</p>
     <button onClick={increment}>Increment</button>
   </div>
 );
}
```

---

### **23\. What is the purpose of `useEffect` in React?**

`useEffect` is a hook for performing **side effects** in functional components, such as:

- Fetching data.
- Updating the DOM.
- Subscribing to events.

**Syntax**:

`useEffect(effectFunction, dependencyArray);`

- `effectFunction`: Function that runs the side effect.
- `dependencyArray`: Array of variables that, when changed, trigger the effect.

**Example**:

```bash
function DataFetcher() {
 const [data, setData] = React.useState(null);

 React.useEffect(() => {
   fetch('https://api.example.com/data')
     .then((response) => response.json())
     .then((data) => setData(data));
 }, []); // Empty array ensures this runs only once.

 return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
}
```

---

### **24\. What are React Portals?**

Portals allow rendering children into a DOM node outside the parent component hierarchy.

**Why use Portals?**

- To render elements like modals, tooltips, or dropdowns that are visually or contextually separate from the main component tree.

**Syntax**:

```bash
ReactDOM.createPortal(child, container);
```

**Example**:

```bash
function Modal({ children }) {
 return ReactDOM.createPortal(
   <div className="modal">{children}</div>,
   document.getElementById('modal-root')
 );
}
```

---

### **25\. What is Redux, and how is it used with React?**

**Redux** is a state management library often used with React for managing application-wide state.

**Core Concepts**:

- **Store**: Centralizes the state of the application.
- **Actions**: Describe changes to the state.
- **Reducers**: Pure functions that update the state based on actions.

**Usage**:

1.  Install Redux and React-Redux:

    `npm install redux react-redux`

2.  Create a store:

    ```bash
     const store = createStore(reducer);
    ```

3.  Provide the store:

    ```bash
     <Provider store={store}>
     <App />
    </Provider>
    ```

4.  Connect components to Redux:

    ```bash
    const mapStateToProps = (state) => ({ count: state.count });
    export default connect(mapStateToProps)(Counter);
    ```

---

### **26\. What is the difference between `useEffect` and `componentDidMount`?**

| **Aspect**           | **`useEffect`**                              | **`componentDidMount`**           |
| -------------------- | -------------------------------------------- | --------------------------------- |
| **Component Type**   | Used in functional components.               | Used in class components.         |
| **Execution Timing** | Runs after every render (can be controlled). | Runs once after the first render. |
| **Flexibility**      | Can handle multiple lifecycle phases.        | Limited to mounting phase.        |

**Example of `useEffect` acting like `componentDidMount`**:

```bash
useEffect(() => {
 console.log('Mounted');
}, []); // Empty array ensures it runs only once.
```

---

### **27\. What are React Context and `useContext`?**

React **Context** provides a way to share values (e.g., theme, user data) across components without passing props down manually at every level.

**Creating a Context**:

```bash
const ThemeContext = React.createContext('light');
```

**Consuming Context with `useContext`**:

```bash
function ThemeButton() {
 const theme = React.useContext(ThemeContext);
 return <button className={theme}>Click Me</button>;
}
```

**Why use Context?**

- Avoids **prop drilling** (passing props through multiple levels).
- Centralizes shared state across components.

---

### **28\. What is React Router?**

React Router is a library for managing navigation in React applications.

**Core Features**:

- **Declarative Routing**: Define routes using JSX.
- **Dynamic Routing**: Match paths dynamically based on the URL.
- **Nested Routes**: Structure routes hierarchically.

**Installation**:

`npm install react-router-dom`

**Basic Example**:

```bash
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';

function App() {
 return (
   <Router>
     <Routes>
       <Route path="/" element={<Home />} />
       <Route path="/about" element={<About />} />
     </Routes>
   </Router>
 );
}
```

---

### **29\. How does React handle performance optimization?**

React optimizes performance through:

1.  **Virtual DOM**: Updates only the necessary DOM elements.
2.  **React.memo**: Prevents re-rendering of functional components if props haven't changed.
3.  **PureComponent**: Similar to `React.memo`, but for class components.
4.  **Code Splitting**: Splits large bundles into smaller ones using `React.lazy` and `Suspense`.
5.  **useCallback and useMemo**: Memoizes functions and values to avoid unnecessary recalculations.

---

### **30\. What are React PropTypes?**

**PropTypes** are used to validate the props passed to a component, ensuring they have the expected type and structure.

**Installation**:

`npm install prop-types`

**Example**:

```bash
import PropTypes from 'prop-types';

function Greeting({ name }) {
 return <h1>Hello, {name}!</h1>;
}

Greeting.propTypes = {
 name: PropTypes.string.isRequired,
};
```

PropTypes help catch errors during development by validating data types.

---

### **31\. What is the significance of keys in React?**

**Keys** are unique identifiers used in lists to help React identify which items have changed, been added, or removed. They improve performance by enabling efficient updates to the DOM.

**Why are keys important?**

- They help React distinguish between items, avoiding unnecessary re-renders.
- Without keys, React may re-render all elements in a list, even if only one changes.

**Best Practices for Keys**:

- Use a unique value from the data (e.g., `id`).
- Avoid using indices as keys unless the list is static.

**Example**:

```bash
 const items = ['Apple', 'Banana', 'Cherry'];

function ItemList() {
 return (
   <ul>
     {items.map((item, index) => (
       <li key={index}>{item}</li> // Use a unique identifier if available
     ))}
   </ul>
 );
}
```

---

### **32\. What is React.memo, and how does it optimize performance?**

`React.memo` is a higher-order component (HOC) that prevents re-renders of a functional component unless its props change.

**How it works**:

- React.memo performs a shallow comparison of the props.
- If the props are the same as the previous render, React skips re-rendering the component.

**Example**:

`const MyComponent = React.memo(({ name }) => {
console.log('Rendered');
return <h1>Hello, {name}!</h1>;
});

// MyComponent will only re-render if the `name` prop changes.`

**When to use**:

- For components that render frequently with the same props.

---

### **33\. What are React Refs?**

**Refs** (short for references) allow direct access to a DOM element or a class component instance.

**Why use Refs?**

- Managing focus, text selection, or media playback.
- Triggering animations.
- Integrating with third-party libraries.

**Creating and Using Refs**:

```bash
 function InputFocus() {
 const inputRef = React.useRef();

 const handleFocus = () => {
   inputRef.current.focus();
 };

 return (
   <div>
     <input ref={inputRef} type="text" />
     <button onClick={handleFocus}>Focus Input</button>
   </div>
 );
}
```

---

### **34\. What is React.lazy, and how does it help with code splitting?**

**React.lazy** is a function that enables **lazy loading** of components, which delays loading them until they are needed. This reduces the initial bundle size and speeds up application load times.

**How to Use React.lazy**:

1.  Wrap the component with `React.lazy`.
2.  Use `Suspense` to display a fallback UI while the component is loading.

**Example**:

```bash
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
 return (
   <React.Suspense fallback={<div>Loading...</div>}>
     <LazyComponent />
   </React.Suspense>
 );
}
```

---

### **35\. What is the difference between `useCallback` and `useMemo`?**

| **Aspect**        | **`useCallback`**                             | **`useMemo`**                       |
| ----------------- | --------------------------------------------- | ----------------------------------- |
| **Purpose**       | Memoizes functions.                           | Memoizes values or computations.    |
| **Returns**       | A memoized version of the callback function.  | A memoized result of a calculation. |
| **Usage Example** | Passing stable callbacks to child components. | Optimizing expensive calculations.  |

**Example of `useCallback`**:

```bash
 const handleClick = React.useCallback(() => {
 console.log('Clicked!');
}, []); // Function is recreated only if dependencies change
```

**Example of `useMemo`**:

```bash const expensiveCalculation = React.useMemo(() => {
 return computeExpensiveValue(a, b);
}, [a, b]); // Value is recalculated only if `a` or `b` changes
```

---

### **36\. How does error boundary work in React?**

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree and display a fallback UI instead of crashing the app.

**Creating an Error Boundary**:\
Error boundaries are implemented using class components.

```bash
class ErrorBoundary extends React.Component {
 constructor(props) {
   super(props);
   this.state = { hasError: false };
 }

 static getDerivedStateFromError() {
   return { hasError: true };
 }

 componentDidCatch(error, info) {
   console.log(error, info);
 }

 render() {
   if (this.state.hasError) {
     return <h1>Something went wrong.</h1>;
   }
   return this.props.children;
 }
}

// Usage:
<ErrorBoundary>
 <MyComponent />
</ErrorBoundary>
```

---

### **37\. What is the difference between `getDerivedStateFromProps` and `componentDidUpdate`?**

| **Aspect**           | **`getDerivedStateFromProps`**                 | **`componentDidUpdate`**             |
| -------------------- | ---------------------------------------------- | ------------------------------------ |
| **Purpose**          | Updates state based on props before rendering. | Runs after the component updates.    |
| **Component Type**   | Static method in class components.             | Instance method in class components. |
| **Execution Timing** | Called during rendering phase.                 | Called after rendering phase.        |

**Example of `getDerivedStateFromProps`**:

```bash
static getDerivedStateFromProps(nextProps, prevState) {
 if (nextProps.value !== prevState.value) {
   return { value: nextProps.value };
 }
 return null;
}
```

**Example of `componentDidUpdate`**:

```bash
componentDidUpdate(prevProps) {
 if (prevProps.value !== this.props.value) {
   console.log('Value changed');
 }
}
```

---

### **38\. What is the purpose of `shouldComponentUpdate`?**

`shouldComponentUpdate` is a lifecycle method used in class components to control re-renders. It returns `true` or `false` based on whether the component should update.

**Default Behavior**:

- React re-renders a component whenever props or state change.

**Custom Implementation**:

```bash
shouldComponentUpdate(nextProps, nextState) {
 return nextProps.value !== this.props.value;
}
```

**Why use it?**

- To optimize performance by preventing unnecessary renders.

---

### **39\. What are synthetic events in React?**

Synthetic events are cross-browser wrappers around native events, ensuring consistent behavior across different browsers.

**Features of Synthetic Events**:

- Unified API for events.
- Works the same in all browsers.
- Mimics native browser events, but not the actual DOM event.

**Example**:

```bash
function handleClick(event) {
 console.log(event.type); // "click"
}

<button onClick={handleClick}>Click Me</button>
```

---

### **40\. How do you optimize large lists in React?**

To optimize rendering large lists, use:

1.  **React Virtualization**:\
    Libraries like `react-window` render only the visible portion of the list.

    `npm install react-window`

    **Example**:

    ```bash
    import { FixedSizeList as List } from 'react-window';

    const items = Array.from({ length: 1000 }, (_, i) => `Item ${i}`);

    function App() {
     return (
       <List
         height={200}
         itemCount={items.length}
         itemSize={35}
         width={300}
       >
         {({ index, style }) => (
           <div style={style}>{items[index]}</div>
         )}
       </List>
     );
    }
    ```

2.  **Pagination**: Load data in chunks instead of rendering everything at once.

3.  **Memoization**: Use `React.memo` or `useMemo` to prevent re-rendering unchanged items.

---

### **41\. What is a higher-order component (HOC) in React?**

A **higher-order component (HOC)** is a function that takes a component as input and returns a new component. HOCs are used for reusing component logic, such as authentication, logging, or state management.

**Syntax**:

```bash
const withEnhancement = (WrappedComponent) => {
 return function EnhancedComponent(props) {
   // Add custom logic
   return <WrappedComponent {...props} />;
 };
};
```

**Example**:

```bash
const withAuth = (WrappedComponent) => {
 return function AuthenticatedComponent(props) {
   const isLoggedIn = true; // Example logic
   if (!isLoggedIn) {
     return <div>Please log in.</div>;
   }
   return <WrappedComponent {...props} />;
 };
};

function Dashboard() {
 return <h1>Welcome to the Dashboard!</h1>;
}

const ProtectedDashboard = withAuth(Dashboard);
```

**When to use HOCs**:

- Reuse logic across multiple components.
- Add functionalities like error handling or theming.

---

### **42\. What are controlled and uncontrolled components in React?**

**Controlled Components**:

- The React state controls the component's value.
- Requires `onChange` handlers to update state.

**Example of Controlled Component**:

```bash
function ControlledInput() {
 const [value, setValue] = React.useState('');

 const handleChange = (event) => {
   setValue(event.target.value);
 };

 return <input value={value} onChange={handleChange} />;
}
```

**Uncontrolled Components**:

- The DOM manages the component's value.
- Uses `ref` to access values.

**Example of Uncontrolled Component**:

```bash
function UncontrolledInput() {
 const inputRef = React.useRef();

 const handleSubmit = () => {
   console.log(inputRef.current.value);
 };

 return (
   <div>
     <input ref={inputRef} />
     <button onClick={handleSubmit}>Submit</button>
   </div>
 );
}
```

---

### **43\. What is the difference between React and React Native?**

| **Aspect**    | **React**                        | **React Native**                            |
| ------------- | -------------------------------- | ------------------------------------------- |
| **Purpose**   | Builds web applications.         | Builds mobile applications.                 |
| **Rendering** | Uses HTML and CSS for rendering. | Uses native components like `View`, `Text`. |
| **Platform**  | Browser-based.                   | Platform-specific (iOS, Android).           |
| **Styling**   | Uses CSS.                        | Uses `StyleSheet` for styling.              |

**Example of React**:

```bash
 function App() {
 return <div>Hello, React!</div>;
}
```

**Example of React Native**:

```bash
import { Text, View } from 'react-native';

function App() {
 return (
   <View>
     <Text>Hello, React Native!</Text>
   </View>
 );
}
```

---

### **44\. What is the difference between `React.Fragment` and `<div>`?**

| **Aspect**      | **`React.Fragment`**                                    | **`<div>`**                           |
| --------------- | ------------------------------------------------------- | ------------------------------------- |
| **Purpose**     | Groups child components without adding extra DOM nodes. | Adds a DOM node.                      |
| **Performance** | More performant due to no extra DOM node.               | May introduce unnecessary nodes.      |
| **Usage**       | Semantic grouping, e.g., `<Fragment></Fragment>`.       | Generic container for styling/layout. |

**Example of React.Fragment**:

```bash
function App() {
 return (
   <React.Fragment>
     <h1>Title</h1>
     <p>Content</p>
   </React.Fragment>
 );
}
```

**Shorthand**: `<></>`

```bash
function App() {
 return (
   <>
     <h1>Title</h1>
     <p>Content</p>
   </>
 );
}
```

---

### **45\. How do you handle forms in React?**

React handles forms using either controlled or uncontrolled components.

**Controlled Component Form**:

```bash
function Form() {
 const [formData, setFormData] = React.useState({ name: '', email: '' });

 const handleChange = (event) => {
   setFormData({ ...formData, [event.target.name]: event.target.value });
 };

 const handleSubmit = (event) => {
   event.preventDefault();
   console.log(formData);
 };

 return (
   <form onSubmit={handleSubmit}>
     <input name="name" value={formData.name} onChange={handleChange} />
     <input name="email" value={formData.email} onChange={handleChange} />
     <button type="submit">Submit</button>
   </form>
 );
}
```

**Uncontrolled Component Form**:

```bash
function UncontrolledForm() {
 const nameRef = React.useRef();
 const emailRef = React.useRef();

 const handleSubmit = (event) => {
   event.preventDefault();
   console.log({ name: nameRef.current.value, email: emailRef.current.value });
 };

 return (
   <form onSubmit={handleSubmit}>
     <input ref={nameRef} name="name" />
     <input ref={emailRef} name="email" />
     <button type="submit">Submit</button>
   </form>
 );
}
```

---

### **46\. What is `useReducer` in React?**

`useReducer` is a React Hook for managing more complex state logic than `useState`.

**Syntax**:

`const [state, dispatch] = React.useReducer(reducer, initialState);`

**Arguments**:

1.  `reducer`: A function `(state, action) => newState`.
2.  `initialState`: The initial state value.

**Example**:

```bash
function reducer(state, action) {
 switch (action.type) {
   case 'increment':
     return { count: state.count + 1 };
   case 'decrement':
     return { count: state.count - 1 };
   default:
     return state;
 }
}

function Counter() {
 const [state, dispatch] = React.useReducer(reducer, { count: 0 });

 return (
   <div>
     <p>Count: {state.count}</p>
     <button onClick={() => dispatch({ type: 'increment' })}>+</button>
     <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
   </div>
 );
}
```

---

### **47\. What are Prop Drilling and its solutions?**

**Prop Drilling**: Passing props down through multiple levels of components, even when intermediate components don't need them.

**Example of Prop Drilling**:

```bash
function GrandParent({ user }) {
 return <Parent user={user} />;
}

function Parent({ user }) {
 return <Child user={user} />;
}

function Child({ user }) {
 return <h1>{user.name}</h1>;
}
```

**Solutions**:

1.  **Context API**: Avoid passing props manually by using context.

    ```bash
    const UserContext = React.createContext();

    function App() {
     return (
       <UserContext.Provider value={{ name: 'John' }}>
         <Child />
       </UserContext.Provider>
     );
    }

    function Child() {
     const user = React.useContext(UserContext);
     return <h1>{user.name}</h1>;
    }
    ```

2.  **State Management Libraries**: Use Redux, MobX, or Zustand to manage state globally.

---

### **48\. What is React Context API, and when should you use it?**

The **React Context API** provides a way to share state or data between components without passing props manually at every level of the component tree. It is primarily used to avoid **prop drilling**.

**Key Parts of Context API**:

1.  **React.createContext()**: Creates a context.
2.  **Provider**: Supplies the context value to child components.
3.  **Consumer**: Accesses the context value.

---

**Example of Context API Usage**:

```bash
// Create a context
const ThemeContext = React.createContext();

function App() {
 return (
   <ThemeContext.Provider value="dark">
     <Toolbar />
   </ThemeContext.Provider>
 );
}

function Toolbar() {
 return <ThemedButton />;
}

function ThemedButton() {
 // Access context value using useContext Hook
 const theme = React.useContext(ThemeContext);
 return <button className={theme}>Click Me</button>;
}
```

---

### **49\. What is the difference between state and props in React?**

| **Aspect**     | **State**                             | **Props**                                   |
| -------------- | ------------------------------------- | ------------------------------------------- |
| **Definition** | Component-specific data.              | Data passed from a parent component.        |
| **Mutability** | Mutable via `setState` or `useState`. | Immutable (read-only).                      |
| **Scope**      | Local to the component.               | Shared between parent and child components. |
| **Usage**      | To manage internal logic.             | To configure child components.              |

**Example**:

```bash
function App() {
 const [count, setCount] = React.useState(0); // State

 return <Counter count={count} increment={() => setCount(count + 1)} />; // Props
}

function Counter({ count, increment }) {
 return (
   <div>
     <p>Count: {count}</p>
     <button onClick={increment}>Increment</button>
   </div>
 );
}
```

---

### **50\. How does React handle events?**

React handles events using **Synthetic Events**, which are wrappers around native events. These events are consistent across browsers, making them easier to work with.

**Differences from Native Events**:

- React event handlers use camelCase (`onClick`) instead of lowercase (`onclick`).
- In React, `onClick={() => ...}` is preferred over inline HTML event handlers.

**Example**:

```bash
 function App() {
 const handleClick = (event) => {
   console.log('Button clicked!', event.target);
 };

 return <button onClick={handleClick}>Click Me</button>;
}
```

---

### **51\. What is PropTypes in React?**

**PropTypes** is a built-in library for type-checking props in React components. It ensures that components receive the correct type and structure of props, helping catch bugs.

**How to Use PropTypes**:

```bash
import PropTypes from 'prop-types';

function Greeting({ name, age }) {
 return (
   <h1>
     Hello, {name}! You are {age} years old.
   </h1>
 );
}

Greeting.propTypes = {
 name: PropTypes.string.isRequired,
 age: PropTypes.number.isRequired,
};

Greeting.defaultProps = {
 name: 'Guest',
};
```

---

### **52\. What is reconciliation in React?**

**Reconciliation** is React's process of updating the DOM efficiently. When the state or props of a component change, React determines how to update the UI with minimal changes.

**How Reconciliation Works**:

1.  React creates a **virtual DOM**.
2.  When updates occur, React compares the new virtual DOM with the old one using a **diffing algorithm**.
3.  React updates only the parts of the real DOM that changed.

**Key Concepts**:

- React uses **keys** for identifying list items during reconciliation.
- Updates are applied in batches to optimize performance.

---

### **53\. What is the use of `StrictMode` in React?**

**`React.StrictMode`** is a tool for highlighting potential issues in an application. It performs additional checks and warnings in development mode without impacting production builds.

**Features**:

- Identifies unsafe lifecycle methods.
- Warns about legacy string ref APIs.
- Warns about unexpected side effects in components.

**Usage**:

```bash
function App() {
 return (
   <React.StrictMode>
     <MyComponent />
   </React.StrictMode>
 );
}
```

---

### **54\. How does React handle memory leaks?**

React doesn't handle memory leaks directly, but you can prevent them by:

1.  **Cleaning up in `useEffect`**: Remove subscriptions or event listeners.
2.  **Avoiding state updates after unmounting**:

    ```bash
    let isMounted = true;
    React.useEffect(() => {
     fetchData().then(() => {
       if (isMounted) {
         setState(data);
       }
     });
     return () => (isMounted = false);
    }, []);
    ```

---

### **55\. What is the role of `useRef` in React?**

`useRef` provides a way to create a mutable reference that persists across renders.

**Use Cases**:

- Accessing DOM elements.
- Storing mutable data (like timers or previous values).
- Avoiding re-renders when data changes.

**Example of Accessing DOM**:

```bash
function InputFocus() {
 const inputRef = React.useRef();

 const handleFocus = () => {
   inputRef.current.focus();
 };

 return (
   <div>
     <input ref={inputRef} type="text" />
     <button onClick={handleFocus}>Focus Input</button>
   </div>
 );
}
```

---

### **56\. What is React Router, and why is it used?**

**React Router** is a standard library for routing in React applications. It enables navigation between different views of an application, changes the browser URL, and keeps the UI in sync with the URL.

**Why Use React Router?**

1.  Manage navigation and rendering of components.
2.  Enable single-page application (SPA) behavior.
3.  Simplifies dynamic routing.

**Basic Example**:

```bash
 import { BrowserRouter as Router, Route, Link, Routes } from 'react-router-dom';

function Home() {
 return <h1>Home</h1>;
}

function About() {
 return <h1>About</h1>;
}

function App() {
 return (
   <Router>
     <nav>
       <Link to="/">Home</Link>
       <Link to="/about">About</Link>
     </nav>
     <Routes>
       <Route path="/" element={<Home />} />
       <Route path="/about" element={<About />} />
     </Routes>
   </Router>
 );
}
```

---

### **57\. What is lazy loading in React?**

**Lazy Loading** is a technique for loading components or resources only when they are needed. This improves performance by reducing the initial load time.

**React's `React.lazy`**:\
This allows components to be loaded dynamically.

**Example**:

```bash
import React, { Suspense } from 'react';

const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
 return (
   <Suspense fallback={<div>Loading...</div>}>
     <LazyComponent />
   </Suspense>
 );
}
```

**Benefits of Lazy Loading**:

- Optimizes resource usage.
- Reduces initial bundle size.
- Improves page load time.

---

### **58\. What is a key in React, and why is it important?**

A **key** is a special attribute used to identify each item in a list uniquely. React uses keys to determine which items have changed, added, or removed during reconciliation.

**Why Are Keys Important?**

- Improve performance by reducing unnecessary re-renders.
- Helps React optimize updates to the DOM.

**Example**:

```bash
function List({ items }) {
 return (
   <ul>
     {items.map((item) => (
       <li key={item.id}>{item.name}</li>
     ))}
   </ul>
 );
}
```

**What Happens Without Keys?**\
React might re-render the entire list instead of updating specific items.

---

### **59\. What are portals in React?**

**Portals** allow rendering of a component into a different DOM node outside of its parent hierarchy.

**Why Use Portals?**

- Handle modals, tooltips, or pop-ups without affecting the layout or styling of parent components.
- Prevent z-index or overflow issues.

**Example**:

```bash
import ReactDOM from 'react-dom';

function Modal({ children }) {
 return ReactDOM.createPortal(
   <div className="modal">{children}</div>,
   document.getElementById('modal-root')
 );
}

function App() {
 return (
   <div>
     <h1>App Component</h1>
     <Modal>
       <p>This is rendered in a portal!</p>
     </Modal>
   </div>
 );
}
```

---

### **60\. How do you optimize React performance?**

Here are techniques to optimize performance in React applications:

1.  **Use `React.memo`**:\
    Prevents unnecessary re-renders by memoizing functional components.

    `const MemoizedComponent = React.memo(MyComponent);`

2.  **Code-Splitting and Lazy Loading**:\
    Load components dynamically using `React.lazy` and `Suspense`.

3.  **Use `useCallback` and `useMemo`**:\
     Optimize functions and values to prevent re-creation on every render.

        `const memoizedValue = React.useMemo(() => computeValue(a, b), [a, b]);

    const memoizedCallback = React.useCallback(() => doSomething(), [dependency]);`

4.  **Avoid Anonymous Functions in Props**:\
    Avoid passing inline functions directly to props.

5.  **Use a Production Build**:\
    Use `npm run build` to create optimized builds for production.

6.  **Virtualize Long Lists**:\
    Use libraries like `react-window` or `react-virtualized` for rendering large lists efficiently.

7.  **Avoid State Derivation**:\
    Avoid creating derived states unnecessarily, as it can cause unnecessary re-renders.

8.  **Optimize Reconciliation**:

    - Use unique and stable keys for list rendering.
    - Flatten deeply nested structures.
