-  Wrap 
```java
// 1. Importing (createContext)
import { createContext } from "react";
import ComponentA from "./ComponentA";

// 2. Creating instance of (createContext)
export const Data = createContext();
export const Data1 = createContext();

const App = () => {
  const name = "HuXn";
  const age = 19;

  return (
    <>
      {/* 3. Wrapping our components into Provider component */}
      <Data.Provider value={name}>
        <Data1.Provider value={age}>
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
import { Data, Data1 } from "./App.jsx";

const ComponentC = () => {
  return (
    <>
      {/* 4. Consuimg/Accessing Data */}
      <Data.Consumer>
        {(name) => {
          // return <h1>My name is: {name}</h1>;
          return (
            <Data1.Consumer>
              {(age) => {
                return (
                  <h1>
                    My name is: {name} and I'm {age} years old.
                  </h1>
                );
              }}
            </Data1.Consumer>
          );
        }}
      </Data.Consumer>
    </>
  );
};

export default ComponentC;
```
