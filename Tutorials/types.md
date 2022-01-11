# TS Types

# Basic Types
  - Number
  - String
  - Boolean
  - Object

# Advanced Types
 - Tuple:
    -  added by typescript: fixed length array
    -  when is this handy?
      - `Role: [2, 'author']` 
    - Example `[number, string`]
    - **Note: Push will work with tuple but get other support**
  
  - Enums:
    -   Syntax: `enum { NEW, OLD }
    -   It automatically assigns a number to each enum start with 0, 1, 2 ... you can access it directly.
    -   Example
        -  ```
           Enum Role { ADMIN, Author }
           Role.ADMIN === 0, Role.AUTHOR === 1
           ```
    - can reassign the number to something else and will increment from there
    -  can assign your own string to everything as well

  - Any:
    -  most flexible but loose a lot of the features in TS
    -  *Avoid when possible!*

  - Union:
    - Syntax: number | string

  - Literal:
    - syntax: `‘as-number’ | ‘as-text’`
    - This is magic stringy

  - Type Alias:
    - example: type CheeseId = number | string

  - Void:
    - TS expects to return ‘void’ if no return value is sent back
    - If you return nothing (return;) then you can return ‘undefined’
    - Basically the message here is use void for everything, undefined is very rare.

  - Type Function:
    - Example: someValue: Function = () => {}
    - Function types are types that describe the function arguments and return value.
    - Syntax: let combinedValues: (a: number, b: number) => number;

  - Unknown:
    - more restrictive than any, needs additional checks
    - Example of a unknown input on a user form
    - Better choice over “any”, will eventually know what to do with it.
    - Has some type checking

  - Never
    - will never return anything from a function
    - This is inferred as void, but to be super clear, never gives additional context
