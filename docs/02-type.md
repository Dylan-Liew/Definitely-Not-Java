# Variable and Type Summary

## Data Abstraction: Variable
- Variables are abstractions over memory locations
- Provide user-friendly names instead of memory addresses
- Allow memory locations to change without affecting code

## Types
- Help manage program complexity
- Communicate data type information to readers
- Allow compiler to check for valid operations
- Determine how operations behave
- Example: String + String concatenates, Integer + Integer adds

## Static vs Dynamic Typing
- Dynamic Typing (e.g., Python, JavaScript)
    - Variables can hold different types
    - Type checking done at runtime
    - Type associated with values
    - Example: `x = 1; x = "hello"` is valid

- Static Typing (e.g., Java)
    - Variables must declare type
    - Type checking done at compile time
    - Type cannot change after declaration
    - Example: `int x = 1; x = "hello"` is invalid

## Strong vs Weak Typing
- Strong Typing
    - Enforces strict type rules
    - Ensures type safety
    - Prevents implicit type conversions
    - Example: Java prevents casting string to int

- Weak Typing
    - More permissive with type rules
    - Allows implicit type conversions
    - Example: C allows casting between unrelated types

## Java Primitive Types
- Boolean: `boolean` (1 bit)
- Character: `char` (16 bits)
- Integral Types:
    - `byte` (8 bits)
    - `short` (16 bits)
    - `int` (32 bits)
    - `long` (64 bits)
- Floating-Point:
    - `float` (32 bits)
    - `double` (64 bits)

## Subtyping
- Defines relationship between types where one type can substitute another
- Properties:
    - Reflexive: S <: S
    - Transitive: If S <: T and T <: U, then S <: U
    - Anti-symmetric: If S <: T and T <: S, then S = T

## Java Primitive Type Hierarchy
- Subtype relationships:
    - `byte` <: `short` <: `int` <: `long` <: `float` <: `double`
    - `char` <: `int`
- Widening type conversion happens automatically
- Narrowing conversion requires explicit casting
