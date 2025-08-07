## Interview Questions & Answers (Short)

### 1. Introduce yourself? Total years of experience?

I’m a Full Stack UI Developer with **12+ years of experience**, skilled in React, Angular, JavaScript, TypeScript, Node.js, and AWS-based microservices.

---

### 2. JavaScript is synchronous or asynchronous?

JavaScript is **synchronous by default**, but supports **asynchronous behavior** using callbacks, Promises, and `async/await`.

---

### 3. What is asynchronous call? How to make async call?

An asynchronous call runs in the background without blocking the main thread.  
You can make one using:

- `setTimeout`
- `fetch` (returns a Promise)
- `async/await`

---

### 4. Callback?

A **callback** is a function passed into another function as an argument, to be executed later after an operation completes.

---

### 5. Callback hell?

Occurs when callbacks are nested within callbacks, making code messy and unreadable.  
**Solution**: Use Promises or `async/await` for cleaner, linear flow.

---

### 6. call, apply, bind? Where did you use?

Used to control the `this` context inside functions.

- `call()`: Calls a function with a specified `this` and arguments.
- `apply()`: Like `call`, but takes arguments as an array.
- `bind()`: Returns a new function with bound `this`.

**Used `bind`** in React class components to bind event handlers.
call() — For function borrowing, apply() — When args are in an array, 3. bind() — To fix this in advance

## Interview Questions & Answers (Part 2)

### 7. Coding Question

```js
const test = [[1, 2, 3], [4, 5, [5, false, 6, [5, 8, null]]], [6]];

function flattenArray(arr) {
  const result = [];

  function helper(subArr) {
    for (let item of subArr) {
      if (Array.isArray(item)) {
        helper(item);
      } else {
        result.push(item);
      }
    }
  }

  helper(test);
  console.log(result);
}
```

## Interview Questions & Answers (8–15)

### 8. React: Functional or Class — which have you used?

I’ve primarily used **functional components** with hooks in recent projects. I’ve also worked with **class components** in legacy codebases.

---

### 9. State management — how did you achieve it?

- For local state: `useState`, `useReducer`
- For shared/global state: Redux Toolkit, Context API
- For async/server state: React Query
- Also used Zustand in a lightweight scenario

---

### 10. Have you worked on class components?

Yes. I’ve used class components in earlier projects and worked with lifecycle methods like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

---

### 11. Lifecycle Methods Using Hooks (equivalent to Class)

```js
// componentDidMount
useEffect(() => {
  // code to run on mount
}, []);

// componentDidUpdate
useEffect(() => {
  // code to run on update
}, [dependency]);

// componentWillUnmount
useEffect(() => {
  return () => {
    // cleanup code
  };
}, []);
```

## Interview Questions & Answers (12–15)

### 12. Hooks — have you worked with them? Which?

Yes. I’ve worked with the following hooks:

- `useState` – for managing local state
- `useEffect` – for side effects and lifecycle behavior
- `useContext` – for accessing shared context
- `useRef` – for referencing DOM elements or storing mutable values
- `useReducer` – for complex state logic
- `useMemo` – to memoize expensive computations
- `useCallback` – to memoize functions

---

### 13. useMemo vs useCallback — Difference?

| Hook          | Purpose                                | Returns  |
| ------------- | -------------------------------------- | -------- |
| `useMemo`     | Caches the **result** of a computation | Value    |
| `useCallback` | Caches the **function** itself         | Function |

- Use `useMemo` to avoid re-calculating expensive values unless dependencies change.
- Use `useCallback` to avoid recreating functions on each render, especially when passing them to child components.

---

### 14. How to pass data from child to parent?

You pass a callback from parent to child. The child calls that function with the data:

```js
// Parent
const handleData = (value) => setState(value);
<Child onSendData={handleData} />;

// Child
props.onSendData("data from child");
```

### 15. Other than Redux and Context — how to manage state?

Here are alternative ways to manage state in React:

- **Zustand** – A small, fast, and scalable global state management library without boilerplate.
- **Jotai** – Atomic state model. Each piece of state is an individual unit (atom) that can be shared.
- **Recoil** – Provides fine-grained state control using atoms/selectors. Good for complex global state needs.
- **React Query (TanStack Query)** – Manages **server state** like API data: caching, fetching, updating.
- **useReducer + Context** – Combine both to create a basic global state system without external libs.

<!-- const test = [[1, 2, 3], [4, 5, [5, false, 6, [5, 8, null]]], [6]]
//convert array to single array without flat method

const flattAray = (arr) => {
const result = [];

    for (const item of arr) {
        if (Array.isArray(item)) {
            result.push(...flattAray(item));
        } else {
            result.push(item);
        }
    }

    return result;

}
console.log(flattAray(test)); -->
