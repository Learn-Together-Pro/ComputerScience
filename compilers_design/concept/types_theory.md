# Key concepts of Parsing Theory

Cheatsheets for Parsing Theory.

<!-- [:arrow_down: Tags legend](#tags-legend) at the end of the page. -->

<!-- - []() by []() ( _:movie_camera:_ ) -->

## **Type Analysis** > Type Checking / Type Inference

Processes that ensure type correctness and deduce missing type information in programming.

**Type Checking** verifies adherence to type rules, catching errors at compile time, while **Type Inference** deduces missing type information, reducing the need for explicit type annotations.

## **Typing Strength** > Strongly Typed Languages / Weakly Typed Languages

The strictness of type enforcement in programming languages affects error detection and conversion behavior.

**Strongly Typed Languages** enforce strict type rules, preventing implicit conversions and catching errors early, whereas **Weakly Typed Languages** allow implicit conversions, which can lead to unexpected behaviors.

## **Typing Explicitness** ~ **Level of Inference** > Implicit Typing / Explicit Typing

The level of type inference required in programming languages determines the explicitness of type declarations.

**Implicit Typing** relies on type inference to deduce types without explicit declarations, while **Explicit Typing** requires programmers to declare types explicitly, reducing reliance on inference.

## **Typing Timing** > Dynamic Language / Static Typed Language

The timing of type checking in programming languages influences flexibility and error detection.

**Dynamic Languages** perform type checking at runtime, offering flexibility but potentially leading to runtime errors, whereas **Static Typed Languages** perform type checking at compile time, ensuring type safety before execution.

## Symbol Table

A data structure used by compilers to store information about identifiers and scope.

Symbol tables are crucial in the compilation process, as they keep track of variable names, function names, objects, and other identifiers, along with their associated attributes such as type, scope, and memory location. This information is used during semantic analysis and code generation to ensure correct program execution and to optimize resource allocation.

Symbol tables are typically implemented as hash tables or linked lists, allowing efficient insertion, deletion, and lookup operations. They are often organized hierarchically to reflect the scope of identifiers, with nested tables representing nested scopes in the source code.