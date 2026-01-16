# Volupl history










## 2026 01 18 - 14 11

### Removed
- Reactivity as intended this morning.

### New
- App paradigm with App and Api keyword.
  - App for tuple that is used as App.
  - Api for tuple that is used as buffer for interaction between Apps.
- Event handling with Apps.
- Opt type.
- Mut type.
- ApiOpt type.










## 2026 01 18 - 10 57

### Removed
- Reactivity system.
  - Bind
  - Cmd. Replaced with Change.
  - Memo. Replaced with FnFlow.
  - State. Replaced with AtomFlow and MapFlow.
- Keywords. Replaced with operators and basic types.

### Added
- Reactivity system. Without help from AI. But yesterday, Gemini Pro mentioned ideas that lead to my ideas this morning.
  - AtomFlow. With set function.
  - FnFlow. With function.
  - MapFlow. Contains a map. With put and remove function.
  - AtomChange. Stores a value and the function that changes the value.
  - FnChange. Stores the old and new output value of a function.
  - MapChange. Stores the map and a function that changes the map.
  - MultiChange. Stores a list of changes for processing of multiple changes as single transaction.
- Ptr type. As Pointer to anything. I had the idea while thinking about what Flow and Change type I need. 
- Function call chain.










## 2026 01 17 - 21 41

### Planned
- Improvements to the reactivity system according to Gemini 3.0 Pro:
  - https://gemini.google.com/app/017776019b1713db
  - Lenses like in Swift according to Gemini 3.0 Pro.
  - Collection operations and use of sorted maps instead of lists. Like databases.
  - Cmd transactions that can comprise multiple operations in one transaction.










## 2026 01 17 - 19 09

### Replaced
- Sig keyword => State
- Comp keyword => Memo
- Mut keyword => Cmd
- Src keyword => Bind










## 2026 01 17 - 09 19

### Added
- Member function
- Operator
- Tuple copy
- Text keyword
- t keyword
- string keyword
- Reactivity
  - According to Gemini 3: https://gemini.google.com/app/ce0a29061faadb50
- Closure
- Sig keyword
- Comp keyword
- Mut keyword
- Src keyword
- ...


### Replaced
- L => l










## 2026 01 16 - 11 59

### Changed
- [] only for strings. had the idea on 2026 01 13 but I tried to keep it more conservative as list.
- () for blocks where comma is separator.
- {} for blocks where linefeed is separator.

### Removed
- Curly value
- Flat value
- Round value
- File value
- Definition
- Replacement
- f keyword
- Editor functions

### Added
- tp for tuple AKA struct AKA record type.
- enum for enum type.
- fn for function definition.
- c[] fur cut string.
- u[] fur uncut string.
- Inline strings. As name for a string declared with quotation marks.
- Doc keyword
- Type keyword
- Todo keyword










## 2026 01 13 - 14 58

### Basics

Based on github:
- volupl.org_2026-01-08_14-45.
- voluptum.org_2025-12-23_14-04

https://gemini.google.com/app/65356c5e9e7f0139
  - Gemini 3.0 Fast proposed use of shape (type in Volupl) and components (types related to shape in Volupl).

### Added
- Type definitions. Some types have associated a shape.
- ai keyword for type for communication with AI.
- tp keyword for tuple (AKA record, struct) type definition.
  - tuple for easy and similar pronunciation in several languages.
- enum for enum type definition.
- fn keyword for function record type.
  - Functions are functional.
  - Functions are statically dispatched and fully known by all readers including AI. 
  - Functions are used to create a new value from existing values. Notably for creation of value with shape based on the data of 1 or more other values. Gemini 3.0 Fast proposed binding between record and component (= GUI). I think a function is even better than binding.
  - Functions comprise if-else or when logic.
  - Function calls are with round blocks because humans and AI are trained for that.
- Type parameters are with round blocks for named arguments.
  - List (Type) [val2 val3]
  - Map (Type1, Type2) [ [val3 val4] [val5 val6] ]
  - Type1 (t2 = Type3, t4 = Type4) { name4 = val5 name6 = val7}
- No concept of trait or interface because it is replaced with functions that create new values.

### Changed
- : only used for typing and not for replacement.
  - Example type definition: tp { name1: Type2 = value3}
  - There is no concept of addition of items because items are determined by the type of the value.
- {} for blocks of type definitions, blocks of value declarations, and blocks of functions because humans and AI are trained for that.
- () for function parameters and type parameters because humans and AI for trained for that.
  - add(1, 2)
  - sin(angle)
  - print(value1)
  - (a, b, c = 4) means (a = a b = b c = 4)
- [] for list of values
- s[] for string with indentation and code completion when other blocks are used.
- p[] for with with preserved whitespace.










