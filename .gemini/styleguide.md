# Company Kotlin Style Guide

## Introduction

This style guide outlines the coding conventions for Kotlin code developed at the Company.
It's based on [Kotlin coding conventions](https://kotlinlang.org/docs/coding-conventions.html),
but with some modifications to address specific needs and preferences within our organization.

## Key Principles

- **Readability:** Code should be easy to understand for all team members.
- **Maintainability:** Code should be easy to modify and extend.
- **Consistency:** Adhering to a consistent style across all projects improves collaboration and
  reduces errors.
- **Performance:** While readability is paramount, code should be efficient.
- **Scalability:** Code should be designed to scale with the project's growth.
- **Security:** Code should be written with security best practices in mind.
- **Documentation:** Code should be well-documented to aid understanding and maintenance.
- **Testing:** Code should be testable, with a focus on automated testing.
- **Automate:** Use tools to automate code formatting, linting, testing, build, and deployments.
- **Code Reviews:** Peers should review all code to ensure quality and consistency.
- **Pragmatic:** Don't follow the rules blindly; use your judgment to decide when to deviate.

## Unix Philosophy

- Write programs that do one thing and do it well.
- Write programs to work together.
- Write programs to handle text streams, because that is a universal interface.

## Design Principles

1. Beautiful is better than ugly.
2. Explicit is better than implicit.
3. Simple is better than complex.
4. Complex is better than complicated.
5. Flat is better than nested.
6. Sparse is better than dense.
7. Readability counts.
8. Special cases aren't special enough to break the rules.
9. Although practicality beats purity.
10. Errors should never pass silently.
11. Unless explicitly silenced.
12. In the face of ambiguity, refuse the temptation to guess.
13. There should be one-- and preferably only one --obvious way to do it.
14. Although that way may not be obvious at first unless you're Dutch.
15. Now is better than never.
16. Although never is often better than *right* now.
17. If the implementation is hard to explain, it's a bad idea.
18. If the implementation is easy to explain, it may be a good idea.

## Deviations from Kotlin coding conventions

### Line Length

- **Maximum line length:** 100 characters.
  - Modern screens allow for wider lines, improving code readability on laptops and other smaller
    screens in many cases.
  - Many common patterns in our codebase, like long strings or URLs, often exceed 80 characters.
  - Maximizing code per line.
  - Reducing code complexity per line.
  - Reducing arbitrary line breaks.
  - Enough space for side-by-side editor/comparison.
  - Enough space for navigation views in IDE.

### Indentation

- **Use 2 spaces per indentation level.**
  - 2 spaces is more compact (than 4 spaces) and allows for more code to be visible on the screen.

### Imports

- **Absolute imports:** Always use absolute imports for clarity.

### Newline at the End of the File

