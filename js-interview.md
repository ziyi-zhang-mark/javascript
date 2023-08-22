## Javascript Interview Questions
1. https://medium.com/interviewhackingninja/javascript-interview-questions-1-20-61d05fccf229

2. https://medium.com/interviewhackingninja/javascript-interview-questions-21-40-b35b8045a463

3. https://medium.com/interviewhackingninja/javascript-interview-questions-41-60-ea5bba4795cb

## Javascript concepts

https://spin.atomicobject.com/2014/10/20/javascript-scope-closures/

### Explain the differences on the usage of foo between function foo() {} and var foo = function() {}

Function Declaration vs Function Expression: A function declaration defines a function and doesn’t require a variable to hold it. Function declarations are hoisted. Function expressions define a function within an expression and are not hoisted.

```js
// Function declaration
function foo() { /*...*/ }

// Function expression
var foo = function() { /*...*/ };
```

### What is a closure, and how/why would you use one?

A closure is a function that has access to its own scope, the outer function’s scope, and the global scope. They’re often used to create data privacy, in factory functions, or in functional programming patterns.

```js
function outerFunction(outerVariable) {
    return function innerFunction(innerVariable) {
        console.log('outerVariable:', outerVariable);
        console.log('innerVariable:', innerVariable);
    }
}
const newFunction = outerFunction('outside');
newFunction('inside');  // logs both 'outside' and 'inside'
```

### Explain the difference between Object.freeze() vs const

Object.freeze() is used to make an object immutable, meaning you cannot change its properties. const is used to declare a variable that cannot be reassigned. However, if the const variable is an object, the object's properties can still be modified.

Example:
```js
const obj = {prop: 42};
obj.prop = 33; // Works, the property can be modified.
Object.freeze(obj);
obj.prop = 10; // Doesn't work, the object is now immutable.
```

### Suggest one simple way of removing duplicates from an array using ES6.

You can use a Set to easily remove duplicates from an array in ES6:
```js
const array = [1, 2, 3, 4, 4, 5, 5];
const uniqueArray = [...new Set(array)];
console.log(uniqueArray); // [1, 2, 3, 4, 5]
```

# Javascript Basics

- let vs const
- Arrow Functions

  - Besides a shorter syntax, they offer advantages when it comes to keeping the scope of the `this` keyword.

    ```js
    const multiply = (number) => number * 2;
    ```

- Export and Import

  ```js
  const person = {
    name: "max",
  };
  export default person;

  export const clean = () => {};
  export const baseData = 10;

  import prs from "./person.js";
  import { baseData } from "./utility.js";
  import { clean } from "./utility.js";
  import { something as Something } from "./utility.js";
  import * as bundled from "./utility.js";
  ```

- Classes

  ```js
  class Human {
    constructor(name, age) {
      this.name = name;  
      this.age = age;  
      this.gender = "male";
    }
    printGender() {
      console.log(this.gender);
    }
  }
  class Person extends Human {
    constructor(name, age) {
      super(name, age);
      this.gender = "female";
    }

    printMyName() {
      console.log(this.name);
    }
  }
  const myPerson = new Person("max", 25);
  myPerson.printMyName(); // max
  myPerson.printGender(); // female

  // ES6+ syntax
  class Human {
    gender = "male";
    printGender = () => {
      console.log(this.gender);
    };
  }
  class Person extends Human {
    name = "Max";
    gender = "female";

    printMyName = () => {
      console.log(this.name);
    };
  }
  const myPerson = new Person();
  myPerson.printMyName(); // Max
  myPerson.printGender(); // female
  ```

- Spread & Rest operators

  ```js
  // Spread: split up array elements or object properties
  const newArray = [...oldArray, 1, 2];
  const newObject = { ...oldObject, newProp: 5 };

  // Rest: merge a list of arguments into an array
  const filter = (...args) => {
    return args.filter((el) => el === 1);
  };
  ```

- Array and Object are reference type, others are primitive type

  ```js
  const person = {
    name: "max",
  };
  // shallow copy
  const secondPerson = {
    ...person,
  };
  ```