# TypeScript notes

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
      -   
         