Mostly due to [historical reasons](https://thoughtbot.com/blog/no-newline-at-end-of-file),
every text file should end with a `\n` or "newline" character.

## Additional Naming rules

### Capitalizing Compound Words and Common Terms

- ❌️ DO NOT capitalize each word in so-called closed-form compound words.
  Treat a closed-form compound word as a single word.

  | ✔️️ Good      | ❌️ Bad                       |
  |---------------|------------------------------|
  | `callback`    | `CallBack`, `callBack`       |
  | `canceled`    | `cancelled`                  |
  | `email`       | `EMail`, `eMail`             |
  | `endpoint`    | `EndPoint`, `endPoint`       |
  | `filename`    | `FileName`, `fileName`       |
  | `gridline`    | `GridLine`, `gridLine`       |
  | `hashtable`   | `HashTable`, `hashTable`     |
  | `id`          | `ID`                         |
  | `indexes`     | `indices`                    |
  | `metadata`    | `MetaData`, `metaData`       |
  | `ok`          | `OK`                         |
  | `pi`          | `PI`                         |
  | `placeholder` | `PlaceHolder`, `placeHolder` |
  | `username`    | `UserName`,`userName`        |
  | `whitespace`  | `WhiteSpace`,`whiteSpace`    |

### Word Choice

- ✔️️ DO choose easily readable identifier names. For example, a property named `HorizontalAlignment`
  is more English-readable than `AlignmentHorizontal`.
- ✔️️ DO favor readability over brevity. For example, the property name `CanScrollHorizontall` is
  better than `ScrollableX` (an obscure reference to the X-axis).
- ❌️ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.
- ❌️ DO NOT use Hungarian notation.
- ❌️ AVOID using identifiers that conflict with keywords of widely used programming languages.
- ✔️️ DO use semantically interesting names rather than language-specific keywords for type names.
  For example, `GetLength` is a better name than `GetInt`.

### Abbreviations

- ❌️ DO NOT use abbreviations or contractions as part of identifier names.
  For example, use `GetWindow` rather than `GetWin`.
- ❌️ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.
- When appropriate, use well-known acronyms to replace lengthy phrase names.
  For example, use `UI` for User Interface, or `OLAP` for On-line Analytical Processing.

### Acronyms

- Two letter acronyms (like `IO` or `DB`), should have the same case for both letters.
  For example, for PascalCase identifiers (like a class name) you might have `DBRate` instead of
  `DbRate`, while for a camelCase identifier (like a local variable) you might have `ioChannel`.
- Three letters or longer acronyms use mixed case.
  For example, for PascalCase identifiers (like a class name) you might have `XmlDocument` instead
  of `XMLDocument`, while for a camelCase identifier (like a local variable) you might have
  `httpRequest`.

### Naming New Versions of Existing APIs

- ✔️️ DO use a name similar to the old API when creating new versions of an existing API.
  This helps to highlight the relationship between the APIs.
- ✔️️ DO prefer adding a suffix rather than a prefix to indicate a new version of an existing API.
  This will assist discovery when browsing documentation, or using autocomplete. The old version
  of the API will be organized close to the new APIs, because most browsers and autocomplete show
  identifiers in alphabetical order.
- ✔️️ CONSIDER using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.
- ✔️️ DO use a numeric suffix to indicate a new version of an existing API, particularly if the
  existing name of the API is the only name that makes sense (i.e. if it is an industry standard)
  and if adding any meaningful suffix (or changing the name) is not a appropriate option.
- ❌️ DO NOT use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier
  version of the same API.

### Boolean

#### 1. The Golden Rule

**A boolean variable name should sound like a Yes/No question.**

When placed inside a conditional statement (
`if`), the code should read like a natural English sentence.

- ✅ **Good:** `if (isOpen)` -> Reads as: "If it is open..."
- ❌ **Bad:** `if (open)` -> Reads as: "If open..." (Ambiguous: Is this a command? A state?)

#### 2. Choosing the Right Prefix

While
`is` is the most common prefix, it is not always the most accurate. Choose the auxiliary verb that best describes the
**nature** of the boolean.

##### A. State & Identity (`is`, `has`, `uses`, `exists`)

Use these for current properties or ownership.

| Prefix     | Usage                        | Example                                 |
|:-----------|:-----------------------------|:----------------------------------------|
| **`is`**   | General state or identity.   | `isValid`, `isVisible`, `isAdmin`       |
| **`has`**  | Ownership or containment.    | `hasChildren`, `hasErrors`, `hasAccess` |
| **`uses`** | Is it currently employing X? | `usesEncryption`, `usesCache`           |

| Suffix       | Usage                             | Example                      |
|:-------------|:----------------------------------|:-----------------------------|
| **`exists`** | Existence checks (often DB/File). | `fileExists`, `recordExists` |

##### B. Capabilities & Permissions (`can`, `allows`, `supports`, `requires`)

Use these to define what the system or user is able to do.

| Prefix         | Usage                          | Example                                 |
|:---------------|:-------------------------------|:----------------------------------------|
| **`can`**      | Ability to perform an action.  | `canExecute`, `canEdit`                 |
| **`allows`**   | Permission or policy settings. | `allowsGuestAccess`, `allowsDuplicates` |
| **`supports`** | Technical/Hardware features.   | `supportsBluetooth`, `supportsIPv6`     |
| **`requires`** | A hard dependency.             | `requiresAuth`, `requiresRestart`       |

##### C. Lifecycle & Time (`should`, `will`, `did`, `was`, `needs`)

Use these for future intent, past history, or recommendations.

| Prefix       | Usage                                | Example                          |
|:-------------|:-------------------------------------|:---------------------------------|
| **`should`** | Recommendation/necessity (often UI). | `shouldRender`, `shouldRetry`    |
| **`will`**   | Definitive future outcome.           | `willOverwrite`, `willBlock`     |
| **`did`**    | Completed action (history).          | `didFinish`, `didTimeout`        |
| **`was`**    | Previous historical state.           | `wasCreated`, `wasSeen`          |
| **`needs`**  | Requirement for a future state.      | `needsRefresh`, `needsMigration` |

##### D. Content (`contains`, `includes`, `matches`)

Use these for collections or string validation.

| Prefix         | Usage                         | Example                               |
|:---------------|:------------------------------|:--------------------------------------|
| **`contains`** | Membership in a collection.   | `containsItem`, `containsSpecialChar` |
| **`includes`** | Membership in a collection.   | `includesTax`                         |
| **`matches`**  | Regex or pattern conformance. | `matchesFilter`, `matchesRegex`       |

##### E. Plurals & Relationships (`are`)

Use this when checking the state of a group or a mutual relationship between multiple items.

| Prefix    | Usage                          | Example                                 |
|:----------|:-------------------------------|:----------------------------------------|
| **`are`** | Plural states or mutual links. | `areFriends`, `areEqual`, `areAllReady` |

#### 3. Anti-Patterns (What to Avoid)

##### 🚫 The "Flag" Suffix

Do not put the type in the name. We know it's a boolean; tell us what it means.

- **Bad:** `loginFlag`, `validStatus`, `checkBit`
- **Good:** `isLoggedIn`, `isValid`, `isChecked`

##### 🚫 Negatives

Keep logic positive. Standard convention is usually `isEnabled`.

- **Bad:** `isDisabled`, `disallowsGuest`, `excludesItem`
- **Good:** `isEnabled`, `allowsGuest`, `includesItem`

##### 🚫 Double Negatives

Logic becomes incredibly hard to parse when you negate a negative variable.

- **Bad:** `isNotEnabled` (Checking `!isNotEnabled` is painful).
- **Good:** `isEnabled`

##### 🚫 Ambiguous Nouns

A noun by itself usually implies an object (String, Class, Dictionary), not a boolean.

- **Bad:** `user`, `answer`, `file`
- **Good:** `isUser`, `hasAnswer`, `fileExists`

##### 🚫 Third-person Singular Question Form

- **Acceptable:** `doesFileExist` (Valid, answers Yes/No), `doesSupportHdr`
- **Better:** `fileExists`, `hasFile`, `supportsHdr`

##### 🚫 Commands

The word `do` is almost always a command.

- **Bad:** `doLog`, `doUpdate` (looks like a function name: `function doUpdate() { ... }`)
- **Good:** `shouldLog`, `isLoggingEnabled`, `isUpdated`

### DateTime

- For DateTime variables, use the postfix `At`:
  - Examples: `createdAt`, `updatedAt`, `deletedAt`, `enabledAt`, `disabledAt`.

### Function Name Prefix for Converting and Casting

- Use the `to` prefix when converting or creating a new type (e.g.
  [`toString()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/to-string.html),
  [`toInt()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/to-int.html),
  [`toList()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/to-list.html)).
- Use the `as` prefix when casting types (e.g.
  `List` as `Iterable` -> [`asIterable()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/as-iterable.html),
  `Cat` as `Animal` -> `asAnimal()`).

### Interfaces

Use a noun and short noun phrase for the interface, then using a prefix for each implementation
describing how it's implemented. e.g.:

- [`List`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html) interface, with implementations including [`ArrayList`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html) (using array), [`LinkedList`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/LinkedList.html) (using linked objects), etc.
- [`Set`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Set.html) interface, with implementations including [`HashSet`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html) (using hash table), [`TreeSet`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/TreeSet.html) (using tree map), etc.
- [`Map`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Map.html) interface, with implementations including [`HashMap`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashMap.html) (using hash table), [`LinkedHashMap`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/LinkedHashMap.html) (using linked map), etc.
- `Reader` interface, with implementations including `FileReader` and `StringReader`, etc.
- `Truck` interface, with implementations such as `DumpTruck`, `TransferTruck`, `CementTruck`, `TestTruck`, `FakeTruck`, `MainTruck`, etc.

Notes:

- Do not suffix the name of your class implementations with `Impl` (_implementation_)
  (such as `TruckImpl`), because that name is meaningless!

### `.not()` Operator Function

Kotlin provides the `.not()` operator function used for logical negation. For example:

```kotlin
val isLoggedIn = false
val isNotLoggedIn = isLoggedIn.not() // isNotLoggedIn == true

val hasPermission = true
val doesNotHavePermission = !hasPermission // equivalent to hasPermission.not()
```

Notes:

- The `.not()` operator is equivalent to the logical NOT operator (`!`) in Kotlin.
- The `.not()` is considered an operator function because it follows the naming convention of having
  a single dot (`.`) before the function name.
- **In most cases**, the `!` operator is preferred due to its readability, simplicity, and
  familiarity.
- The `.not()` operator might be useful in situations where you want to emphasize the negation
  operation or when dealing with custom data types that overload the `!` operator for different
  purposes.

## enum vs string

- If your set of parameters is limited and known at compile time,
  use [enum](https://en.wikipedia.org/wiki/Enumerated_type).
  (e.g., sex, types, etc.)
- If your set of parameters is open and unknown at compile time, use strings.
  (e.g., name, address, identifiers)

### Comments are not Version Control

Rules:

- [Comments are not a version control system](https://coding.abel.nu/2012/07/comments-are-not-version-control/).
- Never keep revision history in comments.
- Never check in commented out code.

Every set of rules has some exception; there are some cases where it might be acceptable to deviate
a bit from the rules, such as:

- Make the reader of the code aware of the hidden treasures in the source control history.

## Error Message

A good error message should contain the following three pieces of information:

1. **Context**: What led to the error? What was the code trying to do when it failed?
2. **The error itself**: What exactly failed?
3. **Mitigation**: What needs to be done to overcome the error?

### General recommendations

- **Uniform voice and style**: Maintain a consistent style in error messages, including voice,
  casing, and punctuation, to improve readability.
- **One concept, one term**: Use a single, consistent term for each concept across all error
  messages and documentation to prevent confusion.
- **Do not localize error messages**: Keep error messages in English for developers; if localization
  is needed, include a common error code for easier searching.
- **Do not make error messages an API contract**: Enable programmatic error handling by providing
  machine-readable error codes or specific exception types, rather than requiring message parsing.
- **Be cautious about exposing sensitive data**: Avoid including sensitive user information in error
  messages to prevent privacy issues, particularly with data protected by regulations like GDPR.
- **Either raise an exception OR log an error, but not both**: Report each error by either raising
  an exception or logging it, but not both, to avoid redundant and confusing notifications.
- **Fail early**: Report errors as soon as possible—ideally during build or start-up rather than at
  runtime—to facilitate faster fixes and provide better context.

## Logging

- **Use a standard logging framework:** Use the built-in Spring Boot default logging module (SLF4J).
- **Log at appropriate levels:** `ERROR`, `WARN`, `INFO`, `DEBUG`, or `TRACE`.
  - use `INFO` or `WARN` in production. These levels capture critical events without flooding the
    logs with unnecessary detail.
  - use `DEBUG` or `TRACE` during development or troubleshooting.
- **Provide context:** Include relevant information in log messages to aid debugging.

## Tooling

- **Code formatter:**
  - [Detekt](https://detekt.dev/) - Enforces consistent formatting automatically.
- **Linter:**
  - [Ktlint](https://pinterest.github.io/ktlint/) - Identifies potential issues and style violations.
