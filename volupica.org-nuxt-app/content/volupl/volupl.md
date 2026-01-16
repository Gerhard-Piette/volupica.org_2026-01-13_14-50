# Volupl










## Introduction

Volupl stands for Volupism language.

Volupl is a programming language that offers:
  - Static type system with type parameters and erased generics.
  - Transpiler written in Rust by AI. The transpiler is available in the browser as WASM module.
  - Translation of Volupl programs to:
    - nuxt.js for websites for search engines.
    - SwiftUI on Apple operating systems.
    - GUI on Google operating systems.
  - Declaration of content in Volupl text. Volupl should be a replacement for HTML, markdown, js frameworks, and Microsoft office products for content creators.
  - Assumption of garbage collection.
  - Reactivity with the App paradigm.
  - Functions are without side effects but there is the App paradigm that allows mutable state that is shared among parallel threads.
  - Functions in tuple and enum values are dynamically dispatched.
  - Higher order functions are dynamically dispatched.
  - Type information determined at compile-time with the type type.
  - No object orientation. But values can have member functions.
  - No function overloading.
  - No type extension.
  - No interface type. Instead use functions that create a new value and dynamically dispatched functions.
  - No trait type. Instead use functions that create a new value and dynamically dispatched functions.

Volupl is meant to be read and written by:
- Humans who are willing to learn Volupl.
- General AI (that is not trained on Volupl) should be able to learn Volupl from the Volupl spec in context.

In January 2026: Volupl was designed to be optimal for general AI like ChatGPT, Claude, and Gemini to write, read, and debug Volupl text and Native apps.










## Volupl OS

