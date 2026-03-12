# React + TypeScript Coding Guidelines

## 1. Purpose

This document defines **React + TypeScript coding standards** for
frontend applications.

The goal of these guidelines is to ensure:

- Maintainable React components
- Predictable rendering behavior
- Type-safe component APIs
- Good performance practices
- Consistent component architecture

These rules extend:

- General Coding Guidelines (GCG)
- TypeScript Coding Guidelines (TSC)

Example reference in code review:

Violation: RTS-004 -- Avoid Inline Functions in JSX

---

# 2. Component Design

## RTS-001 Use Functional Components Only

React components must use **functional components** instead of class
components.

❌ Avoid

```tsx
class UserList extends React.Component {}
```

✅ Preferred

```tsx
function UserList() {
  return <div />;
}
```

---

## RTS-002 Keep Components Small and Focused

Components should have a **single responsibility**.

Large components should be split into smaller components.

❌ Avoid large "god components"

Preferred pattern:

    UserPage
     ├── UserHeader
     ├── UserDetails
     └── UserActivityList

---

## RTS-003 Separate UI from Business Logic

Business logic should not be tightly coupled to UI components.

Prefer:

- custom hooks
- service layers
- utility functions

Example:

    components/
    hooks/
    services/

---

# 3. Props and Typing

## RTS-004 Always Type Component Props

Component props must always be typed.

❌ Avoid

```tsx
function Button(props) {
  return <button>{props.label}</button>;
}
```

✅ Preferred

```tsx
interface ButtonProps {
  label: string;
}

function Button({ label }: ButtonProps) {
  return <button>{label}</button>;
}
```

---

## RTS-005 Prefer Interfaces for Props

Component props should use **interfaces** rather than inline types.

❌ Avoid

```tsx
function Card(props: { title: string }) {}
```

✅ Preferred

```tsx
interface CardProps {
  title: string;
}

function Card({ title }: CardProps) {}
```

---

## RTS-006 Avoid Excessive Props

Components with too many props become difficult to use and maintain.

If props exceed **6--7 fields**, consider:

- grouping props into objects
- creating smaller components

---

# 4. JSX Practices

## RTS-007 Avoid Inline Functions in JSX

Inline functions create a new function on every render.

❌ Avoid

```tsx
<button onClick={() => deleteUser(id)}>
```

✅ Preferred

```tsx
const handleDelete = () => deleteUser(id)

<button onClick={handleDelete}>
```

---

## RTS-008 Avoid Complex Logic in JSX

JSX should remain simple and readable.

❌ Avoid

```tsx
{
  users.filter((u) => u.active).map((u) => <User key={u.id} user={u} />);
}
```

✅ Preferred

```tsx
const activeUsers = users.filter((u) => u.active);

return activeUsers.map((user) => <User key={user.id} user={user} />);
```

---

## RTS-009 Always Provide Stable Keys for Lists

Keys must uniquely identify list elements.

❌ Avoid

```tsx
items.map((item, index) => <Item key={index} />);
```

✅ Preferred

```tsx
items.map((item) => <Item key={item.id} />);
```

---

# 5. React Hooks

## RTS-010 Only Call Hooks at the Top Level

Hooks must not be called inside:

- loops
- conditions
- nested functions

❌ Avoid

```tsx
if (user) {
  const [state, setState] = useState();
}
```

---

## RTS-011 Use Custom Hooks for Shared Logic

Shared component logic should be extracted into **custom hooks**.

Example:

```tsx
function useUserData(userId: string) {
  const [user, setUser] = useState<User | null>(null);
}
```

---

## RTS-012 Keep Hooks Focused

Hooks should have a **single responsibility**.

Avoid large hooks performing many unrelated tasks.

---

## RTS-013 Always Declare Hook Dependencies

React hooks such as `useEffect` must declare dependencies.

❌ Avoid

```tsx
useEffect(() => {
  fetchUsers();
}, []);
```

When dependencies exist they must be declared.

---

# 6. State Management

## RTS-014 Avoid Unnecessary State

State should only exist when it is required.

Derived data should not be stored in state.

❌ Avoid

```tsx
const [filteredUsers, setFilteredUsers] = useState([]);
```

✅ Preferred

```tsx
const filteredUsers = users.filter((u) => u.active);
```

---

## RTS-015 Prefer Local State First

Component state should remain local unless it must be shared.

Avoid prematurely introducing:

- global state
- context
- external state libraries

---

# 7. Performance

## RTS-016 Use React.memo for Expensive Components

Components that render frequently or contain heavy logic may benefit
from memoization.

Example:

```tsx
export default React.memo(UserCard);
```

---

## RTS-017 Avoid Unnecessary Re-renders

Avoid creating new objects or functions during render.

❌ Avoid

```tsx
<Component config={{ enabled: true }} />
```

✅ Preferred

```tsx
const config = { enabled: true }
<Component config={config} />
```

---

## RTS-018 Memoize Expensive Computations

Use `useMemo` when expensive computations run during rendering.

Example:

```tsx
const sortedUsers = useMemo(() => {
  return users.sort(sortUsers);
}, [users]);
```

---

# 8. File Organization

## RTS-019 One Component per File

Each component should live in its own file.

Example:

    UserCard.tsx
    UserCard.test.tsx
    UserCard.styles.ts

---

## RTS-020 Use Feature-Based Folder Structure

Prefer grouping by feature rather than file type.

Example:

    features/
      users/
        UserList.tsx
        UserService.ts
        useUsers.ts

---

# 9. Event Handling

## RTS-021 Prefix Event Handlers with "handle"

Event handlers should follow the naming convention:

    handleClick
    handleSubmit
    handleDelete

---

## RTS-022 Avoid Inline Event Logic

Complex logic should not be written inline inside event handlers.

❌ Avoid

```tsx
<button onClick={() => {
  deleteUser(id)
  logAction()
}}>
```

---

# 10. Testing

## RTS-023 Components Should Be Testable

Components should avoid hidden dependencies.

Prefer dependency injection via props or hooks.

---

## RTS-024 Avoid Business Logic in Components

Business logic placed inside components makes testing difficult.

Prefer extracting logic into:

- services
- hooks
- utilities

---

# 11. Accessibility

## RTS-025 Use Semantic HTML

Prefer semantic elements when possible.

Example:

    <button>
    <nav>
    <header>

Avoid using generic elements like `div` for interactive content.

---

## RTS-026 Always Provide Accessible Labels

Interactive elements must have accessible labels.

Example:

    <button aria-label="Delete user">

---

# 12. Summary

React + TypeScript code should prioritize:

- Component simplicity
- Type safety
- Predictable rendering
- Maintainable component architecture
- Accessibility

These rules help ensure a scalable and maintainable React codebase.
