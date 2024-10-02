# Parsing Algorithms

## CFG Parsing Methods Expressivity Comparison

A comparison of the expressivity and restrictions of various context-free grammar (CFG) parsing methods.

##### Grammars Restrictions
- **CFG > LR(k) > LR(1) > LALR(1) > SLR(1)**: Context-Free Grammars (CFGs) are the most expressive, with each subsequent method imposing more restrictions on the grammar.
- **LR(k) > LL(k) > LL(1)**: LR(k) parsers can handle a broader range of grammars compared to LL(k) parsers, with LL(1) being the most restrictive among them.
- **LR(1) > LL(1)**: LR(1) parsers are more expressive than LL(1) parsers, allowing for a wider range of grammars.
- **LALR(1) != LL(1)**: LALR(1) and LL(1) parsers are not directly comparable in terms of expressivity, as they handle different types of grammar restrictions.

##### Languages Restrictions
- **CFG > LR(k)**: Context-Free Grammars can describe a broader set of languages than LR(k) parsers.
- **LR(k) = LR(1) = LALR(1) = SLR(1)**: These parsing methods are equivalent in terms of the languages they can recognize, despite differences in grammar restrictions.
- **LR(1) > LL(k) > LL(1)**: LR(1) parsers can recognize a broader set of languages compared to LL(k) and LL(1) parsers.
- **LALR(1) != LL(1)**: LALR(1) and LL(1) parsers are not directly comparable in terms of the languages they can recognize, as they are designed for different parsing strategies.

## Traversing Order > Top-down Parser / Bottom-up Parser

Two parsing methods distinguished by the order in which they process grammar rules and input strings.

**Top-down parsers** start from the highest-level rule of a grammar and recursively break down the rules to match the input string, often using techniques like recursive descent or LL parsing. They are easier to implement but may have limitations with left-recursive grammars.

**Bottom-up parsers** begin with the input string and work upwards to construct the parse tree by identifying and reducing substrings to non-terminals, using techniques like LR parsing. They are more robust and can handle a broader range of grammars, including left-recursive ones, but are generally more complex to implement.

## Comparison of Operator-precedence Parsers >

- **Precedence Climbing**: Recursive, suitable for simple expression parsing.
- **Shunting Yard**: Non-recursive, stack-based, ideal for infix to postfix conversion.
- **Pratt Parsing**: Flexible, efficient, handles complex precedence and associativity in programming languages.

## Precedence Climbing Method

- **Family**: Operator-precedence parser
- **Traversing Order**: Top-down
- **Complexity**: Generally O(n) for parsing expressions, though recursive calls can introduce minor inefficiencies
- **Grammar**: Suitable for LR(1) grammars where two consecutive non-terminals and epsilon never appear in the right-hand side of any rule
- **Overview**: A recursive approach to parsing expressions based on operator precedence. It is a top-down parsing technique.
- **How it Works**: Processes tokens from left to right, recursively descending into sub-expressions for operators with higher precedence. Uses a recursive function to handle operators and operands.
- **Use Case**: Often used in hand-written parsers for expressions with well-defined operator precedence.
- **Working Example**:
  ```
  E -> E + T | T
  T -> T * F | F
  F -> ( E ) | number
  ```
- **Broken Example**:
  ```
  E -> E E | epsilon
  ```

## Shunting Yard Algorithm

- **Family**: Operator-precedence parser
- **Traversing Order**: Bottom-up
- **Complexity**: Generally O(n) for parsing expressions
- **Grammar**: Suitable for LR(1) grammars where two consecutive non-terminals and epsilon never appear in the right-hand side of any rule
- **Overview**: Developed by Edsger Dijkstra, it is a non-recursive method for parsing infix expressions, converting them to postfix (RPN) or evaluating them.
- **How it Works**: Uses a stack for operators and an output queue for the expression. Processes tokens, respecting operator precedence and associativity, and pops operators to the output queue when necessary.
- **Use Case**: Widely used in calculators and interpreters for converting infix to postfix notation.
- **Working Example**:
  ```
  E -> E + T | T
  T -> T * F | F
  F -> ( E ) | number
  ```
- **Broken Example**:
  ```
  E -> E E | epsilon
  ```

## Pratt Parsing

