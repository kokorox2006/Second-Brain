<center><b><i>Ways to implement conditional rendering.</i></b></center>

---

### 1. **Using `if...else` Statements**

```jsx
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  } else {
    return <h1>Please sign up.</h1>;
  }
}
```

**Usage:**
```jsx
<Greeting isLoggedIn={true} /> // Renders "Welcome back!"
<Greeting isLoggedIn={false} /> // Renders "Please sign up."
```

---

### 2. **Using Ternary Operators**
- Provide a concise way 
- (`condition ? trueValue : falseValue`) 

```jsx
function Greeting({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please sign up.</h1>}
    </div>
  );
}
```

**Usage:**
```jsx
<Greeting isLoggedIn={true} /> // Renders "Welcome back!"
<Greeting isLoggedIn={false} /> // Renders "Please sign up."
```

---

### 3. **Using Logical `&&` Operator**
- When you want to render something only if a condition is `true`. 
- If the condition evaluates to `false`, React will skip rendering that part.

```jsx
function Notification({ hasNotification }) {
  return (
    <div>
      {hasNotification && <p>You have new notifications!</p>}
    </div>
  );
}
```

**Usage:**
```jsx
<Notification hasNotification={true} /> // Renders "You have new notifications!"
<Notification hasNotification={false} /> // Renders nothing
```

---

### 4. **Using Inline Functions**
 - To encapsulate complex logic 

```jsx
function UserStatus({ user }) {
  const getStatusMessage = () => {
    if (user.isAdmin) {
      return <h1>Welcome, Admin!</h1>;
    } else if (user.isMember) {
      return <h1>Welcome, Member!</h1>;
    } else {
      return <h1>Please register.</h1>;
    }
  };

  return <div>{getStatusMessage()}</div>;
}
```

**Usage:**
```jsx
<UserStatus user={{ isAdmin: true }} /> // Renders "Welcome, Admin!"
<UserStatus user={{ isMember: true }} /> // Renders "Welcome, Member!"
<UserStatus user={{}} /> // Renders "Please register."
```

---

### 5. **Using Element Variables**
- You can store JSX elements in variables and conditionally assign them before rendering.

```jsx
function App() {
  const isLoggedIn = true;

  let message;
  if (isLoggedIn) {
    message = <h1>Welcome back!</h1>;
  } else {
    message = <h1>Please sign up.</h1>;
  }

  return <div>{message}</div>;
}
```

---

### 6. **Rendering `null` to Hide Components**
If you want to hide a component under certain conditions, you can return `null`.

```jsx
function WarningBanner({ showWarning }) {
  if (!showWarning) {
    return null; // Component will not render
  }

  return <div>Warning: Something went wrong!</div>;
}
```

**Usage:**
```jsx
<WarningBanner showWarning={true} /> // Renders the warning message
<WarningBanner showWarning={false} /> // Renders nothing
```

---

### 7. **Using Switch-like Logic with Objects**
For more complex scenarios, you can use an object to map conditions to components.

```jsx
function StatusMessage({ status }) {
  const messages = {
    loading: <p>Loading...</p>,
    success: <p>Operation successful!</p>,
    error: <p>Error occurred!</p>,
  };

  return <div>{messages[status] || <p>Unknown status</p>}</div>;
}
```

**Usage:**
```jsx
<StatusMessage status="loading" /> // Renders "Loading..."
<StatusMessage status="success" /> // Renders "Operation successful!"
<StatusMessage status="error" /> // Renders "Error occurred!"
<StatusMessage status="unknown" /> // Renders "Unknown status"
```

---

### Summary of Approaches:
| Method                     | Use Case                                                                 |
|----------------------------|--------------------------------------------------------------------------|
| `if...else`                | For simple or complex conditions outside JSX                             |
| Ternary Operator (`? :`)   | For concise inline conditions                                           |
| Logical `&&`               | To conditionally render a single element                                |
| Inline Functions           | To encapsulate complex logic                                            |
| Element Variables          | To separate logic from JSX                                              |
| Returning `null`           | To prevent rendering of a component                                     |
| Object Mapping             | For switch-like logic with multiple conditions                          |

---

