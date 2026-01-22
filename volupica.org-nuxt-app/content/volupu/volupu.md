# Volupu










## Introduction

Volupu stands for Volupism language.

Volupu is a programming language that offers:
  - Static type system with type parameters and erased generics.
  - Transpiler written in Rust by AI. The transpiler is available in the browser as WASM module.
  - Translation of Volupu programs to:
    - nuxt.js for websites for search engines.
    - SwiftUI on Apple operating systems.
    - GUI on Google operating systems.
  - Declaration of content in Volupu text. Volupu should be a replacement for HTML, markdown, js frameworks, and Microsoft office products for content creators.
  - Assumption of garbage collection.
  - Reactivity with the TQ paradigm.
  - Functions are without side effects but there is the TQ paradigm that allows mutable state that is shared among parallel threads.
  - Functions in Record and Enum values are dynamically dispatched.
  - Higher order functions are dynamically dispatched.
  - Type information determined at compile-time with the type type.
  - No function overloading.
  - Limited object orientation. Values can have member functions.
  - No type extension.
  - No interface type. Instead use functions that create a new value and dynamically dispatched functions.
  - No trait type. Instead use functions that create a new value and dynamically dispatched functions.

Volupu is meant to be read and written by:
- Humans who are willing to learn Volupu.
- General AI (that is not trained on Volupu) should be able to learn Volupu from the Volupu spec in context.

In January 2026: Volupu was designed to be optimal for general AI like ChatGPT, Claude, and Gemini to write, read, and debug Volupu text and Native apps.










## Volupu OS

