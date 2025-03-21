- Similar to useState, but it is designed for more complex state objects  or state transitions that involve multiple sub-values.
- Allow us to manage state in a functional, Immutable way.

<center><b><i>Syntax</i></b></center>
```java
const[state, dispatch] = useReducer(reducer, initalState)
```


- `reducer`: The function that determines how the state should change.
- `initialState`: The initial value of the state.
- `state`: The current state.
- `dispatch`: A function used to trigger state changes by passing an action to the reducer.

- The useReducer Hook is the alternative to useState Hook.
-  If you find yourself keeping track of multiple pieces of state that rely on complex logic, useReducer may be useful.

- The useReducer Hook returns the current (state) and a (dispatch) method.

- State as the name suggest will be the "state" of your component.
- dispatch will allow you to change that state, Think of it is like [val, setVal]

- useReducer accepts two parameters (reducer, initialState)

- The reducer function contains your custom state logic
- The initialState can be a simple value but generally will contain an object.

```java


// 1 👇
import { useReducer } from "react";

const Counter = () => {
  // 2 👇
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      {/*  6 👇 */}
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
      <h1>{state.count}</h1>
    </div>
  );
};

// 3 👇
const initialState = { count: 0 };

// 4 👇
const reducer = (state, action) => {
  // 5 👇
  switch (action.type) {
    case "increment":
      return {
        ...state,
        count: state.count + 1,
      };
    case "decrement":
      return {
        ...state,
        count: state.count - 1,
      };
    case "reset":
      return {
        ...state,
        count: 0,
      };
    default:
      return state;
  }
};

const App = () => {
  return <Counter />;
};

export default App;
```