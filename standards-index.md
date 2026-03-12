# Coding Standards Index

## General Coding Guidelines (GCG)

### Core Principles

GCG-001 Readability
GCG-002 Maintainability
GCG-003 Consistency
GCG-004 Testability
GCG-005 Reliability

### Code Readability

GCG-006 Use Clear and Meaningful Names
GCG-007 Prefer Clarity Over Cleverness
GCG-008 Keep Functions Small and Focused
GCG-009 Avoid Deep Nesting

### Code Structure

GCG-010 Follow Separation of Concerns
GCG-011 Avoid Large Classes or Modules
GCG-012 Organize Code Logically

### Code Reuse

GCG-013 Avoid Code Duplication
GCG-014 Avoid Premature Abstraction

### Error Handling

GCG-015 Handle Errors Explicitly
GCG-016 Provide Meaningful Error Messages
GCG-017 Avoid Swallowing Exceptions

### Logging

GCG-018 Log Meaningful Events
GCG-019 Avoid Excessive Logging
GCG-020 Do Not Log Sensitive Data

### Configuration and Secrets

GCG-021 Do Not Hardcode Sensitive Information
GCG-022 Separate Configuration from Code

### Performance

GCG-023 Avoid Inefficient Operations
GCG-024 Avoid Premature Optimization

### Testing

GCG-025 Write Testable Code
GCG-026 Cover Critical Logic with Tests

### Documentation

GCG-027 Prefer Self-Documenting Code
GCG-028 Document Complex Logic
GCG-029 Avoid Redundant Comments

### Dependency Management

GCG-030 Use Dependencies Carefully
GCG-031 Maintain Dependencies

---

## TypeScript Coding Guidelines (TSC)

### Type Safety

TSC-001 Always Enable Strict Mode
TSC-002 Avoid Using the `any` Type
TSC-003 Prefer `unknown` Over `any`
TSC-004 Always Define Return Types for Public Functions
TSC-005 Prefer Type Inference for Local Variables

### Interfaces and Types

TSC-006 Prefer Interfaces for Object Contracts
TSC-007 Use `type` for Unions and Complex Types
TSC-008 Avoid Overly Complex Types

### Null and Undefined Safety

TSC-009 Always Handle `null` and `undefined`
TSC-010 Avoid Non-Null Assertion (`!`) When Possible

### Functions

TSC-011 Keep Functions Pure When Possible
TSC-012 Avoid Functions With Too Many Parameters
TSC-013 Use Arrow Functions for Short Callbacks

### Enums and Constants

TSC-014 Prefer Union Types Over Enums
TSC-015 Use `const` for Immutable Values

### Async Code

TSC-016 Prefer `async/await` Over `.then()`
TSC-017 Always Handle Promise Errors

### Imports and Modules

TSC-018 Use Named Exports Instead of Default Exports
TSC-019 Avoid Deep Relative Imports

### Immutability

TSC-020 Avoid Mutating Objects

### Type Guards

TSC-021 Use Type Guards for Runtime Type Checking

### Generics

TSC-022 Use Generics for Reusable Logic
TSC-023 Avoid Overly Complex Generics

### Error Handling

TSC-024 Throw Typed Errors

### Code Organization

TSC-025 Group Related Types
TSC-026 Avoid Global Types

### Testing

TSC-027 Type Test Mocks Correctly

---

## React + TypeScript Coding Guidelines (RTS)

### Component Design

RTS-001 Use Functional Components Only
RTS-002 Keep Components Small and Focused
RTS-003 Separate UI from Business Logic

### Props and Typing

RTS-004 Always Type Component Props
RTS-005 Prefer Interfaces for Props
RTS-006 Avoid Excessive Props

### JSX Practices

RTS-007 Avoid Inline Functions in JSX
RTS-008 Avoid Complex Logic in JSX
RTS-009 Always Provide Stable Keys for Lists

### React Hooks

RTS-010 Only Call Hooks at the Top Level
RTS-011 Use Custom Hooks for Shared Logic
RTS-012 Keep Hooks Focused
RTS-013 Always Declare Hook Dependencies

### State Management

RTS-014 Avoid Unnecessary State
RTS-015 Prefer Local State First

### Performance

RTS-016 Use React.memo for Expensive Components
RTS-017 Avoid Unnecessary Re-renders
RTS-018 Memoize Expensive Computations

### File Organization

RTS-019 One Component per File
RTS-020 Use Feature-Based Folder Structure

### Event Handling

RTS-021 Prefix Event Handlers with "handle"
RTS-022 Avoid Inline Event Logic

### Testing

RTS-023 Components Should Be Testable
RTS-024 Avoid Business Logic in Components

### Accessibility

RTS-025 Use Semantic HTML
RTS-026 Always Provide Accessible Labels
