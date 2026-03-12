# TypeScript Coding Guidelines

## 1. Purpose

This document defines **TypeScript-specific coding standards** for
projects using TypeScript.

These guidelines ensure:

-   Type safety
-   Maintainable code
-   Consistent code style
-   Reduced runtime errors
-   Improved developer productivity

These rules complement the **General Coding Guidelines** and any
**framework-specific standards**.

Example reference in code review:

Violation: TSC-002 -- Avoid using the `any` type

------------------------------------------------------------------------

# 2. Type Safety

## TSC-001 Always Enable Strict Mode

All TypeScript projects must enable strict type checking.

Required configuration:

``` json
{
  "compilerOptions": {
    "strict": true
  }
}
```

------------------------------------------------------------------------

## TSC-002 Avoid Using the `any` Type

The `any` type disables TypeScript's type checking.

Avoid using `any` unless absolutely necessary.

❌ Poor example

``` ts
function process(data: any) {
  return data.value
}
```

✅ Preferred

``` ts
interface Data {
  value: string
}

function process(data: Data) {
  return data.value
}
```

------------------------------------------------------------------------

## TSC-003 Prefer `unknown` Over `any`

When the type is truly unknown, use `unknown`.

``` ts
function parse(data: unknown) {
  if (typeof data === "object" && data !== null && "name" in data) {
    return (data as { name: string }).name
  }
}
```

------------------------------------------------------------------------

## TSC-004 Always Define Return Types for Public Functions

Public functions must explicitly declare return types.

``` ts
function getUser(): { id: number } {
  return { id: 1 }
}
```

------------------------------------------------------------------------

## TSC-005 Prefer Type Inference for Local Variables

Explicit types are unnecessary when TypeScript can infer them.

``` ts
const count = 5
```

------------------------------------------------------------------------

# 3. Interfaces and Types

## TSC-006 Prefer Interfaces for Object Contracts

``` ts
interface User {
  id: number
  name: string
}
```

------------------------------------------------------------------------

## TSC-007 Use `type` for Unions and Complex Types

``` ts
type Status = "pending" | "success" | "error"
```

------------------------------------------------------------------------

## TSC-008 Avoid Overly Complex Types

Prefer named types instead of deeply nested inline types.

------------------------------------------------------------------------

# 4. Null and Undefined Safety

## TSC-009 Always Handle `null` and `undefined`

``` ts
user?.name?.length
```

------------------------------------------------------------------------

## TSC-010 Avoid Non-Null Assertion (`!`) When Possible

``` ts
if (!user) {
  throw new Error("User not found")
}

return user.name
```

------------------------------------------------------------------------

# 5. Functions

## TSC-011 Keep Functions Pure When Possible

``` ts
function add(a: number, b: number): number {
  return a + b
}
```

------------------------------------------------------------------------

## TSC-012 Avoid Functions With Too Many Parameters

Prefer objects for many parameters.

``` ts
createUser({
  name,
  age,
  email,
  role,
  active
})
```

------------------------------------------------------------------------

## TSC-013 Use Arrow Functions for Short Callbacks

``` ts
items.map(item => item.name)
```

------------------------------------------------------------------------

# 6. Enums and Constants

## TSC-014 Prefer Union Types Over Enums

``` ts
type Status = "pending" | "completed"
```

------------------------------------------------------------------------

## TSC-015 Use `const` for Immutable Values

``` ts
const API_URL = "https://api.example.com"
```

------------------------------------------------------------------------

# 7. Async Code

## TSC-016 Prefer `async/await` Over `.then()`

``` ts
const user = await fetchUser()
console.log(user)
```

------------------------------------------------------------------------

## TSC-017 Always Handle Promise Errors

``` ts
try {
  await saveUser(user)
} catch (error) {
  logger.error(error)
}
```

------------------------------------------------------------------------

# 8. Imports and Modules

## TSC-018 Use Named Exports Instead of Default Exports

``` ts
export function getUser() {}
```

------------------------------------------------------------------------

## TSC-019 Avoid Deep Relative Imports

Prefer path aliases instead of long relative paths.

------------------------------------------------------------------------

# 9. Immutability

## TSC-020 Avoid Mutating Objects

``` ts
const updatedUser = { ...user, name: "John" }
```

------------------------------------------------------------------------

# 10. Type Guards

## TSC-021 Use Type Guards for Runtime Type Checking

``` ts
function isUser(obj: unknown): obj is User {
  return typeof obj === "object" && obj !== null && "id" in obj
}
```

------------------------------------------------------------------------

# 11. Generics

## TSC-022 Use Generics for Reusable Logic

``` ts
function identity<T>(value: T): T {
  return value
}
```

------------------------------------------------------------------------

## TSC-023 Avoid Overly Complex Generics

Prefer simpler generics for readability.

------------------------------------------------------------------------

# 12. Error Handling

## TSC-024 Throw Typed Errors

``` ts
throw new Error("User not found")
```

------------------------------------------------------------------------

# 13. Code Organization

## TSC-025 Group Related Types

Example structure:

user/ user.service.ts user.types.ts user.repository.ts

------------------------------------------------------------------------

## TSC-026 Avoid Global Types

Prefer module-level type definitions.

------------------------------------------------------------------------

# 14. Testing

## TSC-027 Type Test Mocks Correctly

Mocks should follow the original type definitions.

------------------------------------------------------------------------

# 15. Summary

TypeScript code should prioritize:

-   Type safety
-   Readability
-   Maintainability
-   Predictable behavior

Avoid bypassing the type system unless absolutely necessary.
