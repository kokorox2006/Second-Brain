- Whenever we need to do some task outside of react we use this hook & those task are know as 'Side effect'

# syntax
```java
useEffect(() => {
  // Effect logic (side effect)
  
  return () => {
    // Cleanup logic (optional)
  };
}, [dependencies]); // Dependency array (optional)
```

<center><b><i>Some Common Side Effects</i></b></center>
1. Fetching data from API
2. Updating the DOM document & window
3. Timer Functions setTimeout & setInterval

<center><b><i>Import useEffect</i></b></center>
```javascript
Import React, { useState, useEffect } from "react";
```


```javascript
useEffect( callback, dependencies )
```
- ==callback function== :- Side Effect logic  [what to run ]
- ==dependencies== :- Array of variables (optional) [when to run]

<center><b><i>Variation of useEffect hook</i></b></center>

1. *useEffect without dependencies*
```javascript
import React. { useState, useEffect } from 'react';

const App = () =>{
	 const [count, setCount] = useState(0);
	useEffect(() => {
		document.title = '${count} new messages!';
	});
return (
<div>
	<h3>{count} new Messages!</h3>
	<button onClick={() => setCount(count + 1)}> Increase</button>
</div>
);
};

export default App;
```

2. *useEffect with empty array* :- it will only run one time
```java
import React. { useState, useEffect } from 'react';

const App = () =>{
	 const [count, setCount] = useState(0);
	 
	useEffect(() => {
		document.title = '${count} new messages!';
	}, []);
	
return (
<div>
	<h3>{count} new Messages!</h3>
	<button onClick={() => setCount(count + 1)}> Increase</button>
</div>
);
};

export default App;
```

<center><b><i>Use Cases</i></b></center>
- when we want fast data from API

2. useEffect with variables
```java
import React. { useState, useEffect } from 'react';

const App = () =>{
	 const [count, setCount] = useState(0);
	 const [otherCount, setOtherCount] = useState(5);
	 
	useEffect(() => {
		document.title = '${otherCount} new messages!';
	}, [otherCount]);
	
return (
<div>
	<h3>{count} new Messages!</h3>
	<button onClick={() => setCount(count + 1)}> Increase</button>
	<h3>{otherCount} new Messages!</h3>
	<button onClick={() => otherSetCount(otherCount + 1)}>
	Increase by 5</button>
</div>
);
};

export default App;
```

# Clean-up Function

- If we are setting state using setInterval and that side effect is not cleaned up, when our component unmounts or we're no longer using it, the state is destroyed with the component but the setInterval function will keep running. and that’s make our application slow and low in performance.
- 
- To use clean-up function we need to run return function in useEffect. Timeouts, subscriptions, event listeners, and other effects that are no longer needed should be disposed with the help of cleanup function.

```java
import React, { useEffect, useState } from "react";

const App = () => {
	const [count, setCount] = useState(0);

	useEffect(() => {
		console.log("Run useEffect", count);

		return () => { // clean-up function
			console.log("Clean up", count);
		};
	}, [count]);
	return (
	<>
		<h3>Count {count}</h3>
		<button onClick={() => setCount(count + 1)}>Increase</button>
	</>
	);
};
export default App;
```
