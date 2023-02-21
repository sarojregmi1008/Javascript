# Encapsulation in JavaScript
</Strong>Encapsulation in javascript is achieved using closures or using private fields.</strong>
Encapsulation in JavaScript is a technique used to protect data and behavior of an object from external interference or unauthorized access. It helps in keeping the code organized, secure, and maintainable. JavaScript provides several techniques to achieve encapsulation.

## Encapsulation using Closures
One of the most common techniques for encapsulation in JavaScript is the use of <strong>Closures</strong>. Closures allow variables to be defined within a function scope and then accessed and modified only through the function's own methods. This way, the variables remain private and cannot be accessed from outside the function.

The "<strong>module pattern</strong>" is a common implementation of encapsulation using closures in JavaScript. It involves creating a function that returns an object with public and private properties and methods.

Here's an example of encapsulation using closures in JavaScript:

###### Javascript code
```
const counter = (function() {
  let count = 0; // private variable

  function increment() { // private method
    count++;
  }

  function reset() { // private method
    count = 0;
  }

  return {
    getCount: function() { // public method
      return count;
    },
    incrementCount: function() { // public method
      increment();
    },
    resetCount: function() { // public method
      reset();
    }
  };
})();

console.log(counter.getCount()); // Output: 0
counter.incrementCount();
console.log(counter.getCount()); // Output: 1
counter.resetCount();
console.log(counter.getCount()); // Output: 0
console.log(counter.count); // Output: undefined (private variable cannot be accessed)
```
In this example, the counter function is immediately invoked, creating a closure that contains the private count, increment, and reset variables and functions. The counter function returns an object with three public methods: getCount, incrementCount, and resetCount, which can be used to interact with the private variables.

Because the private variables and functions are enclosed within the counter function, they are not accessible from the outside, and only the public methods can be accessed. This creates a "black box" effect that prevents external code from interfering with the internal workings of the counter object.

## Encapsulation using Classes
Another technique for encapsulation in JavaScript is the use of <strong>Classes</strong>, introduced in ECMAScript 6. Classes allow you to define objects with private properties and methods, which can only be accessed from within the class. This is achieved by using the "<strong>private</strong>" keyword to define private members.

Here's an <strong>example</strong> of encapsulation using a class in JavaScript:

###### Javascript code
```
class Person {
  #name; // private member

  constructor(name) {
    this.#name = name;
  }

  getName() {
    return this.#name;
  }
}

const person = new Person("John");
console.log(person.getName()); // Output: John
console.log(person.#name); // Error: Private member '#name' cannot be accessed outside class
```
In this <strong>example</strong>, the #name property is <strong>private</strong> and can only be accessed through the getName() method. Any attempt to access the #name property from outside the class will result in an error.

Encapsulation is an important concept in object-oriented programming, and its implementation in JavaScript can help create robust and maintainable code.

### Maintaining Private Variables in JavaScript Classes
In JavaScript, you can maintain private variables in classes by using closures, WeakMap, or Symbols. Here are some examples of each approach:

## Using Closures
In this approach, you create a private variable in the constructor function and then create methods that can access it via a closure. The private variable is not accessible outside the class.

###### Javascript code
```
// Define a class named Counter
class Counter {
// Define a constructor for Counter class
constructor() {
let count = 0; // Define a private variable count with initial value of 0
this.increment = function() { // Define a method increment that increments the count variable by 1
count++;
};
this.getCount = function() { // Define a method getCount that returns the current value of count variable
return count;
};
}
}

// Create an instance of Counter class
const counter = new Counter();

// Call the increment method on the counter object
counter.increment();

// Call the getCount method on the counter object and log the output to the console
console.log(counter.getCount()); // Output: 1

// Try to access the private variable count outside the Counter class, which should be undefined
console.log(counter.count); // Output: undefined
```
In this example, count is a private variable that can only be accessed by the increment and getCount methods. The count variable is not accessible outside the Counter class

# Closures:
In JavaScript, a <strong>Closure</strong> is created whenever a function is defined inside another function. A <strong>Closure</strong> is a combination of a function and the environment in which it was declared. The environment consists of any local variables that were in scope at the time the <strong>Closure</strong> was created.

<strong>Closures</strong> are powerful because they allow a function to have "<strong>private</strong>" variables that are accessible only within the function's scope. This can be useful for creating modular and maintainable code.

Here's an example of a closure in JavaScript:
###### Javascript code
```
function outerFunction() {
  const outerVariable = "I'm outside!"; // local variable, accessible only inside `outerFunction`

  function innerFunction() {
    console.log(outerVariable); // logs the value of `outerVariable`, which is a private variable of `innerFunction`
  }

  return innerFunction; // returns the inner function, which will maintain access to `outerVariable`
}

const inner = outerFunction(); // calls `outerFunction`, which returns `innerFunction` and assigns it to the `inner` variable
innerFunction(); // calls `innerFunction`, which logs the value of `outerVariable`
```
In this example, <strong>innerFunction</strong> is defined inside <strong>outerFunction</strong>, which means it has access to the <strong>outerVariable</strong> that is defined in the outer function's <strong>scope</strong>. When <strong>innerFunction</strong> is returned from outerFunction and assigned to the inner variable, it forms a <strong>Closure</strong> that includes both the function and its environment. When <strong>innerFunction</strong> is called, it logs the value of outerVariable, even though that variable is not directly accessible outside of <strong>outerFunction</strong>.

In a <strong>Closure</strong>, <strong>free variables</strong> are the variables that are defined outside the inner function, but are accessible within it due to the closure's scope. The inner function can access the free variables and their values at the time the closure was created. <strong>Free Variable</strong> is
```
const outerVariable = "I'm outside!";
```