The Volupu OS is the operating system or platform for the creation and execution of Native app.
- [Native app](#native-app)

General AI must be able to translate any Volupu text to the following OS:
- HTML + nuxt.js + other libraries. The website must have optimal semantic meaning for search engine optimization.
- Apple OS + SwiftUI.
- Google OS + native UI framework.










## Native app

A native app is an application in the Volupu OS that was created as translation of the main Task.










### Allowed characters in Volupu text

To support "all valid text including emojis" while maintaining security, here is the complete **Allowlist** for Volupu.



#### The Broad Categories (Allow All)
These are safe to allow in their entirety for a specification language that supports natural language text.

* **L (Letters):** All (`Lu`, `Ll`, `Lt`, `Lm`, `Lo`).
* **N (Numbers):** All (`Nd`, `Nl`, `No`).
* **P (Punctuation):** All (`Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, `Po`).
* **S (Symbols):** All (`Sm`, `Sc`, `Sk`, `So`). *This covers math and emojis.*
* **M (Marks):** All (`Mn`, `Mc`, `Me`). *This covers accents.*



#### The Specific Exceptions (Specific Characters Only)
These categories are generally dangerous, so we only allow specific useful characters and prohibit the rest.

| Category | Character Name            | Hex Code | Reason                                                                    |
| :------- | :------------------------ | :------- | :------------------------------------------------------------------------ |
| **Zs**   | **Space**                 | `U+0020` | Standard word separation.                                                 |
| **Zs**   | **No-Break Space**        | `U+00A0` | Common in AI/Web input. **Normalize** to `U+0020`.                        |
| **Cc**   | **Horizontal Tab**        | `U+0009` | Indentation.                                                              |
| **Cc**   | **Line Feed**             | `U+000A` | Newline (Unix).                                                           |
| **Cc**   | **Carriage Return**       | `U+000D` | Newline (Windows).                                                        |
| **Cf**   | **Soft Hyphen**           | `U+00AD` | Common invisible formatting artifact. **Strip**.                          |
| **Cf**   | **Left-to-Right Mark**    | `U+200E` | **Required** for mixed LTR/RTL text (e.g., English inside Arabic).        |
| **Cf**   | **Right-to-Left Mark**    | `U+200F` | **Required** for mixed LTR/RTL text (e.g., Hebrew inside English).        |
| **Cf**   | **Zero Width Joiner**     | `U+200D` | **Required** for complex emojis (Family, flags, skin tones).              |
| **Cf**   | **Variation Selector-15** | `U+FE0E` | **Required** to force text-style rendering (e.g., black & white symbols). |
| **Cf**   | **Variation Selector-16** | `U+FE0F` | **Required** to force emoji rendering (e.g., making "▶" colorful).        |



#### Summary of the Logic
1.  **Input Character comes in.**
2.  **Is it in L, N, P, S, or M?** -> **✅ Pass.**
3.  **Is it one of the 6 specific exceptions (Space, Tab, LF, CR, ZWJ, Volupu16)?** -> **✅ Pass.**
4.  **Everything else?** -> **⛔ Reject.**

**Any other character is forbidden.**











## Block

A block is a term related to Volupu syntax.

A block can be:
- [Bracket block](#bracket-block)
- [File block](#file-block)

A block can have only 0 or 1 outer block that contains the block.

Within a block: Unbalanced brackets must be declared within strings.










## Outer block

An outer block can contain inner blocks.










## Inner block

An inner block is contained in an outer block.

An inner block has always 1 and only 1 immediate outer block.










## File block

A file block is the content of a file that is outside of every other block.










## Bracket block

A bracket block is delimited by brackets.

Volupu offers these bracket blocks:
- [Curly block](#curly-block)
- [Flat block](#flat-block)
- [Round block](#round-block)










## Curly block

A curly block is delimited by "{" and "}" as curly brackets.

A curly block contains a sequence of 0 or more statements where the linefeed codepoint is the required separator.

A curly block that follows a point indicates replacement of members of the preceding Record or Enum value.
- [f member](#f-member)









## Flat block

A flat block is delimited by "[" and "]" as flat brackets.

A flat block is used for c and u values.
- [c keyword](#c-keyword)
- [u keyword](#u-keyword)










## Round block

A round block is delimited by "(" and ")" as round brackets.

A round block is used for a sequence of 0 or more parameters or values where the comma codepoint is the required separator.

A round block that follows a point indicates replacement of members of the preceding Record or Enum value.
- [f member](#f-member)

The comma after "(" is discarded.

The comma before ")" is discarded.










## Comment

`//` indicates a comment.

The comment keyword indicates a comment line.

// is used because AI in 2025 is trained to use // for comments.



### Example

```vlpt
// comment text
 // as part of some text 
```

Where:
- // as keyword indicates a comment.
- // after the space keyword is recognized as literal text //.










## Statement

A statement can be:
- [File statement](#file-statement)
- [Function statement](#function-statement)










## File statement

A file statement is declared in a file block.

The following statements are file statements:
- import statement.
  - [import keyword](#import-keyword)
- [Variable definition](#variable-definition)
- Function type definition.
  - [fn keyword](#fn-keyword)
- Function definition definition.
  - [fn keyword](#fn-keyword)
- Record type definition.
  - [Record type](#record-type)
- Enum type definition.
  - [Enum type](#enum-type)
- Task type definition.
  - [Task type](#task-type)










## Function statement

A function statement is declared:
- in the curly block of a function.
- in the curly block after the if keyword.
- in the curly block after the if else keywords.
- in the curly block after the else keyword.
- in the curly block after the Enum match guard.

The following statements are function statements:
- [Variable definition](#variable-definition)
- Return statement with the return keyword.
  - [return keyword](#return-keyword)
- If statement with the if keyword.
  - [if keyword](#if-keyword)
- If else statement with the if else keywords.
  - [if else keywords](#else-if-keywords)
- Else statement with the else keyword.
  - [else keyword](#else-keyword)
- Match statement with the match keyword.
  - [match keyword](#match-keyword)










## Expression

An expression is like an expression in other languages.

An expression is a sequence of tokens in Volupu text.

An expression can be:
- [Name](#name)
- [Name path](#name-path)
- [Number](#number)
- [Value](#value)
- [Function](#function)
- [Function call](#function-call)
- [Operator usage](#operator-usage)
- [Variable definition](#variable-definition)
- [Record copy](#record-copy)










## Value

A value is an instance of a value type.










## Outer value

An outer value can contain inner values.










## Inner value

An inner value is contained in an outer value.

An inner value has always 1 and only 1 immediate outer value.










## Type

A type is like a type in other programming languages.










## Type parameter

A type parameter is a type parameter like in other programming languages.










## Type argument

A type argument is bound to a type parameter in a type declaration.

The declaration of the type argument is not required when the transpiler can guess the type argument.



### Example 1

```Volupu
List(Int)(1, 2, 3)
List(T: Int)(1, 2, 3)
```

Where:
- T is the name of the type parameter that can be used for named type arguMents.










## Name

A name is an identifier in other languages.

A name must not be a keyword in the Volupu version that is used.
- [Volupu](#Volupu-keyword)



### Rust regex of a valid Volupu name

```rust
r"^(r#)?(\p{XID_Start}|_)\p{XID_Continue}*$"
```

A valid name can still be invalid because the name equals a key keyword.

Different Volupu versions can have different keywords.



### Recommended naming convention

- PascalCase for type names in European letters.
- camelCase for all other names in European letters.










## Name path

A name path is like a qualified name in a programming language.



### Example

```Volupu
name1.name2.name3
```

Where:
- The meaning is like in other programming languages.
- name1 is a name in the outer block where the field path is declared.










## Number

These patterns use `[0-9]` instead of `\d` to enforce strict ASCII digits, ensuring high compatibility with code parsers and avoiding Unicode normalization issues.

The lowline (underscore) character _ is allowed according to the rule found in languages like Python (3.6+), Java (7+), and C#: underscores can appear between digits but cannot be leading, trailing, or consecutive.



### Unsigned Integer

Matches strict positive whole numbers.

```rust
r"^[0-9]+(?:_[0-9]+)*$"
```



### Statened Integer

Matches whole numbers with an optional `+` or `-` sign.

```rust
r"^[+-]?[0-9]+(?:_[0-9]+)*$"
```



### Floating Point Number (Standard)

Matches decimal numbers. This pattern requires at least one digit before and after the dot (e.g., `0.5` not `.5`) to minimize ambiguity for tokenizers.

```rust
r"^[+-]?[0-9]+(?:_[0-9]+)*\.[0-9]+(?:_[0-9]+)*$"
```



### Number with Scientific Notation

Matches numbers with an exponent. This covers integer-scientific (`1e10`) and float-scientific (`1.5E-10`) formats.

```rust
r"^[+-]?[0-9]+(?:_[0-9]+)*(?:\.[0-9]+(?:_[0-9]+)*)?[eE][+-]?[0-9]+(?:_[0-9]+)*$"
```



### Shape

If the number is in flat block or round block then the string is integrated in the text of the flat block or round block.
Else the shape of a number is the shape of a flat block.










## String

String is the Type of a String value.

A string is a value with String type.

There are 3 ways to declare a string Volupu:
- [Inline string](#inline-string)
- [c keyword](#c-keyword)
- [u keyword](#u-keyword)



### Shape

A string has no shape.

Use a Text value instead.
- [Text](#text)










## Inline string

An inline string is delimited by quotation marks like in other programming languages.



### Example

```Volupu
"some string"
```

Where:
- Inline strings must begin and end on the same line.
- Only allowed characters are allowed in string content.
- Escape sequences are recognized in an inline string.



### Escape sequences

The compiler recognizes escape sequences only in string content.

The only valid escape sequences in Volupu:
- \" : Literal Double Quote.
- \\ : Literal Backslash.
- \n : Line Feed.
- \r : Carriage Return.
- \t : Tab.
- \u{1F680} : For Unicode codepoint U+1F680. The number is a hexadecimal number from 0 to 10FFFF included. This aligns with Rust strings.



### Shape

There is no shape for a string type value.

If the string is in flat block:
  - Then string is integrated in the c or u value.
Else if the string is in another:
  - Then the string stands for a value with string type.










## Operator

Volupu offers operators like in other languages.
- [Math operator](#math-operator)
- [Bool operator](#bool-operator)
- [copy operator][#copy-operator]
- [imCopy operator][#imCopy-operator]
- [mutCopy operator][#mutCopy-operator]
- [Question operator][#question-operator]

The technical implementation depends on the Volupu transpiler and the Volupu OS.










## Operator usage

The syntax of operator usage depends on the operator.










## Operator precedence

Operators have lower precedence than functions and thus can use the output of function calls as arguments.

All operators have the same precedence: Left before right.

A different precedence must be declared with round blocks. 










## Math operator

Volupu offers math operators like other languages:
- +
- -
- *
- /










## Bool operator

Volupu offers bool operators like other languages:
- and
- or
- xor
- not



### Example 1

```Volupu
b1 and b2 and b3
```

Where:
- b1, b2, and b3 are bools.



### Example 2

```Volupu
b1 or b2 or b3
```

Where:
- b1, b2, and b3 are bools.



### Example 2

```Volupu
b1 xor b2 xor b3
```

Where:
- b1, b2, and b3 are bools.



### Example 2

```Volupu
not b1
```

Where:
- b1 is a bool.










## copy operator

The copy operator creates a copy of a value.

The mut qualifier of the copies is preserved.
- [mut qualifier](#mut-qualifier)

The copy operator has 2 parameters:
- The first parameter is a CopyEnum type for shallow or deep copy.
- The second parameter is the value that should be copied.










## imCopy operator

The imCopy operator creates a copy of a value.

The mut qualifier is removed in the copied value.
- [mut qualifier](#mut-qualifier)

The copy operator has 2 parameters:
- The first parameter has a CopyEnum type for shallow or deep copy.
- The second parameter is the value that should be copied.










## mutCopy operator

The mutCopy operator creates a copy of a value.

The mut qualifier is added to the copied value.
- [mut qualifier](#mut-qualifier)










## Question operator















## Function

A function is like a function in other languages.

A function is defined with the fn keyword.
- [fn keyword](#fn-keyword)

Volupu does not offer function overloading because function overloading introduces many difficulties. Instead Volupu offers Enum candy.
- [Enum candy](#enum-candy)

Functions are without side effects but there is the TQ paradigm for mutable data.
- [TQ paradigm](#TQ-paradigm)

Functions in file blocks are statically dispatched.
- [File block](#file-block)

Functions in values AKA member functions are dynamically dispatched.
- [Record](#record)
- [Enum](#enum)

Higher order functions are dynamically dispatched.










## Member function

A member function is a function that is accessed from a Record value or Enum case value.
- [Record](#record)
- [Enum](#enum)

The technical implementation depends on the transpiler and the Volupu OS.

Related:
- [me keyword](#me-keyword)
- [me output](#me-output)
- [me type](#me-type)
- [me value](#me-value)










## Closure

A closure is like a closure in other languages.

Every function can capture variables from the definition site because:
- This offers important flexibility with function type constraints.
- This is best for general AI in 2026.

The transpiler decides how to implement a function.
 
Higher order functions are always implemented as closures.

Member functions are always implemented as closures.
- [Member function](#member-function)










## Function with type parameter

A function with type parameter is also called a generic function.

Volupu does not offer function overloading.

If a function definition or function type definition contains 2 round blocks then the first round block is always the block with type parameters.

The round block with 0 or more parameter definitions is always required in a function definition or function type definition.



### Example 1

```Volupu
fn name1 (T2, T3) (param4: T2) T3 {
  ...
}
```

Where:
- If 2 round blocks follow the fn keyword or the function name, then the first round block contains a sequence of 1 or more type parameters.
- ... is a place holder for a sequence of function statements.
  - [Function statement](#function-statement)



### Example 2

```Volupu
fn (T2, T3) (param4: List(Int32), param5: List(T2)) T3
```

Where:
- If 2 round blocks follow the fn keyword or the function name, then the first round block contains a sequence of 1 or more type parameters.
- param4 can be bound to a value with List(Int32) as type.
- param5 can be bound to a value with List(T2) type where T2 can be any type. The function can use items of param5 only with functions that can also use items with type T. The implementation depends on the transpiler and the Volupu OS.










## Function call

A function call is like in other languages.

A function call is done with named arguments.

Volupu offers the hybrid argument model like in Python and Kotlin.

Named arguments must be declared after positional arguments.



### Example 1

```Volupu
functionName()
```



### Example 2

```Volupu
add(1, 2)

add(1, b: 2) 

add(a: 1, b: 2)
```

Where:
- Named arguments must be declared after positional arguments.



### Example 3

```Volupu
functionName(Type1, T2: Type3)(arg4, arg5, param6: arg7)
```

Where:
- If 2 round blocks follow the function name then the first round block contains arguments for the type parameters. Named arguments can be used for type parameters too. In this example: T2 is the name of the type parameter as declared in the function type.



### Example 4

```Volupu
record1.function2(Type2, Type3)(arg4, arg5, param6: arg7)
```

Where:
- record1 is a Record value that contains the member function.
- function2 is a member function in record1.
- record1 is the first argument given to function2. Like in object oriented languages. 










## Record

A Record is a value with a Record type.
- [Record type](#record-type)

A Record in Volupu is like a struct or Record in other languages.

A Record can have member functions.
- [Member function](#member-function)










## Record type

A Record type is the type of a Record.
- [Record](#record)

A Record type is defined with the rec keyword.
-[rec keyword](#rec-keyword)



### Example 1

```Volupu
rec Type1 {
  field2: Type3 = value4
  field5: Type6 = value7
}
```


### Example 2

```Volupu
rec Type1 (T2, T3) {
  field4: T2
  field5: T3
  field6: T3
}
```

Where:
- If 1 round block follows the type name then the round block contains a sequence of 1 or more type parameters.



## Limitations

- All members of a Record have implicitly the public qualifier. The private qualifier must be explicitly declared.
  - [private qualifier](#private-qualifier)
  - [public qualifier](#public-qualifier)










## Record copy

A Record copy is a shallow copy of an existing Record.



### Example 1

```Volupu
record1.{}
record1.()
```
Where:
- record1 is a Record value.
- record1.{} creates a shallow copy of record1.
- record1.() creates a shallow copy of record1.



### Example 2

```Volupu
record1.{
  f.{
    width: "50%em"
    height: "10em"
  }
}
```

Where:
- record1 is a Record value.
- record1.f is a Record value.
- record1.{} indicates replacement of members in the copy of record1. Linefeed is the separator in curly blocks.
- f.{} indicates replacement of members in the copy of f. Linefeed is the separator in curly blocks.
- The output of this expression is a copy of record1.




### Example 2

```Volupu
record1.{
  f.(width: "50%em", height: "10em")
}
```

Where:
- record1 is a Record value.
- record1.f is a Record value.
- record1.{} indicates replacement of members in the copy of record1. Linefeed is the separator in curly blocks.
- f.() indicates replacement of members in the copy of f. Comma is the separator in round blocks.
- The output of this expression is a copy of record1.










## Enum

An Enum is a value with an Enum type.
- [Enum type](#enum-type)

An Enum is like an Enum in other languages.

Related:
- [match keyword](#match-keyword)
- [Question operator](#question-operator)



### Enum member

An enum member is the member that is stored in the Enum.

An Enum can have member functions as part of an Enum case.
- [Member function](#member-function)



### Enum member name

The enum member name is the name that identifies the case for which the Enum member is stored.



### Example 1

```Volupu
EnumType.memberName(arg1, arg2, param3: arg4)
```

Where:
- The case name is used like the function name.
- The field names are used like parameter names.



### Example 2

```Volupu
EnumType.caseName(Type1, Type2)(arg1, arg2, param3: arg4)
```

Where:
- If 2 round blocks follow the case name then the first round block contains arguments for the type parameters. Named arguments can be used for type parameters too. In this example: T2 is the name of the type parameter as declared in the RecordType.










## Enum type

An Enum type is the type of a Enum.
- [Enum](#enum)

An Enum type is defined with the Enum keyword.
- [Enum keyword](#enum-keyword)

An Enum type or Enum value can not contain functions.



### Example 1

```Volupu
Enum ServerResponse {
    case success
    case error(code: Int32, message: String)
    case loading(time: Float32)
}
```



### Example 2

```Volupu
Enum ServerResponse(T1) {
    case success()
    case error(code: Int32, message: T1)
    case loading(time: Float32)
}
```

Where:
- If 1 round block follows the type name then the round block contains a sequence of 1 or more type parameters.










## Enum candy

Volupu offers Enum candy like the Swift language by making the Enum type optional for the creation of an Enum.
- [Candy](#candy)



### Example 1

```Volupu
record1.name2 = .name3(value4, value5)
```

Where:
- If the name2 type is an Enum type then .name3 indicates that the corresponding name3 case should be created.



### Example 2

```Volupu
fun1(.name2(value2, value4))
```

Where:
- If the fun1 function requires an Enum as first explicit argument then .name2 indicates that the corresponding name2 case should be created.










## Mark

A Mark is a type with a Mark type.
- [Mark type](#mark-type)

A  Mark can be used as type argument.



### Example 1

```Volupu
mark PopMark {
  first
  last
}

rec Type1(name2: PopMark, T3){
  name2: fn() Type1 {
    return Type1(PopMark.first, Type4)
  }
}
```










## Mark type

A Mark type is the type of a Mark.
- [Mark](#mark)

By using the mark keyword.
- [mark keyword](#mark-keyword)



### Example 1

```Volupu
mark PopMark {
  first
  last
}
```










## Variable definition

A variable definition is like in other languages.

A variable definition is a file statement and a function statement. 



### Example 1

```Volupu
name1 = exp3
```

Where:
- name1 is the variable.
- exp3 indicates the item that is bound to name1 variable.

The variable type is not declared explicitly because:
- The decreases efforts to read and write Volupu text for humans and AI.
- The decreases the length of Volupu text and thus required tokens in AI context.
- The type of every expression can be derived from the expression.










## Shape

A shape is graphical representation of a value.

Not every value is represented by a shape.

The f member is used to modify the shape of a value.
- [f member](#f-member)



### Why the term shape

Because:
- Shape is easy to pronounce.
- Shape is unusual and not confounded with terms of other GUI frameworks.










## f member

Every value (that is represented by a shape) has an f member with information about the shape of the value that contains the f value.

The f member is a Record value.

The f value is like the style attribute in HTML.

The values in the f value must be easily portable to all Volupu OS.
- [Volupu OS](#Volupu-os)



### Example 1

```Volupu
value1.{
  f.{
    width: "50%em"
    height: "10em"
  }
}
```

Where:
- The expression is a Record copy.
  - [Record copy](#record-copy)



### Example 2

```Volupu
value1.{
  f.(width: "50%em", height: "10em")
}
```

Where:
- The expression is a Record copy.
  - [Record copy](#record-copy)



### Why f as member name

- f for form (or format).
- f is easy to write and pronounce.
- No shape member because this would cause confusion about what is meant by shape: Concept or member.
- No style member because style is more effort to write and pronounce.
- No s member because:
  - s might be useful for another keyword.
  - s might be more difficult to pronounce than f.










## Error handling

Error handling is done with:
- [Enum type](#enum-type)
- [NativeTrace type](#nativetrace-type)
- [Opt type](#opt-type)
- [Result type](#result-type)
- [Trace type](#trace-type)










## Result type

The Result type is an Enum for error handling.
- [Enum](#enum)
- [Error handling](#error-handling)



### Result type definition

```volupl
// The Result Pattern (Standard Return Type)
enum Result(T) {
  case success(item: T)
  case error(message: String, trace: Opt(Trace))
}
```










## Trace type

The Trace type is used for stack traces.
- [Enum](#enum)
- [Error handling](#error-handling)



### Trace type definition

```volupl
// The Trace Record (High-Level Context)
rec Trace {
  public file: String
  public line: Int32
  public functionName: String
  public native: NativeTrace  // Explicitly tagged source
  public parent: Opt(Trace)
}
```










## NativeTrace type

The NativeTrace type is used for stack traces.
- [Enum](#enum)
- [Error handling](#error-handling)



### Trace type definition

```volupl
// The Native Trace (Low-Level Data)
// Using an Enum here removes the need to guess the OS specific trace format.
Enum NativeTrace {
  case android(trace: String)  // Java/Android stacks
  case ios(trace: String)   // Swift/Mach-O symbols
  case js(trace: String)  // Javascript/nuxt errors
  case macos(trace: String)   // Swift/Mach-O symbols
  case wasm(trace: String)    // Rust/Wasm panics
}
```










## Multithreading

Multithreading is done with Apps.
- [TQ paradigm](#TQ-paradigm)










## Reactivity

Volupu does not offer reactivity like popular GUI in 2026.

Volupu offers the TQ paradigm where Apps are used as event handlers.
- [TQ paradigm](#TQ-paradigm)










## Event handling.

Event handling is done with Apps.
- [TQ paradigm](#TQ-paradigm)










## TQ paradigm

The TQ paradigm comprises:
- [Task type](#task-type)
- [Q type](#q-type)

Q = synchronized queue value.



### Frequency of Tasks

Task values have a desired min and max frequency of computation per second.

Volupu OS is not a real time OS.

Volupu OS determines the actual frequency of Tasks based on the fullness of IMO values.

Volupu OS is implemented to avoid out of memory problems before out of time problems.



### Minimizing head-of-Line Blocking

This is done by computing tasks ( that receive elements from UI events) first by setting the frequency per second accordingly.

Furthermore:
- Tasks have a priority. Tasks with higher priority are computed before tasks with lower priority.
- The priority is more important then the desired frequency.










## Keywords

- [c keyword](#c-keyword)
- [Cit keyword](#cit-keyword)
- [Col keyword](#col-keyword)
- [Coltab keyword](#coltab-keyword)
- [Doc keyword](#doc-keyword)
- [Enum keyword](#enum-keyword)
- [fn keyword](#fn-keyword)
- [import keyword](#import-keyword)
- [mark keyword](#mark-keyword)
- [me keyword](#me-keyword)
- [L keyword](#l-keyword)
- [Ln keyword](#ln-keyword)
- [Ol keyword](#ol-keyword)
- [Row keyword](#row-keyword)
- [State keyword](#state-keyword)
- [string keyword](#string-keyword)
- [Tab keyword](#tab-keyword)
- [Text keyword](#text-keyword)
- [Todo keyword](#todo-keyword)
- [rec keyword](#rec-keyword)
- [U keyword](#u-keyword)
- [Ul keyword](#ul-keyword)
- [Volupu keyword](#Volupu-keyword)










## Volupu keyword

The Volupu keyword is followed by the version number of Volupu that is used in the current file.

The Volupu keyword:
- must be declared before any other statement and expression.
- can be declared only once in a file. A different file can contain text in a different Volupu version.

The Volupu version is important in order to determine:
- What is a keyword.
- How to translate expressions.



### Example

```Volupu
Volupu(1)
```

Where:
- Volupu is the Volupu keyword.
- (1) indicates the version 1 declared as round block.










## import keyword

The import keyword is used to refer to a Volupu file as file block.
- [File block](#file-block)

An import is Volupu text that is located:
- either by a file path.
- or by a URI.



### Example of import

```Volupu
import name "URI"
```

Where:
- name is the name of the imported file block. All names declared in the imported file block must be access with the import name as prefix. Example: name.itemName. 










## c keyword

The c keyword is used to declare a string.
- [String][#string]

c for cut.

All characters within the c block are preserved except:
- the line feed character immediately after [ is discarded.
- the line feed character immediately before ] is discarded.
- every sequence of space codepoints and horizontal tabs codepoints is replaced with a single space codepoint. 



### Declaration

```Volupu
c[some text]
```

Where:
- Escape sequences are not recognized within a c block.
- Volupu syntax is not recognized within a c block.
- Unbalanced brackets must be put in strings literals like e.g. "[" or "]".



### Why the c keyword

Because:
- c for cut and u for uncut.
- AI might assume p stands for pointer and not for preserved.










## u keyword

The u keyword is used to declare a string.
- [String][#string]

u for uncut.

In a u value shape: All characters within the u block are preserved except:
- the line feed character immediately after [ is discarded.
- the line feed character immediately before ] is discarded.



### Declaration

```Volupu
u[some text]
```

Where:
- Escape sequences are not recognized within a u block.
- Volupu syntax is not recognized within a u block.
- Unbalanced brackets must be put in strings literals like e.g. "[" or "]".



### Why the u keyword

Because of mnemonics:
- cut and uncut.
- c and u like see you.










## string keyword

The string keyword creates a String as representation of a function, type, or value.



### Example 1

```Volupu
string(exp)
```

Where:
- exp is a function, type, or value.










## Text keyword

The Text keyword is the type of a Text value.

See also:
- [t keyword](#t-keyword)



### Example 1

```Volupu
Text(string)
```

Where:
- [String](#string)



### Shape

The shape of a Text value is a text field.










## t keyword

A t keyword is candy and used to create a Text value.
- [t keyword](#t-keyword)



### Example 1

```Volupu
t(exp)
```

Is synonymous with:

```Volupu
Text(string(exp))
```

Where:
- Text is the Text keyword.
  - [Text keyword](#text-keyword)
- string is the string keyword.
  - [string keyword](#string-keyword)
- exp is a function, type, or value.










## l keyword

A l keyword is candy and used to create a List value.
- [List type](#list-type)



### Example 1

```Volupu
l(val1, val2, val3)
```

Is synonymous with:

```Volupu
List(type1)(cap: 3).add(val1).add(val2).add(val3)
```

Where:
- type1 is the type derived from the declared elements.
- cap: 3 because 3 elements are declared.



### Example 2

```Volupu
l(Type1)(val1, val2, val3)
```

Is synonymous with:

```Volupu
List(Type1)(cap: 3).add(val1).add(val2).add(val3)
```

Where:
- Type1 is the declared typ argument.
- cap: 3 because 3 elements are declared.










## m keyword

A m keyword is candy and used to create a Map value.



### Example 1

```Volupu
m ((key1, value2) (key3, value4))
```

Is synonymous with:

```Volupu
Map(type1, type2).(cap: 2).put(key1, value2).put(key2, value4)
```

Where:
- type1 is the type derived from the declared keys.
- type2 is the type derived from the declared elements.
- cap: 2 because 2 ke-value pairs are declared.



### Example 2

```Volupu
m (Type1, Type2) ((key3, value4) (key5, value6))
```

Is synonymous with:

```Volupu
Map (Type1, Type2).(cap: 2).put(key3, value4).put(key5, value6)
```

Where:
- Type1 is the declared type argument for the declared keys.
- Type2 is the declared type argument for the declared elements.
- cap: 2 because 2 key-element pairs are declared.










## Col keyword

The Ol keyword is the type of Col values.



### Example 1

```Volupu
Col(val1, val2, val3)
```



## Shape

The shape is a field that arranges members vertically.










## Row keyword

The Row keyword is the type of Col values.



### Example 1

```Volupu
Row(val1, val2, val3)
```



## Shape

The shape is a field that arranges members horizontally.










## Ol keyword

The Ol keyword is the type of Ol values.



### Example 1

```Volupu
Ol(val1, val2, val3)
```



## Shape

The shape is an ordered list like in HTML.











## Ul keyword

The Ul keyword is the type of Ul values.



### Example 1

```Volupu
Ul(val1, val2, val3)
```



## Shape

The shape is an unordered list like in HTML.










## Tab keyword

The Tab keyword is the type of a Tab value.



### Example 1

```Volupu
Tab(
  header: l("a", "b", "c")
  rows: l(
      l(val1, val2, val3),
      l(val1, val2, val3),
  )
)
```

Where:
- [l keyword](#l-keyword)



### Shape

The shape of a Tab value is a row oriented table.










## Coltab keyword

The Coltab keyword is the type of a Coltab value.



### Example 1

```Volupu
Coltab(
  header: l(val1, val2, val3)
  cols: l(
    l(val3, val4, val5)
    l(val3, val4, val5)
  )
)
```

Where:
- [l keyword](#l-keyword)



### Shape

The shape of a Coltab value is a column oriented table.










## Ln keyword

The Ln keyword is used to create a link value.



### Example 1

```Volupu
Ln(label: "label", path: "path")
```

Where:
- The label value stands for the label.
- The path value stands for the path.










## Cit keyword

The Cit keyword is used to create a citation value.



### Example 1

```Volupu
Cit(type: "language", text: u[text])
```

Where:
- The type value indicates the type or language of the following text.
- The text value is the copied or cited text.



### Example 2

```Volupu
Cit (
  source: path,
  type: type,
  text: text,
)
```

Where:
- The source value stands for the path where the original text can be obtained.










## Doc keyword

The Doc keyword is the type of a Doc value.

A Doc value can be related to every function, type, and value.



### Example 1

```Volupu
1.2 Doc u(some documentation)
```

Where:
- The Doc followed by a string indicates a Doc value that is related to the value before the Doc keyword.
  - [String](#string)










## Question operator

? operator = question operator.

The ? operator is a conditional unwrap-and-chain operator for Enum.
- [Enum](#enum)

The ? operator is used to match an enum member name.



### Example 1

```Volupu
value1?caseName2.fun3(...)?caseName4.fun5(...)
```

Where:
- ?caseName2 gives the "caseName2" member of the left Enum if present. If not then the operator gives Opt.none.
- ?caseName4 gives the "caseName4" member of the left Enum if present. If not then the operator gives Opt.none.



### Example 2

```Volupu
value1?.fun2(...)?.fun3(...)
```

Where:
- ? followed by . gives the "some" member of the left Enum if present. If not then the operator gives Opt.none.










## Todo keyword

The Todo keyword is the type of a Todo value.

A Todo value is similar to a Doc value.

Some Volupu writer is supposed to add the expression before the Todo value according to the requirements declared in the string that follows the Todo value.



### Example 1

```Volupu
name = Todo u(some documentation)
```

Some Volupu writer (notably AI) is supposed to an expression before Todo so that the Volupu text looks like this:

```Volupu
name = expression Todo u(some documentation)
```










## rec keyword

The rec keyword is use to define a Record type.
- [Record type](#record-type)










## me keyword

The me keyword can be used in 2 ways:
- As a reference to the me value. In this case: The me keyword is similar to this or self keyword in other languages.
  - [me value](#me-value)
- As reference to the me output.
  - [me output](#me-output)










## me type


The me type is the type of the me value.
- [me value](#me-value)



### Example 1

```volupu
rec Type1 {
  name1: fn (name2: Type3) me {
    return me
  }
}
```

Where:
- The me type is Type1.










## me value

The me value in a member function is the Record:
- through which the member function is accessed.
- that is given as implicit argument to the member function when called.



### Example 1

```volupu
rec Type1 {
  name1: fn (name2: Type3) type(me) {
    ...
  }
  name4: fn (name5: Type6) me {
    ...
    me.name1(arg7)
    return me
  }
}
```










## me output

The me output is the me value given as output of a member function.



### Example 1

```volupu
rec Type1 {
  name1: fn (name2: Type3) me {
    return me
  }
}
```

Where:
- The me output preserves the mut qualifier of the me value.
  - [mut qualifier](#mut-qualifier)
- For the creation of an immutable value, the imCopy operator must be used.
  - [imCopy operator](#imcopy-operator)










## Enum keyword

The Enum keyword is used to create an Enum type.
- [Enum type](#enum-type)










## mark keyword

The mark keyword is used to create an Mark type.
- [Mark type](#mark-type)







## task keyword

The task keyword is used to create a Task type.
- [Type type](#task-type)



### Type definition

```Volupu
task TypeName1(T){
  name2: Type3
  name4: T
  name5: T
  name6: fn (param7: T) T{
    ...
  }
}
```

Where:
- The task keyword indicates the creation of a Task type.
- All Q members are private.










## fn keyword

The fn keyword is use to create a function type or function.



### Example 2

```Volupu
fn name1 (param2: Type3) Type4 {
  ...
}
```

Where:
- A name following the fn keyword indicates the declaration of a function with name.
- Parameter names are part of the type because of calls with named arguments.
- The round block with 0 or more parameter definitions is always required in a function definition or function type definition.
- ... is a place holder for a sequence of function statements.
  - [Function statement](#function-statement)
- Type4 is the type of the output of the function and follows the round block with the parameters. If the function returns nothing then no type is declared after the round block.
- The return keyword must be used to indicate that the function returns a value.



### Example 2

```Volupu
fn (param2: Type3) Type4 {
  ...
}
```

Where:
- A round bracket after the fn keyword indicates either the declaration of a nameless function or the declaration of a function type.
- The round block with 0 or more parameter definitions is always required in a function definition or function type definition.
- ... is a place holder for a sequence of function statements.
  - [Function statement](#function-statement)
- Type4 is the type of the output of the function and follows the round block with the parameters. If the function returns nothing then no type is declared after the round block.
- The return keyword must be used to indicate that the function returns a value.



### Example 3

```Volupu
fn (param2: Type3) Type4
```

Where:
- A round bracket after the fn keyword indicates either the declaration of a nameless function or the declaration of a function type.
- Absence of the curly block indicates the declaration of a function type.
- Type4 after : is the type of the output of the function and follows the round block with the parameters. If the function returns nothing then no type is declared after the round block.










## return keyword

The return keyword is used like in other languages.



### Example 1

```Volupu
return expression
```

Where:
- The return statement is only allowed in a function block, if block, else block, or match block.










## if keyword

The if keyword is used like in other languages.



### Example 1

```Volupu
if exp1 {
  ...
}
```

Where:
- ... is a place holder for a sequence of function statements.










## else if keywords

The else if keywords are used like in other languages and must follow an if block or else if block.



### Example 1

```Volupu
if exp1 {
  ...
} else if exp2 {
  ...
} else if exp3 {
  ...
}
```

Where:
- ... is a place holder for a sequence of function statements.










## else keyword

The else keyword is used like in other languages and must follow an if block or else if block.



### Example 1

```Volupu
if exp1 {
  ...
} else if exp2 {
  ...
} else if exp3 {
  ...
} else {
  ...
}
```

Where:
- ... is a place holder for a sequence of function statements.










## match keyword

The match keyword is used to match Enum cases.

The match statement is similar to Swift and Rust but curly blocks are declared after the case guard.



### Example 1

```Volupu
match status {
  // 1. Match specific value (Deep Match)
  // Only runs if connecting AND retries is exactly 0
  case Status.connecting(retries: 0) { 
    statements
  }
  // 2. Match condition (Guard Clause)
  // Common in Swift/Rust, very good for AI logic
  case Status.connecting(retries) if retries > 5 {
    statements
  }
  // 3. Standard Binding
  // Catches everything else
  case Status.connecting(retries) {
    statements
  }
}
```










## Qualifier

Volupu offers these qualifiers:
- [mut qualifier](#mut-qualifier)
- [private qualifier](#private-qualifier)
- [public qualifier](#public-qualifier)
- [tm qualifier](#tm-qualifier)










## mut qualifier

The mut qualifier is:
- a qualifier for a Record member to indicate that the Record member can be replaced.
- a qualifier for a Record type to enable the mut qualifier for the Record members.

Related:
- [Record type](#record-type)
- [mut type](#mut-type)
- [mut value](#mut-value)



### Example 1

```Volupu
mut rec Name1 {
  private mut name2: T
  mut name3: function4
}
```

Where:
- mut is declared before rec.
- mut is declared after private or public.










## private qualifier

A private qualifier is like private in object oriented languages.



### Declaration

```Volupu
rec Name1 {
  private name2: T
  name3: T
}
```

Where:
- In a Record type:
  - The private qualifier must be declared before the name of a member of a Record type.
  - A Record member without private qualifier is implicitly a public member.
- In a task type:
  - The public qualifier must be declared before the name of a member of a task type.
  - A task member without public qualifier is implicitly a private member.



### Limitations

v1 = value.

- Only member functions of v1 can access to the private members of v1 through v1.










## public qualifier

The public qualifier is like private in object oriented languages.



### Declaration

```Volupu
rec Name1 {
  public name2: T
  public name3: T
}
```

Where:
- In a Record type:
  - The private qualifier must be declared before the name of a member of a Record type.
  - A Record member without private qualifier is implicitly a public member.
- In a task type:
  - The public qualifier must be declared before the name of a member of a task type.
  - A task member without public qualifier is implicitly a private member.



### Limitations

v1 = value.

- Only member functions of v1 can access to the private members of v1 through v1.










## tm qualifier

tm for task mutability and Record mutability.

The tm qualifier is a qualifier for a type.

t1 = task or Record.
m1 = tm member of t1.

The tm qualifier of m1 indicates that only member functions of t1 can mutate tm1.

The tm qualifier implies the mut qualifier so that the mut qualifier is not declared.



### tm type

A tm type is a type with tm qualifier.



### tm value

A tm value is a value with tm type.



### Declaration

```Volupu
mut T
```

Where:
- T is a type.
- A value with mut T type is technically like a value with T type but the value can be mutated in a shallow way which means that direct members can be replaced but members of members can not he replaced.



### Limitations

- Only functions of the task or Record container can mutate the tm member of that task or Record container.
- The tm qualifier is implicitly applied to all direct and indirect members becaus this prevents chaotic mutations and chaotic system design.










## Basic types

- [Bool type](#bool-type)
- [List type](#list-type)
- [Map type](#map-type)
- [Opt type](#opt-type)
- [P type](#p-type)
- [Ptr type](#ptr-type)
- [Type type](#type-type)










## Bool

A Bool is value with Bool type.

Bool is singular and plural term.

A Bool is declared with one of these keywords:
- true
- false










## Bool type

A Bool is the type of Bool.
- [Bool]










## List

A List is a value with List type.
- [List type](#list-type)

Related:
- [l keyword](#l-keyword)



### Example 1

```Volupu
List(Type1)
```

Where:
- Type1 is the type of the elements.
- The capacity is 0.



### Example 2

```Volupu
List(Type1)(cap: 10).addAll(l(val1, val2, val3))
```

Where:
- Type1 is the type of the elements.
- The capacity is 10.
- All elements of l(val1, val2, val3) are added to the List.










## List type

A List type is the type of a List.
- [List](#list)

The List type has 1 type parameter for the type of the elements.









## Map

A Map is a value with Map type.
- [List type](#list-type)

A Map is not sorted.

Related:
- [m keyword](#m-keyword)



### Example 1

```Volupu
Map(Type1, Type2)
```

Where:
- Type1 is the type of the key elements.
- Type2 is the type of the value elements.
- The capacity is 0.




### Example 2

```Volupu
Map(Type1, Type2)(cap: 10).putAll(m ((key1, value2) (key3, value4)))
```

Where:
- Type1 is the type of the key elements.
- Type2 is the type of the value elements.
- The capacity is 10.
- All elements of m ((key1, value2) (key3, value4)) are pit in the Map.










## Map type

A Map type is the type of a Map.
- [Map](#map)

The Map type has 2 type parameters.










## Opt type

The Opt type is the type of Opt values.

A Opt value or Opt is an Enum value.

Related:
- [Question operator](#question-operator)



### Members

```Volupu
Enum Opt(T) {
  case none
  case some(item: T)
}
```










## Ptr type

Ptr for pointer.

A Ptr is the type of Ptr values.

A Ptr value is a pointer to some value whose type is unknown.

A Ptr value is a black box and completely opaque from the outside. 

The Ptr type is useful for a container with diverse items.
- For the container and the user of the container: All items are just Ptr values.
- While items in the container remain type safe and unaffected by any Ptr that points to them.

A Ptr value is like the supertype of all values that are accessed by pointer or reference.



### Type declaration

```Volupu
Ptr
```

Where:
- All members of Ptr are inaccessible from the outside.










## mut type

A mut type is a Record type with mut qualifier.
- [mut qualifier](#mut-qualifier)
- [Record type](#record-type)



### Declaration

```Volupu
mut T
```

Where:
- T is a Record type.
  - [Record type](#record-type)










## mut value

A mut value is a value with mut type.
- [mut type](#mut-type)










## Q

Q for queue.

A Q is a value with a Q type.
- [Q type](#q-type)

The Q type is the type of a Q value or Q.

B is singular and plural term.

A Q is used in the TQ paradigm.
- [TQ paradigm](#tq-paradigm)



## Example 1

```Volupu
Q(popMark, pushMarkT, T)(cap: 10)
Q(popMark, pushMark, T)(e: List()(v1, v2, v3))
```

Where:
- Q is a type 3 type parameters.
  - [Q type](#q-type)
- The cap member stores the initial capacity.
- The e field is a list with initial elements.
  - If the cap field is not set, then the initial cap value corresponds to the number of initial elements.



### Q push function

Every Q has a push function that can be called by any function except when the Q has the tm qualifier.
- [tm qualifier](#tm-qualifier)

The function allows to push elements to the Q.

All non-Q elements must be immutable.



### Q pop function

Every Q has a pop function that can be called by any function except when the Q has the tm qualifier.
- [tm qualifier](#tm-qualifier)



### Q peek function

Every Q has a peek function that can be called by any function.



### Q setCap function

Every Q has a setCap function that can be called by any function except when the Q has the tm qualifier.
- [tm qualifier](#tm-qualifier)

The setCap function allows to determine the maximal capacity of the Q.



### Q getCap function

Every Q has a getCap function that can be called by any function.



### Q getPopMark function

Every Q has a getPopMark function that can be called by any function.
- [QPopMark type](#qpopmark-type)



### Q getPushMark function

Every Q has a getPushMark function that can be called by any function.
- [QPushMark type](#qpushmark-type)



### Limitations

- All operations with Q value are synchronized for thread safety. The Q value can be mutable with the tm or mut qualifier.
- The non-Q elements of a Q value must be immutable. This prevents chaos and guarantees good system design.










### Q type

A Q type is the type of a Q.
- [Q](#q)



## Example

```Volupu
Q(popMark, pushMark, T)
```

Where:
- Q is the Q type with 3 type parameters.
- The first argument is a PopMark.
  - [QPopMark type](#qpopmark-type)
- The second argument is a PushMark.
  - [QPushMark](#qpushmark-type)
- T is the type of the elements of the Q.










## QPopMark type

The QPopMark is a mark type.
- [Mark type](#mark-type)

The QPopMark type is defined like this:

```volupu
mark QPopMark {
  first
  last
}
```

Where:
- first means FIFO pop.
- last means LIFO pop.










## QPushMark type

The QPushMark type is mark type.
- [Mark type](#mark-type)

The QPushMark type is defined like this:

```volupu
mark QPushMark {
  keep
  first
  last
}
```

Where:
- keep means to keep all elements and block any push of a new element.
- first means to replace the element that was pushed before all other elements.
- last means to replace the last element.










## Task type

The Task type is the type of a Task value or Task.



### Definition

A Task type is defined with the task keyword.
- [task keyword](#task-keyword)



### task do function

A Task type has always and implicitly a do function with this type:

```volupu
fn (vos: VolupuOs)
```

Where:
- The do function can be private or with public qualifier.
- The do function receives the representation of the Volupu OS as argument from the Volupu OS.
- The do function is called without argument. The call indicates that the Volupu OS should execute the do function with the Volupu OS input at some time in the future.
- The do function gives no output. The caller function does not wait until the do function is computed. The call is a fire and forget operation. Thus guarantees absence of deadlocks.



### Limitations

- Tasks can communicate only through Q and calling the task.do() function. This guarantees thread safety.
  - [Q type](#Q-type)
  - [task do function](#task-do-function)
- All members of a task have implicitly the private qualifier. The public qualifier must be explicitly declared.
  - [private qualifier](#private-qualifier)
  - [public qualifier](#public-qualifier)
- Only one process can compute the task.do function at a time. This prevents chaos. 










## Type type

The Type type is the type of a Type value.

The details of Type members remain to be determined.



### Type value creation

```Volupu
Type(expression)
```

Where:
- expression is some expression.
- The output is a value with Type type.










## Candy

Candy stands for special syntax (syntactic sugar).
- [Enum candy](#enum-candy)
- [l keyword](#l-keyword)
- [m keyword](#m-keyword)
- [t keyword](#t-keyword)










## Editor function

An editor function is related to a change in Volupu text made by the Volupu editor.










