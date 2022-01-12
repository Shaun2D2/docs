# Generics

- Basics:
  - is a way to define a generic type that can be used.  For example `Array` type if the same as `[]` and this is a generic.
    - example `const names: Array<string> = [] // same as string[]`

  - Promises are another type of generic.
    -  example: `const promise: Promise<string> = new Promise((res) => res('this is done')`

- Custom Generics:
  - creating your own custom see example below:  
    - `function merge<T, U>(objA: T, objB: U) { return Object.assign(objA, objB }`
    - This example willl know that the function objects are inferred types of the argument objects and now you can access stuff on the return data.
  - You can also override the implicit typing by providing your own types for the generic
    - `merge<string, object>('hello world', { age: 7 })`


- Contraints
  - restircts generics to certain types instead of just accepting anything
  - example: `function merge<T extends object, U extends string | number>(objA: T, objB: U) { ... }`

- Generic Functions
  - Able to provide generics to arguments and return values
  - example:
    ```
       interface Lenghty { 
        length: number;
       }
       
       function countAndDescribe<T extends Lenghty><element: T): [T, string] { ... }
    ```
- `keyof` Contrait
  -  example:
     ```
     function extractAndConvert<T extends object, U extends keyof T>(obj: T, key: U) {
      return obj[key]
     }
     ```
     
- Generic Classes
  - example:
    ```
    class DataStorage<T> {
      private data: T[] = [];
      
      setItem(item: T) {
        this.data.push(item);
      }
    }
    
    const data = new DataStorage<string>();
    
    data.setItem("stuff"); // is cool!
    data.setItem(10); // NOT cool!
    ```
