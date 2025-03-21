<center><i><b>Types of event</b></i></center>

---
### 1. **Basic Event Handling**
To handle events in React, you attach an event listener to a JSX element and provide a function as the event handler.

#### Example: Handling a Button Click
```jsx
function App() {
  const handleClick = () => {
    alert('Button clicked!');
  };

  return (
    <button onClick={handleClick}>
      Click Me
    </button>
  );
}
```

- The `onClick` attribute specifies the event handler.
- The `handleClick` function is executed when the button is clicked.

---

### 2. **Passing Arguments to Event Handlers**
If you need to pass arguments to the event handler, you can use an inline arrow function.

#### Example: Passing Arguments
```jsx
function App() {
  const greetUser = (name) => {
    alert(`Hello, ${name}!`);
  };

  return (
    <button onClick={() => greetUser('Alice')}>
      Greet Alice
    </button>
  );
}
```

- The arrow function `() => greetUser('Alice')` ensures that `greetUser` is called with the argument `'Alice'`.

---

### 3. **Preventing Default Behavior**
Some events have default behaviors (e.g., submitting a form reloads the page). To prevent this, call `event.preventDefault()` inside the event handler.

#### Example: Preventing Form Submission
```jsx
function LoginForm() {
  const handleSubmit = (event) => {
    event.preventDefault(); // Prevents the default form submission behavior
    alert('Form submitted!');
  };

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

### 4. **Binding Event Handlers in Class Components**
In class components, you often need to bind event handlers to the component instance to ensure the correct `this` context.

#### Example: Binding in Class Components
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
    this.increment = this.increment.bind(this); // Bind the method
  }

  increment() {
    this.setState((prevState) => ({ count: prevState.count + 1 }));
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}
```

Alternatively, you can use **class fields** (with Babel or TypeScript) to avoid manual binding:
```jsx
class Counter extends React.Component {
  state = { count: 0 };

  increment = () => {
    this.setState((prevState) => ({ count: prevState.count + 1 }));
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}
```

---

### 5. **Accessing Event Data**
The `SyntheticEvent` object provides information about the event, such as the target element, key pressed, or mouse position.

#### Example: Accessing Input Value
```jsx
function InputExample() {
  const handleChange = (event) => {
    console.log('Input value:', event.target.value);
  };

  return (
    <input type="text" onChange={handleChange} placeholder="Type something..." />
  );
}
```

---

### 6. **Handling Keyboard Events**
You can handle keyboard events like `onKeyDown`, `onKeyUp`, or `onKeyPress` to respond to specific keys.

#### Example: Detecting Enter Key Press
```jsx
function SearchBox() {
  const handleKeyDown = (event) => {
    if (event.key === 'Enter') {
      alert('Enter key pressed!');
    }
  };

  return (
    <input type="text" onKeyDown={handleKeyDown} placeholder="Press Enter..." />
  );
}
```

---

### 7. **Event Propagation (Bubbling and Capturing)**
React supports event propagation just like the DOM. You can stop propagation using `event.stopPropagation()`.

#### Example: Stopping Propagation
```jsx
function App() {
  const handleOuterClick = () => {
    alert('Outer div clicked!');
  };

  const handleInnerClick = (event) => {
    event.stopPropagation(); // Stops the event from bubbling up
    alert('Inner div clicked!');
  };

  return (
    <div onClick={handleOuterClick} style={{ padding: '20px', border: '1px solid black' }}>
      Outer Div
      <div
        onClick={handleInnerClick}
        style={{ padding: '20px', border: '1px solid red', marginTop: '10px' }}
      >
        Inner Div
      </div>
    </div>
  );
}
```

---

### 8. **Common React Events**
Here’s a list of commonly used React events:

| Event Name       | Description                              |
|------------------|------------------------------------------|
| `onClick`        | Triggered when an element is clicked     |
| `onChange`       | Triggered when the value of an input changes |
| `onSubmit`       | Triggered when a form is submitted       |
| `onKeyDown`      | Triggered when a key is pressed down     |
| `onKeyUp`        | Triggered when a key is released         |
| `onMouseEnter`   | Triggered when the mouse enters an element |
| `onMouseLeave`   | Triggered when the mouse leaves an element |
| `onFocus`        | Triggered when an element gains focus    |
| `onBlur`         | Triggered when an element loses focus    |

---

### 9. **Using Hooks for Event State Management**
With React hooks like `useState`, you can manage state based on events.

#### Example: Managing Input State
```jsx
import React, { useState } from 'react';

function NameForm() {
  const [name, setName] = useState('');

  const handleChange = (event) => {
    setName(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Hello, ${name}!`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={name}
        onChange={handleChange}
        placeholder="Enter your name"
      />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

### Summary
React's event system simplifies handling user interactions while maintaining cross-browser consistency. Here’s a quick recap:

- Use camelCase for event names (e.g., `onClick`, `onChange`).
- Pass functions as event handlers.
- Use `event.preventDefault()` to stop default behavior.
- Access event data via the `SyntheticEvent` object.
- Manage state dynamically using hooks like `useState`.

By mastering these concepts, you can build interactive and responsive React applications effectively.