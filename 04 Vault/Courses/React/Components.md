Basically Function is know as 'Component ' But function name should be ==Capital== &
it always return an HTML syntax 

```javascript
function App() {
  return <h1>Hello, World!</h1>;
}
```

- Note :- We can use any type of Function for components
# Multiple Components
Usually we create separate folder for components and export them main Function which is present in 'App.jsx'

Greeting.jsx
```Javascript
const Greet = () =>{
return <h1> Hello </h1>
};
export default Greet;
```

App.jsx
```Javascript
import Greet from './components/Greeting';

const App = () => {
return <Greet/>
};
export default App;
```
	