- **Family**: Operator-precedence parser
- **Traversing Order**: Top-down
- **Complexity**: Generally O(n) for parsing expressions
- **Grammar**: Flexible with operator precedence and associativity; suitable for LR(1) grammars where two consecutive non-terminals and epsilon never appear in the right-hand side of any rule
- **Overview**: A top-down operator precedence parsing technique introduced by Vaughan Pratt. It is flexible and efficient.
- **How it Works**: Uses parsing functions associated with token types. Processes tokens based on precedence, using prefix and infix functions to handle expressions. Decides functions dynamically based on token and precedence.
- **Use Case**: Useful in programming language interpreters and compilers for handling complex operator precedence and associativity.
- **Working Example**:
  ```
  E -> E + T | T
  T -> T * F | F
  F -> ( E ) | number
  ```
- **Broken Example**:
  ```
  E -> E E | epsilon
  ```

## Recursive Descent Parser

A top-down parsing technique that uses a set of recursive procedures to process the input according to a grammar's production rules.

Recursive descent parsers are straightforward to implement and involve writing a separate function for each non-terminal in the grammar. These functions recursively call each other to match the input string against the grammar rules, making decisions based on the current input token. While they are intuitive and easy to understand, recursive descent parsers can struggle with left-recursive grammars, which can lead to infinite recursion.

To handle left recursion, grammars often need to be transformed or rewritten. Despite this limitation, recursive descent parsers are popular for their simplicity and are often used in educational settings and for small to medium-sized language parsers.

- **Family**: Top-down parser
- **Traversing Order**: Top-down
- **Complexity**: Typically O(n) for LL(1) grammars, but can become exponential with certain grammars and inputs requiring extensive backtracking
- **Grammar**: Suitable for LL(1) grammars; left recursion must be eliminated, and epsilon productions are typically not allowed
- **Overview**: A top-down parsing technique that uses a set of recursive procedures to process the input according to a grammar's production rules.
- **How it Works**: Involves writing a separate function for each non-terminal in the grammar, with these functions recursively calling each other to match the input string against the grammar rules. Decisions are made based on the current input token.
- **Use Case**: Popular for their simplicity, they are often used in educational settings and for small to medium-sized language parsers.
- **Working Example**:
  ```
  E -> T E'
  E' -> + T E' | epsilon
  T -> F T'
  T' -> * F T' | epsilon
  F -> ( E ) | number
  ```
- **Broken Example**:
  ```
  E -> E + T | T
  ```

## Packrat Parsing

A parsing technique that efficiently implements Parsing Expression Grammars (PEGs) using memoization to achieve linear-time performance.

**Packrat parsers** store intermediate parsing results in a memoization table, avoiding redundant computations and backtracking, which are common in other parsing methods. This ensures each part of the input is processed only once, leading to predictable and efficient parsing times, even for complex grammars. The trade-off is increased memory usage due to the storage of parsing results.

These parsers are particularly well-suited for implementing PEGs, as they can handle the deterministic choice operator and other PEG-specific constructs without ambiguity or performance degradation. By leveraging memoization, packrat parsers provide a robust solution for parsing tasks that require precise control over grammar rules and parsing decisions.

- **Family**: Parsing Expression Grammar (PEG) parser
- **Traversing Order**: Top-down
- **Complexity**: Linear time, O(n), due to memoization
- **Grammar**: Suitable for PEGs, which allow for deterministic parsing without ambiguity; can handle left recursion
- **Overview**: A top-down parsing technique that efficiently implements PEGs using memoization to achieve linear-time performance.
- **How it Works**: Stores intermediate parsing results in a memoization table to avoid redundant computations and backtracking, ensuring each part of the input is processed only once. This approach handles deterministic choice operators and other PEG-specific constructs without ambiguity.
- **Use Case**: Ideal for programming language parsers where precise control over parsing decisions is required, providing robust solutions for complex grammar parsing tasks.
- **Working Example**:
  ```
  Expr <- Term (('+' / '-') Term)*
  Term <- Factor (('*' / '/') Factor)*
  Factor <- '(' Expr ')' / number
  ```
- **Broken Example**:
  ```
  Expr <- Expr '+' Expr / epsilon
  ```
  ```
  A <- aAa | bAb | a | b | ε
  ```
