# Typescript Types

## Basic Type examples

### Strings, Numbers and Bools oh my!
```
let id: number = 5;
let company: string = 'some cool company';
let isPublished: boolean = true;
let x: any = 'Hello';

x = true;

let age: number;

age = 30;
```

## Complex Examples

### Arrays
```
let ids: number[] = [1, 2, 3, 4, 5];
let arr: any[] = [1, 2, 3, true];
```

### Tuple
Tuple must be in exact order or error will be throw
```
let person: [number, string, boolean] = [1, 'string', true];

// more complicated example
let employee: [number, string][];

employee = [
  [1, 'stuff'], 
  [2, 'more stuff']
];
```

### Union
```
let pid: string | number;

pid = '1';
pid = 1;
```

### Enums
```
// default
enum direction1 {
  Up, // 0
  Down, // 1
  Left, // 2
  Right // 3
}

console.log(direction1.Left) // 2

enum direction1 {
  Up = 1, // 1
  Down, // 2
  Left, // 3
  Right // 4
}

console.log(direction1.Down) // 2

enum direction2 {
  Up = 'Up',
  Down = 'Down', 
  Left = 'Left', 
  Right = 'Right'
}

console.log(direction2.Up) // 'Up'

````

### Objects
```
const user: {
  id: number,
  name: string
} = {
  id: 1,
  name: 'John'
}

// Object, the better way

type User = {
  id: number,
  name: string
};

const user: User = {
  id: 1,
  name: 'James'
}
```

## Type Assertion

### Method 1:
```
let cid: any = 1;

let customerId = <number>cid;

customerId = '1' // error! must be a number!
```

### Method 2:
```
let cid: any = 1;

let customerId = cid as number;
```

## Functions
### Basic Example With Return Value:
```
function addNumb(x: number, y: number): number {
  return x + y;
}

console.log(addNumb(1, 2)) // 3
```

### Example without return value
```
function log(message: string | number): void {
  console.log(message);
}

log('cheese') // cheese
```

## Interfaces

### Basic Example
```
interface UserInterface {
  readonly id: number, // read only property duh
  name: string,
  age?: number // this is an optional property
};

const user2: UserInterface = {
  id: 1,
  name: 'James'
}

```

### Interfaces and Functions
```
interface mathFunc {
  (x: number, y: number): number
}

const add: mathFunc = (x: number, y: number): number => x + y;

const sub: mathFunc = (x: number, y: number): number => x - y; // example of using the same interface, woooooo

```

### Interfaces and Classes
```
interface PersonInterface {
  id: number,
  name: string,
  register(): string
}

class Person implements PersonInterface {
  private id: number; // private property
  protected name: string; // protected property
  
  
  constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
  }

  register() {
    return `${this.name} is now registered`;
  }
}

const brad = new Person(5, 'Brad');

// extending

class Employee extends Person {
  position: string
  
  constructor(id, name, position) {
    super(id, name);

    this.position = position;
  }

}

const emp = new Employee(2, 'Shaun', 'Developer');
```

### Interface Gotchas

#### Interface Cannot Be Used With Primitives

#### Interface Cannot Be Used With Unions
*Wrong:*
```
interface Point = string | number;

let thing: Point = 'thing';
```

*Correct:*
```
type Point = string | number;

let thing: Point = 'thing';
```

## Generics

```
function getArray<T>(items: T[]): T[]{
  return new Array().concat(items);
}

let numbArray = getArray<number>([1, 2, 3, 4]);
let stringArray = getArray<string>(['jack', 'jill', 'john']);


```
