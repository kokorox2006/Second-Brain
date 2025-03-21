- To communicate Parent -----> Child 
- But you can pass any JavaScript value through them, including objects, arrays, and functions.
```Javascript
// ParentComponent.js
import React from 'react';
import ChildComponent from './ChildComponent';

function ParentComponent() {
  const user = {
    name: "John Doe",
    age: 30,
  };

  return (
    <div>
      <h1>Parent Component</h1>
      <ChildComponent name={user.name} age={user.age} />
    </div>
  );
}

export default ParentComponent;

// ChildComponent.js
import React from 'react';

function ChildComponent({ name, age }) {
  return (
    <div style={{ border: '1px solid black', padding: '10px', margin: '10px' }}>
      <h2>Child Component</h2>
      <p>Name: {name}</p>
      <p>Age: {age}</p>
    </div>
  );
}

export default ChildComponent;
```

<center><b><i>Props Destructing</i></b></center>
 - Take out sections of data from an array or objects
 - How to :- ==const { active, activeStatus } = props;==
;
*without Destructing*

 ```javascript
 // Parent Component
 // Filename - App.js

import React from "react";
import Greet from "./component/Greet";

class App extends React.component {
    render() {
        return (
            <div className="App">
                <Greet active="KAPIL GARG" activeStatus="CSE" />
            </div>
        );
    }
}
export default App;

```

```javascript
// Child Component
// Filename - component/Greet.js

import React from "react";

const Greet = (props) => {
    return (
        <div>
            <div className="XYZ">
                <h3> {props.active} </h3>
            </div>
            <div className="PQR">
                <h1>{props.activeStatus}</h1>
            </div>
        </div>
    );
};
export default Greet;

```
 *Destructuring*
 ```javascript
 // Filename - component/Greet.js

import React from "react";

const Greet = (props) => {
    // Destructuring
    const { active, activeStatus } = props;
    return (
        <div>
            <div className="XYZ">
                <h3> {active} </h3>
            </div>
            <div className="PQR">
                <h1>{activeStatus}</h1>
            </div>
        </div>
    );
};
export default Greet;

```
 