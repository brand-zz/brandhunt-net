<!--
  AGENTS.MD - SOURCE OF TRUTH
  This file is hosted at https://brandhunt.net/AGENTS.md
  If you are editing this file in the brandhunt-net repo, you are updating the global standard.
  If you are finding this file in another repo, DO NOT EDIT IT. Update it from the source above.
-->

# Agent Operating Protocol

This document defines the standard operating procedures and coding best practices for AI agents working on this repository. You must follow these guidelines to ensure consistency, quality, and maintainability.

## 1. Core Workflow

1.  **Explore & Plan**: Before writing code, list all files to understand the context. Create a detailed, step-by-step plan.
2.  **Atomic Steps**: Execute your plan in small, verifiable steps.
3.  **Verify First**: Never assume success.
    *   After creating/editing a file, `read_file` to confirm content.
    *   After changing logic, run tests or create a reproduction script.
4.  **No Regressions**: Run existing tests to ensure no functionality is broken.
5.  **Self-Correction**: If a step fails, pause. Analyze the error log, adjust the plan, and retry. Do not blindly repeat the same action.

## 2. General Engineering Principles

*   **Modernity**: Prefer modern language features and standard libraries over legacy patterns or third-party dependencies for trivial tasks.
*   **Safety**: Prioritize memory safety and type safety. Validate inputs at the boundary.
*   **Simplicity**: Write code that is easy to read and understand. Complexity should be opt-in.
*   **Documentation**: Document *why* a decision was made, not just *what* the code does.
*   **Git**:
    *   Commit often.
    *   Use Conventional Commits (e.g., `feat: ...`, `fix: ...`, `docs: ...`).
    *   Do not commit secrets, temporary files, or binary artifacts.

## 3. Language-Specific Standards

### Python
*   **Version**: 3.10+
*   **Style**: PEP 8. Use `ruff` or `black` for formatting.
*   **Typing**: Mandatory Type Hints (PEP 484). All function signatures must be typed.
*   **Testing**: Use `pytest`.
*   **Dependencies**: Manage with `poetry`, `uv`, or standard `requirements.txt`.

### JavaScript / TypeScript
*   **Preference**: Use TypeScript for robust applications; JavaScript for simple scripts.
*   **Style**: Prettier + ESLint (Standard or Airbnb config).
*   **Modern ES**: Use `const`/`let`, arrow functions, async/await, and destructuring.
*   **No `any`**: In TypeScript, avoid `any`. Use `unknown` or proper types.

### Rust
*   **Tooling**: `cargo fmt` and `cargo clippy` (must pass with no warnings).
*   **Idioms**:
    *   Use `Result` and `Option` for error handling. Avoid `unwrap()`/`expect()` in production code.
    *   Prefer idiomatic iterators (`.map()`, `.filter()`) over raw loops where clear.
    *   Leverage the Type System to make invalid states unrepresentable.

### C++
*   **Standard**: C++20 (or C++17 minimum).
*   **Memory**:
    *   **NO** raw `new`/`delete`. Use `std::unique_ptr` and `std::shared_ptr`.
    *   Use `std::vector` and `std::string` instead of raw arrays/C-strings.
*   **Style**: `.clang-format` (Google or LLVM style).
*   **Safety**: Enable compiler warnings (`-Wall -Wextra -Werror`).

### Java
*   **Version**: Java 17 LTS or newer.
*   **Style**: Google Java Style.
*   **Modern Features**: Use Records (`record`), Pattern Matching, and Switch Expressions.
*   **Concurrency**: Prefer `java.util.concurrent` over raw threads.

### HTML / CSS
*   **HTML**: Semantic tags (`header`, `main`, `footer`, `section`). Accessible ARIA attributes.
*   **CSS**:
    *   Mobile-First media queries.
    *   CSS Grid and Flexbox for layout.
    *   CSS Variables (`--var-name`) for colors/spacing.

## 4. Verification & Testing

*   **Test Driven**: Where possible, write a failing test case before implementing the feature.
*   **Visual Verification**: For frontend changes, inspect the DOM or screenshot if tools allow.
*   **Linter Checks**: Run strict linters before submitting.
