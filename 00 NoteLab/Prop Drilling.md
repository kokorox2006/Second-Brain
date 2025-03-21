# App.jsx
```java
import ComponentA from "./ComponentA";

const App = () => {
  const name = "HuXn";
  return <ComponentA name={name} />;
};

export default App;
```

# ComponentA.jsx
```java
import ComponentB from "./ComponentB";

const ComponentA = ({ name }) => {
  return <ComponentB name={name} />;
};

export default ComponentA;
```

# ComponentB.jsx
```java
import ComponentC from "./ComponentC";

const ComponentB = ({ name }) => {
  return <ComponentC name={name} />;
};

export default ComponentB;
```

# ComponentC.jsx
```java
const ComponentC = ({ name }) => {
  return <h1>{name}</h1>;
};

export default ComponentC;
```