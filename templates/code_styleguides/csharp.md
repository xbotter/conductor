# Google C# Style Guide Summary

This document summarizes key rules and best practices from the Google C# Style Guide.

## 1. Naming Conventions
- **PascalCase:** For class names, method names, constants, properties, namespaces, and public fields.
  - Example: `MyClass`, `GetValue()`, `MaxValue`
- **_camelCase:** For private, internal, and protected fields (with leading underscore).
  - Example: `_myField`, `_internalState`
- **camelCase:** For local variables and parameters.
  - Example: `localVariable`, `methodParameter`
- **Interfaces:** Prefix with `I` (e.g., `IMyInterface`).
- **Type Parameters:** Use descriptive names prefixed with `T` (e.g., `TValue`, `TKey`), or just `T` for simple cases.
- **Async Methods:** Suffix with `Async` (e.g., `GetDataAsync()`).

## 2. Formatting Rules
- **Indentation:** Use 2 spaces (never tabs).
- **Braces:** K&R style—no line break before the opening brace; keep `} else` on one line; braces required even when optional.
  ```csharp
  if (condition) {
    DoSomething();
  } else {
    DoSomethingElse();
  }
  ```
- **Line Length:** Column limit 100.
- **One Statement Per Line:** Each statement on its own line.
- **Column Alignment:** Align consecutive declarations and assignments for readability when appropriate.

## 3. Declaration Order
Within a class, enum, interface, or struct:
1. Constant fields
2. Static fields
3. Fields
4. Constructors
5. Finalizers (if any)
6. Delegates
7. Events
8. Enums
9. Interfaces (if any)
10. Properties
11. Indexers
12. Methods
13. Structs
14. Classes

## 4. Language Features
- **var:** Use `var` when the type is obvious from the right side. Avoid for basic types, numeric types, or when type clarity helps readability.
  ```csharp
  var apple = new Apple();  // Good - type is obvious
  bool success = true;  // Preferred over var for basic types
  ```
- **Expression-bodied Members:** Use sparingly for simple properties and lambdas; don't use on method definitions.
  ```csharp
  public int Age => _age;
  // Methods: prefer block bodies.
  ```
- **String Interpolation:** Prefer string interpolation over `String.Format()` or concatenation.
  ```csharp
  var message = $"Hello, {name}!";
  ```
- **Collection Initializers:** Use collection and object initializers when appropriate.
  ```csharp
  var list = new List<int> { 1, 2, 3 };
  ```
- **Null-conditional Operators:** Use `?.` and `??` to simplify null checks.
  ```csharp
  var length = text?.Length ?? 0;
  ```
- **Pattern Matching:** Use pattern matching for type checks and casts.
  ```csharp
  if (obj is string str) { /* use str */ }
  ```

## 5. Best Practices
- **Access Modifiers:** Always explicitly declare access modifiers (don't rely on defaults).
- **this:** Do not use `this.` unless required for disambiguation.
- **Ordering Modifiers:** Use standard order: `public protected private internal static extern new virtual abstract sealed override readonly unsafe volatile async`.
- **Namespace Imports:** Place `using` directives at the top of the file (outside namespaces); `System` first, then alphabetical.
- **LINQ:** Use LINQ for readability, but be mindful of performance in hot paths.
- **String Comparison:** Use `StringComparison` parameter for string comparisons.
  ```csharp
  if (name.Equals(other, StringComparison.OrdinalIgnoreCase))
  ```

## 6. Comments and Documentation
- **XML Documentation:** Use XML comments (`///`) for all public APIs.
  ```csharp
  /// <summary>
  /// Gets or sets the user name.
  /// </summary>
  public string UserName { get; set; }
  ```
- **Implementation Comments:** Use `//` for inline comments explaining complex logic.
- **TODO Comments:** Use `// TODO(username): Description` format.
- **Avoid Obvious Comments:** Comments should add value, not restate the code.

## 7. File Organization
- **One Class Per File:** Typically one class, interface, enum, or struct per file.
- **File Name:** Should match the name of the primary type in the file.
- **Namespace:** Should follow folder structure.

## 8. Disallowed Features
- **goto:** Do not use `goto` statements.
- **#regions:** **Avoid `#region`**. Organize code with proper file structure instead.

## 9. Parameters and Returns
- **out Parameters:** Permitted for output-only values; place `out` parameters after all other parameters. Prefer tuples or return types when they improve clarity.

## 10. Modern C# Features
- **Nullable Reference Types:** Enable and use nullable reference types (`#nullable enable`).
- **Records:** Use record types for immutable data models.
- **Init-only Properties:** Use `init` for immutable properties after construction.
- **Switch Expressions:** Prefer switch expressions over switch statements for assignments.
  ```csharp
  var result = value switch
  {
      1 => "one",
      2 => "two",
      _ => "other"
  };
  ```

**BE CONSISTENT.** When editing code, follow the existing style in the codebase.

*Source: [Google C# Style Guide](https://google.github.io/styleguide/csharp-style.html)*
