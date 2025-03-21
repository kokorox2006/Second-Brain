It is an extension for React & We return HTML  inside [[Components]]

```Javascript
const App = () => {
  return (
    <section id="section">
      <h1>My Website</h1>
      <article>
        <h2>Welcome To React</h2>
        <p className="text">Paragraph Content</p>
      </article>
    </section>
  );
};

export default App;

```


<center><b><i>JSX RULES</i></b> </center>

 1. ==Return a single root element== :-To return multiple elements from a component, wrap them with a single parent tag.

ERROR
``` javascript
const App = () => {
     return (
         <section id="section">
         </section>
           <h1>Welcome To React</h1>
       );
 }
``` 

 2. ==Close all the tags== :- JSX requires tags to be explicitly closed: self-closing tags 

# Expression in JSX    (Dynamic Content)
- In Curly Braces we can write expression & expression can be react variable, property or any other Javascript expression.

```Javascript
const App = () => {
  const myName = "HuXn WebDev";
  const multiply = (a, b) => a + b;
  const specialClass = "simple-class";

  return (
    <section>
      {/* Rendering Expression */}
      <p>2 + 2 = {2 + 2}</p>
      {/* Rendering Variable Value */}
      <h1>{myName}</h1>
      {/* Rendering Array */}
      <p>My Friends List: {["Alex", "John", "Waheed", "Jordan"]}</p>
      {/* Rendering Function Value */}
      <p>2 * 2 = {multiply(2, 2)}</p>
      {/* Rendering Class */}
      <p className={specialClass}>This is special class</p>
    </section>
  );
};

export default App;
```

# List
- We need to create some type of loop & generally we use JS map() method.

```Javascript
const Shopping = ({ items }) => {
  return (
    <section>
      <ol>
        {items.map((item) => (
          <li key={Math.random() * 5}>{item}</li>
        ))}
      </ol>
    </section>
  );
};

const App = () => {
  return (
    <section>
      <Shopping
        items={["Wireless Earbuds", "Power Bank", "New SSD", "Hoddie"]}
      />
    </section>
  );
};

export default App;
```

