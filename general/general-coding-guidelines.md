# General Coding Guidelines

## 1. Purpose

This document defines the **general coding principles and best
practices** that apply to all software projects regardless of
programming language or framework.

These guidelines aim to ensure:

- High code quality
- Maintainable and readable code
- Consistent development practices
- Reduced bugs and technical debt
- Easier collaboration across teams

These rules serve as **baseline standards** and should be used together
with:

- Language-specific standards
- Framework-specific standards
- Enterprise / organization standards

Each rule includes a **Rule ID** so it can be referenced easily in code
reviews or automated AI reviews.

Example reference:

`Violation: GCG-003 – Keep Functions Small and Focused`

---

# 2. Core Principles

## GCG-001 Readability

Code must be easy for other developers to read and understand.

Prefer clear and simple implementations over clever or overly complex
solutions.

---

## GCG-002 Maintainability

Code should be easy to modify, extend, and debug without introducing
unintended side effects.

Well-structured code reduces long‑term maintenance cost.

---

## GCG-003 Consistency

Follow consistent patterns, naming conventions, and project structures
throughout the codebase.

Consistency reduces cognitive load when reading code.

---

## GCG-004 Testability

Code should be written in a way that enables reliable automated testing.

Avoid tight coupling that makes testing difficult.

---

## GCG-005 Reliability

Applications should handle unexpected scenarios gracefully and avoid
crashes or undefined behavior.

---

# 3. Code Readability

## GCG-006 Use Clear and Meaningful Names

Variables, functions, classes, and modules must have descriptive names
that clearly communicate their purpose.

Good examples:

    calculateTotalPrice
    userRepository
    orderService

Poor examples:

    calc
    data
    temp

Avoid unnecessary abbreviations unless they are widely understood.

---

## GCG-007 Prefer Clarity Over Cleverness

Prioritize readability and maintainability over clever tricks or
condensed expressions.

Readable code is easier to maintain and debug.

---

## GCG-008 Keep Functions Small and Focused

Functions should perform **a single well‑defined responsibility**.

Large functions that perform multiple tasks should be refactored into
smaller ones.

---

## GCG-009 Avoid Deep Nesting

Deep nesting reduces readability and increases complexity.

Prefer early returns or simplified control flow.

Example:

Instead of:

    if (user != null) {
      if (user.isActive) {
        if (user.hasPermission) {
           processRequest()
        }
      }
    }

Prefer:

    if (user == null) return
    if (!user.isActive) return
    if (!user.hasPermission) return

    processRequest()

---

# 4. Code Structure

## GCG-010 Follow Separation of Concerns

Each component should have a **single clear responsibility**.

Avoid mixing unrelated responsibilities in the same module, class, or
function.

Examples include separation of:

- UI logic
- Business logic
- Data access
- Infrastructure concerns

---

## GCG-011 Avoid Large Classes or Modules

Large files often indicate multiple responsibilities.

If a module grows excessively large, consider splitting it into smaller
components.

---

## GCG-012 Organize Code Logically

Code should be organized according to the system architecture.

Example structure:

    services/
    repositories/
    controllers/
    models/
    utils/

---

# 5. Code Reuse

## GCG-013 Avoid Code Duplication

Duplicate logic increases maintenance effort and the risk of
inconsistent behavior.

Common logic should be extracted into reusable utilities or shared
modules.

---

## GCG-014 Avoid Premature Abstraction

Do not introduce abstractions before they are necessary.

Abstractions should be introduced when duplication or complexity
justifies them.

---

# 6. Error Handling

## GCG-015 Handle Errors Explicitly

Errors should be handled intentionally and clearly.

Avoid ignoring errors or allowing failures to occur silently.

---

## GCG-016 Provide Meaningful Error Messages

Error messages should contain useful context that helps diagnose the
issue.

Avoid vague or generic messages.

---

## GCG-017 Avoid Swallowing Exceptions

Exceptions should not be caught and ignored without proper handling.

Poor example:

    catch (Exception e) {
    }

Better example:

    catch (Exception e) {
      log.error("Failed to process order", e)
      throw e
    }

---

# 7. Logging

## GCG-018 Log Meaningful Events

Logs should capture meaningful system events that help diagnose
problems.

---

## GCG-019 Avoid Excessive Logging

Excessive logs make debugging difficult and increase system noise.

Log only useful information.

---

## GCG-020 Do Not Log Sensitive Data

Sensitive information must never appear in logs.

Examples:

- Passwords
- API keys
- Tokens
- Personal user data

---

# 8. Configuration and Secrets

## GCG-021 Do Not Hardcode Sensitive Information

Sensitive information must never be stored directly in source code.

Examples:

- Database credentials
- API keys
- Encryption keys

Use environment variables or secret management tools.

---

## GCG-022 Separate Configuration from Code

Application configuration should be stored outside application logic
whenever possible.

This improves security and flexibility.

---

# 9. Performance

## GCG-023 Avoid Inefficient Operations

Avoid patterns that unnecessarily degrade performance such as:

- Inefficient loops
- Repeated expensive computations
- Redundant data processing

---

## GCG-024 Avoid Premature Optimization

Prioritize correctness and readability first.

Optimize only when performance problems are measurable.

---

# 10. Testing

## GCG-025 Write Testable Code

Code should be structured to allow reliable automated testing.

Avoid tightly coupling business logic to infrastructure or external
systems.

---

## GCG-026 Cover Critical Logic with Tests

Important business logic and edge cases should be covered with automated
tests.

---

# 11. Documentation

## GCG-027 Prefer Self‑Documenting Code

Use clear naming and structure so the code explains itself.

---

## GCG-028 Document Complex Logic

Add documentation when:

- Logic is complex
- Behavior is non‑obvious
- External integrations exist

---

## GCG-029 Avoid Redundant Comments

Comments should explain **why** something exists, not simply repeat what
the code already states.

Poor example:

    # increment counter
    counter += 1

---

# 12. Dependency Management

## GCG-030 Use Dependencies Carefully

External libraries should only be added when they provide clear value.

Avoid unnecessary dependencies.

---

## GCG-031 Maintain Dependencies

Dependencies should be kept updated to reduce security vulnerabilities
and compatibility issues.

---

# 13. Relationship with Other Standards

These guidelines provide **baseline practices**.

Additional standards may exist in:

    /standards/language/
    /standards/framework/
    /standards/security/
    /standards/enterprise/

When conflicts arise, **enterprise or project‑specific standards take
precedence**.

---

# 14. Summary

Developers should strive to write code that is:

- Clear
- Simple
- Maintainable
- Consistent
- Testable
- Secure

Good code is not only correct --- it is also **easy for other developers
to understand and evolve**.
