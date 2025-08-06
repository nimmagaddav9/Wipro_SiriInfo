# Frontend Engineer - Mock Interview Q&A

## ✅ Technical Questions (Core Frontend)

### 1. What are the benefits of using TypeScript in a React project?

TypeScript adds static typing to JavaScript, helping catch bugs at compile time. In React, this improves:

- Component prop validation (replaces PropTypes)
- Better code completion and IntelliSense
- Enforces type contracts
- Easier large-scale refactoring

**Example:**

```tsx
type UserProps = {
  name: string;
  age: number;
};

const UserCard: React.FC<UserProps> = ({ name, age }) => (
  <div>
    {name} is {age} years old
  </div>
);
```

### 2. How does Next.js differ from Create React App (CRA)?

| Feature         | CRA                   | Next.js            |
| --------------- | --------------------- | ------------------ |
| SSR/SSG Support | ❌ No                 | ✅ Yes             |
| Routing         | Manual (React Router) | ✅ File-based      |
| API Routes      | ❌                    | ✅ `/pages/api`    |
| Performance     | Depends               | Optimized          |
| Deployment      | Frontend only         | Full-stack capable |

**Summary:**  
Next.js is a full-stack framework with built-in routing, SSR/SSG support, and API capabilities, making it a better fit for SEO and dynamic rendering needs.

---

### 3. Explain `getServerSideProps` vs `getStaticProps` in Next.js.

- `getServerSideProps`: Executes on every request. Used for dynamic, per-user content.
- `getStaticProps`: Runs at build time. Best for static content like blogs or marketing pages.

**Example:**

```tsx
export async function getServerSideProps(context) {
  const data = await fetchUser(context.params.id);
  return { props: { data } };
}
```

## ✅ Technical & Behavioral Questions (Q4 to Q8)

---

### 4. How do you use Apollo Client in a React app to fetch GraphQL data?

**Step 1 – Setup ApolloProvider:**

```tsx
const client = new ApolloClient({
  uri: "/graphql",
  cache: new InMemoryCache(),
});

<ApolloProvider client={client}>
  <App />
</ApolloProvider>;
```

### Step 2 – Use the `useQuery` Hook

```tsx
const GET_USERS = gql`
  query GetUsers {
    users {
      id
      name
    }
  }
`;

const Users = () => {
  const { loading, error, data } = useQuery(GET_USERS);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error</p>;

  return data.users.map((user) => <p key={user.id}>{user.name}</p>);
};
```

### 5. How do you manage performance in large React apps?

- **Code splitting** with `React.lazy` and `Suspense`
- **Memoization** using `React.memo`, `useMemo`, and `useCallback`
- **Virtualization** for large lists using `react-window` or `react-virtualized`
- **Avoid unnecessary re-renders** by structuring components properly and using `key` props wisely
- **Debounce/throttle** frequent updates (e.g., input handlers or scroll events)
- **Use profiling tools** like React DevTools, Chrome DevTools, and Lighthouse to identify bottlenecks

---

### 6. Tell me about a challenging bug you faced in a React app.

**Scenario:**
During a React migration project, we encountered a form submission issue where state didn’t update correctly.

**Root Cause:**
A stale closure inside a `useEffect` hook was holding on to outdated state values.

**Solution:**
We refactored the logic into a custom hook and updated the dependency array of `useEffect`. This resolved the issue and improved code reusability and testability.

---

### 7. How do you approach code reviews as a Frontend Engineer?

When reviewing code, I focus on:

- Code readability and structure
- Correct and consistent use of TypeScript types
- Reusability and adherence to DRY principles
- Accessibility and semantic HTML
- Performance implications of certain patterns
- Test coverage and edge case handling

I aim to make my reviews constructive—offering better alternatives when needed, and acknowledging clean or clever solutions.

---

### 8. How do you stay updated with frontend technologies?

- Follow official blogs (React, TypeScript, Next.js, Apollo)
- Listen to podcasts like _Syntax.fm_, _The Changelog_, and _Frontend Happy Hour_
- Try out tools in personal side projects
- Read release notes on GitHub for key libraries
- Engage in communities on Twitter, Reddit (`r/reactjs`), and Dev.to

I believe staying hands-on is the best way to actually retain and apply what you learn.
