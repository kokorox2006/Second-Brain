- Way to store data that can change ==over time & affect== the how component renders
- Define state using ==useState hook==:- allow us to set initial value & provide a way to update it.

# useState
- Allow us to track state in a functional component 
- Generally, refers to data or properties


---

### **2. Syntax**
The syntax for `useState` is straightforward:

```javascript
const [state, setState] = useState(initialState);
```

- **`state`**: This is the current value of the state.
- **`setState`**: This is a function used to update the state.
- **`initialState`**:initial value of the state when the component first renders.
# 1. Basic Counter

```javascript
import { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
    </div>
  );
};

const App = () => {
  return <Counter />;
};

export default App;
```

# 2. Updating Array

```javascript
import { useState } from "react";

const App = () => {
  const [friends, setFriends] = useState(["Alex", "John"]);

  const addOne = () => setFriends([...friends, "HuXn"]);
  const removeOne = () => setFriends(friends.filter((f) => f !== "John"));
  const updateOne = () =>
    setFriends(friends.map((f) => (f === "Alex" ? "Alex Smith" : f)));

  return (
    <div>
      {friends.map((t) => (
        <li key={Math.random()}>{t}</li>
      ))}
      <button onClick={addOne}>Add One</button>
      <button onClick={removeOne}>Remove One</button>
      <button onClick={updateOne}>Update One</button>
    </div>
  );
};

export default App;
```

# 3. Updating Object

```javascript
import { useState } from "react";

const App = () => {
  const [movie, setMovie] = useState({
    title: "Equalizer 3",
    ratings: 7,
  });

  const handleClick = () => {
    // 🥂 To tell react about state updates, we have to give react a brand new object.

    // 👉 LONG WAY
    // const copyMovie = {
    //   // This will copy all the properties, into the new object, and then we can change whatever we want in new object.
    //   ...movie,
    //   ratings: 5,
    // };
    // setMovie(copyMovie);

    // 👉 SHORT WAY
    setMovie({ ...movie, ratings: 5 });
  };

  return (
    <div>
      <h1>{movie.title}</h1>
      <p>{movie.ratings}</p>
      <button onClick={handleClick}>Change Ratings</button>
    </div>
  );
};

export default App;
```

# 4. Updating Array of Objects

```javascript
import { useState } from "react";

const App = () => {
  const [movies, setMovies] = useState([
    { id: 1, title: "Spider man", ratings: 3 },
    { id: 2, title: "Superman", ratings: 6 },
  ]);

  const handleClick = () => {
    setMovies(
      movies.map((m) => (m.id === 1 ? { ...movies, title: "John Wick 4" } : m))
    );
  };

  return (
    <div>
      {movies.map((movie) => (
        <li key={Math.random()}>{movie.title}</li>
      ))}
      <button onClick={handleClick}>Change Name</button>
    </div>
  );
};

export default App;
```

# 5. Sharing State

- App.jsx
```javascript
import { useState } from "react";
import ComponentTwo from "./ComponentTwo";
import ComponentOne from "./ComponentOne";

const App = () => {
  const [count, setCount] = useState(0);

  return (
    <section>
      <ComponentOne count={count} onClickHandler={() => setCount(count + 1)} />
      <ComponentTwo count={count} onClickHandler={() => setCount(count + 1)} />
    </section>
  );
};

export default App;
```

- ComponentOne.jsx
```javascript
const ComponentOne = ({ count, onClickHandler }) => {
  const handleClick = () => onClickHandler();

  return (
    <section>
      <p>{count}</p>
      <button onClick={handleClick}>increment</button>
    </section>
  );
};

export default ComponentOne;
```

- ComponentTwo.jsx
```javascript
const ComponentOne = ({ count, onClickHandler }) => {
  const handleClick = () => onClickHandler();

  return (
    <section>
      <p>{count}</p>
      <button onClick={handleClick}>increment</button>
    </section>
  );
};

export default ComponentOne;
```

# 6. Passing Function as a value

- App.jsx
```javascript
import ExampleOne from "./components/ExampleOne";
import ExampleThree from "./components/ExampleThree";
import ExampleTwo from "./components/ExampleTwo";

const App = () => {
  return (
    <div>
      <ExampleOne />
      <ExampleTwo />
      <ExampleThree />
    </div>
  );
};
export default App;
```

- ExampleOne.jsx
 ```javascript
 import { useState } from "react";

const ExampleOne = () => {
  // Use a function to compute the initial state
  const [count, setCount] = useState(() => {
    // This function will only run on the initial render
    const initialCount = 10;
    return initialCount;
  });

  const increment = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default ExampleOne;
```

- ExampleTwo.jsx
```javascript
import { useState } from "react";

const ExampleTwo = () => {
  // Initialize state with a function that generates a random number
  const [randomNumber, setRandomNumber] = useState(() =>
    Math.floor(Math.random() * 100)
  );

  const generateNewRandomNumber = () => {
    const newNumber = Math.floor(Math.random() * 100);
    setRandomNumber(newNumber);
  };

  return (
    <div>
      <h1>Random Number: {randomNumber}</h1>
      <button onClick={generateNewRandomNumber}>Generate New Number</button>
    </div>
  );
};

export default ExampleTwo;
```

- ExampleThree.jsx
```javascript
import { useState, useEffect } from "react";

const ExampleThree = () => {
  // Initialize state from localStorage or default to an empty string
  const [name, setName] = useState(() => {
    const savedName = localStorage.getItem("name");
    return savedName ? JSON.parse(savedName) : "";
  });

  // Update localStorage whenever the name changes
  useEffect(() => {
    localStorage.setItem("name", JSON.stringify(name));
  }, [name]);

  const handleChange = (event) => {
    setName(event.target.value);
  };

  const handleClear = () => {
    setName("");
  };

  return (
    <div>
      <h1>Your Name: {name}</h1>
      <input
        type="text"
        value={name}
        onChange={handleChange}
        placeholder="Enter your name"
      />
      <button onClick={handleClear}>Clear Name</button>
    </div>
  );
};

export default ExampleThree;
```