The Volupl OS is the operating system or platform for the creation and execution of Native app.
- [Native app](#native-app)

General AI must be able to translate any Volupl text to the following OS:
- HTML + nuxt.js + other libraries. The website must have optimal semantic meaning for search engine optimization.
- Apple OS + SwiftUI.
- Google OS + native UI framework.










## Native app

A native app is an app in the Volupl OS that was created as translation of an app.
- [App](#app)










### Allowed characters in Volupl text

To support "all valid text including emojis" while maintaining security, here is the complete **Allowlist** for Volupl.



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
3.  **Is it one of the 6 specific exceptions (Space, Tab, LF, CR, ZWJ, Volupl16)?** -> **✅ Pass.**
4.  **Everything else?** -> **⛔ Reject.**

**Any other character is forbidden.**











## Block

A block is a term related to Volupl syntax.

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

Volupl offers these bracket blocks:
- [Curly block](#curly-block)
- [Flat block](#flat-block)
- [Round block](#round-block)










## Curly block

A curly block is delimited by "{" and "}" as curly brackets.

A curly block contains a sequence of 0 or more statements where the linefeed codepoint is the required separator.

A curly block that follows a point indicates replacement of members of the preceding tuple or enum value.
- [f member](#f-member)









## Flat block

A flat block is delimited by "[" and "]" as flat brackets.

A flat block is used for c and u values.
- [c keyword](#c-keyword)
- [u keyword](#u-keyword)










## Round block

A round block is delimited by "(" and ")" as round brackets.

A round block is used for a sequence of 0 or more parameters or values where the comma codepoint is the required separator.

A round block that follows a point indicates replacement of members of the preceding tuple or enum value.
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
- Tuple type definition
  - [tp keyword](#tp-keyword)
- Enum type definition
  - [enum keyword](#enum-keyword)










## Function statement

A function statement is declared:
- in the curly block of a function.
- in the curly block after the if keyword.
- in the curly block after the if else keywords.
- in the curly block after the else keyword.
- in the curly block after the enum match guard.

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

An expression is a sequence of tokens in Volupl text.

An expression can be:
- [Name](#name)
- [Name path](#name-path)
- [Number](#number)
- [Value](#value)
- [Function](#function)
- [Function call](#function-call)
- [Operator usage](#operator-usage)
- [Variable definition](#variable-definition)
- [Tuple copy](#tuple-copy)










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

```volupl
List(Int)(1, 2, 3)
List()(1, 2, 3)
List(1, 2, 3)
```

Where:
- The three lines are valid declarations of List values. The List type has 1 type parameter.










## Name

A name is an identifier in other languages.

A name must not be a keyword in the Volupl version that is used.
- [volupl](#volupl-keyword)



### Rust regex of a valid Volupl name

```rust
r"^(r#)?(\p{XID_Start}|_)\p{XID_Continue}*$"
```

A valid name can still be invalid because the name equals a key keyword.

Different Volupl versions can have different keywords.



### Recommended naming convention

- PascalCase for type names in European letters.
- camelCase for all other names in European letters.










## Name path

A name path is like a qualified name in a programming language.



### Example

```volupl
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

There are 3 ways to declare a string Volupl:
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

```volupl
"some string"
```

Where:
- Inline strings must begin and end on the same line.
- Only allowed characters are allowed in string content.
- Escape sequences are recognized in an inline string.



### Escape sequences

The compiler recognizes escape sequences only in string content.

The only valid escape sequences in Volupl:
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

Volupl offers operators like in other languages.
- [Math operator](#math-operator)
- [Bool operator](#bool-operator)

The technical implementation depends on the Volupl transpiler and the Volupl OS.










## Operator usage

The syntax of operator usage depends on the operator.










## Operator precedence

Operators have lower precedence than functions and thus can use the output of function calls as arguments.

All operators have the same precedence: Left before right.

A different precedence must be declared with round blocks. 










## Math operator

Volupl offers math operators like other languages:
- +
- -
- *
- /










## Bool operator

Volupl offers bool operators like other languages:
- and
- or
- xor
- not



### Example 1

```volupl
b1 and b2 and b3
```

Where:
- b1, b2, and b3 are bools.



### Example 2

```volupl
b1 or b2 or b3
```

Where:
- b1, b2, and b3 are bools.



### Example 2

```volupl
b1 xor b2 xor b3
```

Where:
- b1, b2, and b3 are bools.



### Example 2

```volupl
not b1
```

Where:
- b1 is a bool.










## Function

A function is like a function in other languages.

A function is defined with the fn keyword.
- [fn keyword](#fn-keyword)

Volupl does not offer function overloading because function overloading introduces many difficulties. Instead Volupl offers implicit create of enum values.
- [Enum](#enum)

Functions are without side effects but there is the App paradigm for mutable data.
- [App paradigm](#app-paradigm)

Functions in file blocks are statically dispatched.
- [File block](#file-block)

Functions in values AKA member functions are dynamically dispatched.
- [Tuple](#tuple)
- [Enum](#enum)

Higher order functions are dynamically dispatched.










## Member function

A member function is a function that is accessed from a tuple value or enum case value.
- [Tuple](#tuple)
- [Enum](#enum)

The technical implementation depends on the transpiler and the Volupl OS.










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

Volupl does not offer function overloading.

If a function definition or function type definition contains 2 round blocks then the first round block is always the block with type parameters.

The round block with 0 or more parameter definitions is always required in a function definition or function type definition.



### Example 1

```volupl
fn name1 (T2, T3) (param4: T2) T3 {
  ...
}
```

Where:
- If 2 round blocks follow the fn keyword or the function name, then the first round block contains a sequence of 1 or more type parameters.
- ... is a place holder for a sequence of function statements.
  - [Function statement](#function-statement)



### Example 2

```volupl
fn (T2, T3) (param4: List(Int32), param5: List(T2)) T3
```

Where:
- If 2 round blocks follow the fn keyword or the function name, then the first round block contains a sequence of 1 or more type parameters.
- param4 can be bound to a value with List(Int32) as type.
- param5 can be bound to a value with List(T2) type where T2 can be any type. The function can use items of param5 only with functions that can also use items with type T. The implementation depends on the transpiler and the Volupl OS.










## Function call

A function call is like in other languages.

A function call is done with named arguments.

Named arguments mist be declared after positional arguments.



### Example 1

```volupl
functionName()
```



### Example 2

```volupl
functionName(arg1, arg2)
```



### Example 3

```volupl
functionName(param1: arg2, param3: arg4)
```



### Example 4

```volupl
functionName(arg1, arg2, param3: arg4)
```

Where:
- arg1 and arg2 are positional arguments.
- Named arguments must be declared after positional arguments.



### Example 5

```volupl
functionName(Type1, T2: Type3)(arg4, arg5, param6: arg7)
```

Where:
- If 2 round blocks follow the function name then the first round block contains arguments for the type parameters. Named arguments can be sed for type parameters too. In this example: T2 is the name of the type parameter as declared in the function type.



### Example 6

```volupl
tuple1.function2(Type2, Type3)(arg4, arg5, param6: arg7)
```

Where:
- tuple1 is a tuple value that contains the member function.
- function2 is a member function in tuple1.
- tuple1 is the first argument given to function2. Like in object oriented languages. 



### Example 7

```volupl
match enum1 {
  case case2(function3) {
    function3(Type4)(arg5, param6: arg7)
  }
}
```

Where:
- enum1 is an enum.
- case2 is an enum case.
- function3 is a member function in case2 of enum1.
- arg5 is the first argument given to function3.










## Tuple

A tuple in Volupl is like a struct or record in other languages.

A tuple can have member functions.
- [Member function](#member-function)

A tuple type is defined with the tp keyword.
- [tp keyword](#tp-keyword)

A tuple value is created with a tuple type.
- [Tuple value creation](#tuple-value-creation)










## Tuple value creation

A tuple value is created with the tuple type followed by a round block.

The tuple type is used like a function to create a tuple value.
- [Function call](#function-call)

A new tuple can also be created as tuple copy.
- [Tuple copy](#tuple-copy)



### Example 1

```volupl
TupleType(arg1, arg2, param3: arg4)
```

Where:
- The tuple type name is used like the function name.
- The field names are used like parameter names.



### Example 2

```volupl
TupleType(Type1, T2: Type3)(arg1, arg2, param3: arg4)
```

Where:
- If 2 round blocks follow the type name then the first round block contains arguments for the type parameters. Named arguments can be sed for type parameters too. In this example: T2 is the name of the type parameter as declared in the tupleType.










## Tuple copy

A tuple copy is a shallow copy of an existing tuple.



### Example 1

```volupl
tuple1.{}
tuple1.()
```
Where:
- tuple1 is a tuple value.
- tuple1.{} creates a shallow copy of tuple1.
- tuple1.() creates a shallow copy of tuple1.



### Example 2

```volupl
tuple1.{
  f.{
    width: "50%em"
    height: "10em"
  }
}
```

Where:
- tuple1 is a tuple value.
- tuple1.f is a tuple value.
- tuple1.{} indicates replacement of members in the copy of tuple1. Linefeed is the separator in curly blocks.
- f.{} indicates replacement of members in the copy of f. Linefeed is the separator in curly blocks.
- The output of this expression is a copy of tuple1.




### Example 2

```volupl
tuple1.{
  f.(width: "50%em", height: "10em")
}
```

Where:
- tuple1 is a tuple value.
- tuple1.f is a tuple value.
- tuple1.{} indicates replacement of members in the copy of tuple1. Linefeed is the separator in curly blocks.
- f.() indicates replacement of members in the copy of f. Comma is the separator in round blocks.
- The output of this expression is a copy of tuple1.










## Enum

An enum is like an enum in other languages.

An enum case is an enum member. The member name follows the case name.

An enum can have member functions as part of an enum case.
- [Member function](#member-function)

An enum type is defined with the enum keyword.
- [enum keyword](#enum-keyword)










## Enum value creation

An enum value is created with the enum type followed by a round block.

The enum type is used like a function to create an enum value.
- [Function call](#function-call)



### Example 1

```volupl
EnumType.memberName(arg1, arg2, param3: arg4)
```

Where:
- The case name is used like the function name.
- The field names are used like parameter names.



### Example 2

```volupl
EnumType.caseName(Type1, T2: Type3)(arg1, arg2, param3: arg4)
```

Where:
- If 2 round blocks follow the case name then the first round block contains arguments for the type parameters. Named arguments can be sed for type parameters too. In this example: T2 is the name of the type parameter as declared in the tupleType.



### Example 3

```volupl
fun1(case name2(exp3), param5: case name6(exp7, exp8))
```

Where:
- fun1 is a function that takes 2 enum values as parameters.
- The case name2 indicates the case name2 of the first enum.
- The case name6 indicates the case name6 of the second enum.



### Example 4

```volupl
Text(t: case comp(string + state))
Text(t: string + state)
```

Where:
- Text is a type with a t field that binds a value with Bind type that is an enum type.
  - [Bind keyword](#bind-keyword)
- string + state is implicitly replaced with Memo(string + state).
  - [State keyword](#state-keyword)
  - [Memo keyword](#memo-keyword)
- If the transpiler can determine the case of the enum based on the type of the given argument then there is no need to write case caseName before the argument.










## Variable definition

A variable definition is like in other languages.

A variable definition is a file statement and a function statement. 



### Example 1

```volupl
name1 = exp3
```

Where:
- name1 is the variable.
- exp3 indicates the item that is bound to name1 variable.

The variable type is not declared explicitly because:
- The decreases efforts to read and write Volupl text for humans and AI.
- The decreases the length of Volupl text and thus required tokens in AI context.
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

The f member is a tuple value.

The f value is like the style attribute in HTML.

The values in the f value must be easily portable to all Volupl OS.
- [Volupl OS](#volupl-os)



### Example 1

```volupl
value1.{
  f.{
    width: "50%em"
    height: "10em"
  }
}
```

Where:
- The expression is a tuple copy.
  - [Tuple copy](#tuple-copy)



### Example 2

```volupl
value1.{
  f.(width: "50%em", height: "10em")
}
```

Where:
- The expression is a tuple copy.
  - [Tuple copy](#tuple-copy)



### Why f as member name

- f for form (or format).
- f is easy to write and pronounce.
- No shape member because this would cause confusion about what is meant by shape: Concept or member.
- No style member because style is more effort to write and pronounce.
- No s member because:
  - s might be useful for another keyword.
  - s might be more difficult to pronounce than f.










## Reactivity

Volupl does not offer reactivity like popular GUI in 2026.

Volupl offers the App paradigm where Apps are used as event handlers.
- [App paradigm](#app-paradigm)










## Event handling.

Event handling is done with Apps.
- [App paradigm](#app-paradigm)










## Multithreading

Multithreading is done with Apps.
- [App paradigm](#app-paradigm)










## App paradigm

The App paradigm comprises:
- [App](#app)
- [Api](#api)










## Keywords

- [c keyword](#c-keyword)
- [Cit keyword](#cit-keyword)
- [Col keyword](#col-keyword)
- [Coltab keyword](#coltab-keyword)
- [Doc keyword](#doc-keyword)
- [enum keyword](#enum-keyword)
- [fn keyword](#fn-keyword)
- [import keyword](#import-keyword)
- [L keyword](#l-keyword)
- [List keyword](#list-keyword)
- [Ln keyword](#ln-keyword)
- [Ol keyword](#ol-keyword)
- [Row keyword](#row-keyword)
- [State keyword](#state-keyword)
- [string keyword](#string-keyword)
- [Tab keyword](#tab-keyword)
- [Text keyword](#text-keyword)
- [Todo keyword](#todo-keyword)
- [tp keyword](#tp-keyword)
- [Type keyword](#type-keyword)
- [U keyword](#u-keyword)
- [Ul keyword](#ul-keyword)
- [volupl keyword](#volupl-keyword)










## volupl keyword

The volupl keyword is followed by the version number of Volupl that is used in the current file.

The volupl keyword:
- must be declared before any other statement and expression.
- can be declared only once in a file. A different file can contain text in a different Volupl version.

The Volupl version is important in order to determine:
- What is a keyword.
- How to translate expressions.



### Example

```volupl
volupl(1)
```

Where:
- volupl is the volupl keyword.
- (1) indicates the version 1 declared as round block.










## import keyword

The import keyword is used to refer to a Volupl file as file block.
- [File block](#file-block)

An import is Volupl text that is located:
- either by a file path.
- or by a URI.



### Example of import

```volupl
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

```volupl
c[some text]
```

Where:
- Escape sequences are not recognized within a c block.
- Volupl syntax is not recognized within a c block.
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

```volupl
u[some text]
```

Where:
- Escape sequences are not recognized within a u block.
- Volupl syntax is not recognized within a u block.
- Unbalanced brackets must be put in strings literals like e.g. "[" or "]".



### Why the u keyword

Because of mnemonics:
- cut and uncut.
- c and u like see you.










## string keyword

The string keyword creates a String as representation of a function, type, or value.



### Example 1

```volupl
string(exp)
```

Where:
- exp is a function, type, or value.










## Text keyword

The Text keyword is the type of a Text value.

See also:
- [t keyword](#t-keyword)



### Example 1

```volupl
Text(string)
```

Where:
- [String](#string)



### Shape

The shape of a Text value is a text field.










## t keyword

A t keyword is candy and used to create a Text value.
- [Candy](#candy)



### Example 1

```volupl
t(exp)
```

Is synonymous with:

```volupl
Text(string(exp))
```

Where:
- Text is the Text keyword.
  - [Text keyword](#text-keyword)
- string is the string keyword.
  - [string keyword](#string-keyword)
- exp is a function, type, or value.










## List keyword

A List keyword is the List type.

See also:
- [l keyword](#l-keyword)



### Example 1

```volupl
List(type1)
```

Where:
- List(type1) is the List type where type1 is a type argument and the type of the items.



### Example 1

```volupl
List(type1)(val1, val2, val3)
```

Where:
- This is the declaration of a List value where all items must have type type1.










## l keyword

A l keyword is candy and used to create a List value.
- [Candy](#candy)



### Example 1

```volupl
l(val1, val2, val3)
```

Is synonymous with:

```volupl
List(type1)(val1, val2, val3)
```

Where:
- type1 is the type derived from the declared items.










## Col keyword

The Ol keyword is the type of Col values.



### Example 1

```volupl
Col(val1, val2, val3)
```



## Shape

The shape is a field that arranges members vertically.










## Row keyword

The Row keyword is the type of Col values.



### Example 1

```volupl
Row(val1, val2, val3)
```



## Shape

The shape is a field that arranges members horizontally.










## Ol keyword

The Ol keyword is the type of Ol values.



### Example 1

```volupl
Ol(val1, val2, val3)
```



## Shape

The shape is an ordered list like in HTML.











## Ul keyword

The Ul keyword is the type of Ul values.



### Example 1

```volupl
Ul(val1, val2, val3)
```



## Shape

The shape is an unordered list like in HTML.










## Tab keyword

The Tab keyword is the type of a Tab value.



### Example 1

```volupl
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

```volupl
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

```volupl
Ln(label: "label", path: "path")
```

Where:
- The label value stands for the label.
- The path value stands for the path.










## Cit keyword

The Cit keyword is used to create a citation value.



### Example 1

```volupl
Cit(type: "language", text: u[text])
```

Where:
- The type value indicates the type or language of the following text.
- The text value is the copied or cited text.



### Example 2

```volupl
Cit (
  source: path,
  type: type,
  text: text,
)
```

Where:
- The source value stands for the path where the original text can be obtained.










## Type keyword

The Type keyword is the type of a Type value.

The Type keyword can be used in 2 ways:
- As type of a Type value.
- Like a function that returns a Type value that represents the type of argument.

The details of the Type value remains to be determined.



### Example 1

```volupl
Type(expression)
```

Where:
- expression is some expression.
- The output is a value with Type type.










## Doc keyword

The Doc keyword is the type of a Doc value.

A Doc value can be related to every function, type, and value.



### Example 1

```volupl
1.2 Doc u(some documentation)
```

Where:
- The Doc followed by a string indicates a Doc value that is related to the value before the Doc keyword.
  - [String](#string)










## Todo keyword

The Todo keyword is the type of a Todo value.

A Todo value is similar to a Doc value.

Some Volupl writer is supposed to add the expression before the Todo value according to the requirements declared in the string that follows the Todo value.



### Example 1

```volupl
name = Todo u(some documentation)
```

Some Volupl writer (notably AI) is supposed to an expression before Todo so that the Volupl text looks like this:

```volupl
name = expression Todo u(some documentation)
```










## tp keyword

The tp keyword is use to create a type type.

A tp type or tp value can not contain functions.



### Example 1

```volupl
tp Type1 {
  field2: Type3 = value4
  field5: Type6 = value7
}
```


### Example 2

```volupl
tp Type1 (T2, T3) {
  field4: T2
  field5: T3
  field6: T3
}
```

Where:
- If 1 round block follows the type name then the round block contains a sequence of 1 or more type parameters.










## enum keyword

The enum keyword is used to create an enum type.

An enum type or enum value can not contain functions.



### Example 1

```volupl
enum ServerResponse {
    case success
    case error(code: Int32, message: String)
    case loading(time: Float32)
}
```



### Example 2

```volupl
enum ServerResponse(T1) {
    case success()
    case error(code: Int32, message: T1)
    case loading(time: Float32)
}
```

Where:
- If 1 round block follows the type name then the round block contains a sequence of 1 or more type parameters.










## fn keyword

The fn keyword is use to create a function type or function.



### Example 2

```volupl
fn name1 (param2: Type3) Type4 {
  ...
}
```

Where:
- A name following the fn keyword indicates the declaration of a function with name.
- The round block with 0 or more parameter definitions is always required in a function definition or function type definition.
- ... is a place holder for a sequence of function statements.
  - [Function statement](#function-statement)
- Type4 is the type of the output of the function and follows the round block with the parameters. If the function returns nothing then no type is declared after the round block.
- The return keyword must be used to indicate that the function returns a value.



### Example 2

```volupl
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

```volupl
fn (param2: Type3) Type4
```

Where:
- A round bracket after the fn keyword indicates either the declaration of a nameless function or the declaration of a function type.
- Absence of the curly block indicates the declaration of a function type.
- Type4 after : is the type of the output of the function and follows the round block with the parameters. If the function returns nothing then no type is declared after the round block.










## return keyword

The return keyword is used like in other languages.



### Example 1

```volupl
return expression
```

Where:
- The return statement is only allowed in a function block, if block, else block, or match block.










## if keyword

The if keyword is used like in other languages.



### Example 1

```volupl
if exp1 {
  ...
}
```

Where:
- ... is a place holder for a sequence of function statements.










## else if keywords

The else if keywords are used like in other languages and must follow an if block or else if block.



### Example 1

```volupl
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

```volupl
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

The match keyword is used to match enum cases.

The match statement is similar to Swift and Rust but curly blocks are declared after the case guard.



### Example 1

```volupl
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










## Basic types

- [App](#app)
- [Api](#api)
- [Bool](#bool)
- [Mut](#mut)
- [Opt](#opt)
- [Ptr](#ptr)










## Bool

A Bool is the type of Bool values.

A Bool value or a Bool is declared with one of these keywords:
- true
- false










## Mut

The Mut type is the type of Mut values.

A Mut value is a logical type that marks an existing value as mutable.

The creation of a Mut value does not imply allocation of memory.










## Opt

The Opt type is the type of Opt values.

A Opt value or Opt is an enum value.



### Members

```volupl
enum Opt(T) {
  case none
  case some(item: T)
}
```










## ApiOpt

The ApiOpt type is the type of ApiOpt values.

A ApiOpt value or ApiOpt is an enum value.



### Members

```volupl
enum ApiOpt(T) {
  case timeout(api: api)
  case opt(item: Opt(T))
}
```

Where:
- The timeout member is used when the lock of an Api was removed the Volupl OS.










## Ptr

A Ptr is the type of Ptr values.

A Ptr value is a pointer to some value whose type is unknown.

The Ptr type is useful for a container with diverse items.
- For the container and the user of the container: All items are just Ptr values.
- While items in the container remain type safe and unaffected by any Ptr that points to them.










## App

The App type is used to create a App value.

An App value or App is like a tuple value.

An App can communicate with other Apps only through Api values.
- [Api type](#api-type)



### Members

The App type is similar a tp type defined like so:

```volupl
tp App(S1, S2) {
  state: S1
  apply: fn(api: Api(S2))
  bind: fn(api: Api(S2))
  unbind: fn(api: Api(S2))
}
```

Where:
- state is the state of the App.
- apply is a function that processes the app.state. The api parameter is the bound Api value that triggered the computation of the app.apply function.
- The app.state member is only accessible to the app.apply function of the same app.



### Computation of the apply function

The apply function of the same App is never computed at the same time by different threads.

The apply functions of different Apps can be computed at the same time by different threads.

There are 2 ways to trigger the computation of an app.apply function:
- When a function calls the app.apply function then a request to compute the apply function is registered in the Volupl OS. The Volupl OS will compute the app.apply function at some time in the future. The caller continues immediately and does not wait until the app.apply function has been computed. This prevents deadlocks.
- The Volupl OS computes the app.apply(api) function after the bound api value has changed because of the api.set(state) function.



### Binding an App to an Api

```volupl
app.bind(api)
```

The bind operator binds an App value as handler to an Api value. 



### Unbinding an App from an Api

```volupl
app.unbind(api)
```

This removes the binding of the App value from the Api value.










## Api

Api is pronounced as single world that rhymes with happy.

The Api type is used to create a Api value or Api.

An Api value or Api is like a tuple value.

An Api is used for exchange of values between apps.



### Members

The Api type is similar a tp type defined like so:

```volupl
tp Api(S) {
  set: fn(state: Mut(S)) ApiOpt(S)
  get: fn() ApiOpt(S)
  change: fn(setter: fn(state: Opt(Mut(S)))) ApiOpt(Bool)
  setLockDuration: fn(duration: Duration) ApiOpt(Bool)
  getLockDuration: fn() ApiOpt(Duration)
}
```

Where:
- The Api stores a value with type S as state of the Api.
- An Api is locked for the duration of the computation of an Api member function. At most one process can compute an Api member function at a time. The Volupl OS pauses all waiting threads for less than the lock duration of the Api. The Volupl OS scheduling does not guarantee any precision regarding the actual lock duration.
- The set function:
  - sets the given state as Api state.
  - returns the previous Api state.
- The get function returns the Api state. The returned value is immutable. All values stored in an Api are tracked by a garbage collector and any value remains until the GC removes it.
- The change function calls the setter function that receives the Api state in order to change it. The setter function allows to replace only some members of the Api state.










## Change

The Change type is used to create a Change value or Change.

A Change is like a tuple value.



### Members

The Change type is similar a tp type defined like so:

```volupl
tp Change(T1) {
  target: T1
  focus: Focus(T1)
}
```

Where:
- The set function replaces the state of the Api.
  - The set function replaces the Api state only if the given App is the writer App.
  - If no writer app is set then the set function sets the received App as writer App.
  - The output is true if the state was replaced.
- The get function replaces the state of the Api. The value is immutable. In Volupl: All values stored in a Api are tracked by a garbage collector and thus remains accessible after then value of the Api was replaced.
- The setWriter function sets the writer App. The output is the previous writer App.
- The getWriter function gives the current writer App.
- Opt(App) is the Opt enum type.
  - [Opt type](#opt-type)








## Candy

Candy stands for special syntax (syntactic sugar).
- [l keyword](#l-keyword)
- [t keyword](#t-keyword)










## Editor function

An editor function is related to a change in Volupl text made by the Volupl editor.










