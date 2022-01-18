# Decorators

- Compiler Configuration
  - must enabled "experimentalDecorators" to true

- What is a Decorator? 
  - Decorator is a function that you apply to a class
  - They are executed when the class is defined, not instantiated
  
- Where can I add decorators
  - 

First Class Decorator Example:
```
function Logger(constructor: Function) {
  console.log("Logging");
  console.log(constructor);
}

@Logger
class Person {
 name = 'Max';
 
 constructor() {
  console.log("creating a person object");
 }
}

const pers = new Person();

console.log(pers);
```

Decorator Factory Example:
```
function Logger(logString: string) {
return function (constructor: Function) {
    console.log(logString);
    console.log(constructor);
  }
}

function WithTemplate(template: string, target: string){
  return function(constructor:Function) {
    const targetEl = document.getElementById(target);
    const p = new constructor();
    if (targetEl) {
      targetEl.innerHTML = template;
      targetEl.querySelector('h1').textContent = p.name;
    }
  
  }

}

@Logger("logging person");
@WithTemplate("<h1>hello world</h1>", "app");
class Person {
 name = 'Max';
 
 constructor() {
  console.log("creating a person object");
 }
}

const pers = new Person();

console.log(pers);
```

```
function Log(target: any, propertyName: string | Symbol) {
  console.log("property decorator!");
  console.log(target, propertyName);
}

// accessor decorator
function Log2(target: any, name: string, descriptor: PropertyDescriptor) {
  console.log("accessor decorator!");
  console.log(target, name, descriptor);
}

// method decorator
function Log3(target: any, name: string | Symbol, descriptor: PropertyDescriptor) {

}

// parameter decorator
function Log4(target, name, position) {
  
}

class Product {
  @Log
  title: string;
  private _price: number;
  
  constructor() {
    ...
  }
  
  @Log2 // can return something
  set price(val: number) {
    if (val > 0) {
      this._price = val;
    } else {
      throw new Error("blah");
    }
  }
  
  @Log3 // can return something
  coolMethod(@Log4 something: string) {
    ...
  }
...
}
```

autobind decorator example:
```
function Autobind(_target: any, _methodName: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;
  const adjDescriptor: PropertyDescxriptor = {
    configurable: true;
    enumerable: false,
    get() {
      const boundFn = originalMethod.bind(this);
      return boundFn;
    }
  }
  
  return adjDescriptor;
}

class Printer {
  message = "this works!";
  
  @Autobind
  showMessage() {
    console.log(this.message);
  }
}

const button = document.querySelector("button")!;

button.addEventListener('click', p.showMessage); // "this" will be the addEventListener instead of the class "this";

```

validator decorator example:

```
interface ValidatorConfig {
  [property: string]: {
    [validatableProp: string]: string[] // ['required', 'positive]
  }
}

const registeredValidators: ValidatorConfig = {};

function Required(target: any, propName: string) {
  registeredValidators[target.constructor.name] = {
    [propName]: ['positive']
  }
}

function PositiveNumber() {
  registeredValidators[target.constructor.name] = {
    [propName]: ['required']
  }
}

function validate(obj: object) {
  const objValidatorConfig = registeredValidators[obj.constructor.name];
  if (!objValidatorConfig) return true;
  
  for (const prop in objValidatorConfig) {
    for (const validator of objValidatorConfig[prop]){
      switch(validator) {
        case 'required':
          return !!obj[prop];
        case 'positivie':
          return obj[prop] > 0;
      }
    }
  }
  
  return true;
}

class Course {
  @Required
  title: string;
  @PositiveNumber
  price: number;
  
  constructor(t: string, p: number) {
    this.title = t;
    this.price = p;
  }
}
```


Modify class example:
```
function WithTemplate(template: string, target: string){
  return function<T extends {new(..args: any[]): {name: string} }>) >(originalConstructor:Function) {
    return class extends originalConstructor {
      constructor() {
        super();
        const targetEl = document.getElementById(target);
        if (targetEl) {
          targetEl.innerHTML = template;
          targetEl.querySelector('h1').textContent = this.name;
        }
      }
    }  
  }

}
```

