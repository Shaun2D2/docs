# Advanced Types

- Intersection Types
    - Allow us to combine multiple types 
        - Example: type ElevatedEmployee = Admin & Employee
    - can also use interfaces interface ElevatedEmployee extends Admin, Employee

- Type Guards
    - Use ‘privileges in emp’ to see if a property exists on a mixed type
    - can use “instanceof” to check type of a class

- Discriminated Union
    - Using a type property like ‘bird’ ‘horse’ in animal interfaces (remember example with switch statement).

- Type Casting
    - Converts the thing to whatever type you need, remember the HTML element example
        - Two ways to do this:
            - <> method: const userInput = <HTMLInputElement>document.getElementById(“thing”);
            - “As” method: const userInput = document.getElementById(“thing”) as HTMLInputElement;

- Index Types
    - Interface ErrorContainer { [prop: string]: string }

- Function overload
    - You can force the return value to be a certain type instead of a union type by adding overloads
    - Example: function add(a: string, b: string): string
    - Example: function add(a:number, b: number): number

- Optional Chaining
    - Used when getting data from a backend, you may not know if a certain property is defined
