- *To manage global data in react application such as Global State, Services, Themes & User Settings.*
- Use Case :- In React hierarchy we need to pass props to transfer data to child component which makes it harder if we long branch.

---

- **Context Provider**: A component that supplies the context value to its children.
- **Context Consumer**: Components that consume the context value.

#### **2. Syntax**
```javascript
const value = useContext(MyContext);
```

- `MyContext`: The context object created using `React.createContext`.
- `value`: The current value of the context. This value is determined by the nearest `Provider` component in the tree.

---

#### **3. How `useContext` Works**
Here’s a step-by-step breakdown:

1. **Create a Context**:
   Use `React.createContext` to create a context object.
   ```javascript
   const MyContext = React.createContext(defaultValue);
   ```

   - `defaultValue`: The value used when no matching `Provider` is found in the component tree.

2. **Provide a Value**:
   Wrap your component tree with a `Provider` to supply the context value.
   ```javascript
   <MyContext.Provider value={contextValue}>
     <ChildComponent />
   </MyContext.Provider>
   ```

   - `contextValue`: The value passed to the `value` prop of the `Provider`. This can be any JavaScript value (e.g., an object, string, number).

3. **Consume the Value**:
   Use the `useContext` hook in any functional component to access the context value.
   ```javascript
   const value = useContext(MyContext);
   ```

---
# App.jsx
```java
import ComponentA from "./ComponentA";

// 1. Importing (createContext)
import { createContext } from "react";

// 2. Creating instance of (createContext)
export const Data = createContext();
export const Data1 = createContext();

const App = () => {
  const name = "HuXn";
  const Age = 18;

  return (
    <>
      <Data.Provider value={name}>
        <Data1.Provider value={Age}>
          <ComponentA />
        </Data1.Provider>
      </Data.Provider>
    </>
  );
};

export default App;
```

# ComponentA.jsx
```java
import ComponentB from "./ComponentB";

const ComponentA = () => {
  return <ComponentB />;
};

export default ComponentA;
```

# ComponentB.jsx
```java
import ComponentC from "./ComponentC";

const ComponentB = () => {
  return <ComponentC />;
};

export default ComponentB;
```

# ComponentC.jsx
```java
import { useContext } from "react";
import { Data, Data1 } from "./App";

const ComponentC = () => {
  const userName = useContext(Data);
  const Age = useContext(Data1);

  return (
    <h1>
      My name is: {userName} & I'm {Age} years old.
    </h1>
  );
};

export default ComponentC;
```
