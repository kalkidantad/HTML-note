# JS Q&A and Notes

1. What is the difference between dynamically and statically types languages?
- **Statically Typed Languages**: In these languages, type checking occurs at compile time. This means that the type of each variable must be known before the source code is compiled[1](https://www.baeldung.com/cs/statically-vs-dynamically-typed-languages). Some common examples of statically typed languages are Java, Haskell, C, C++, C#, Scala, Fortran, Go, Pascal, and Swift.
- **Dynamically Typed Languages**: These languages associate types with run-time values rather than named variables/fields/etc[2](https://stackoverflow.com/questions/1517582/what-is-the-difference-between-statically-typed-and-dynamically-typed-languages). This means that you can write a little quicker because you do not have to specify types every time. Examples of dynamically typed languages include Perl, Ruby, Python, PHP, JavaScript, and Erlang.

2.The difference between function declaration and expression ; in declaration variables can be accessed before initialization but we can’t in expressions. 

In JavaScript, both function declarations and function expressions are ways to define a function, but they have some differences:

**Function Declaration**:

- [A function declaration must have a function name1](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/).
- [Function declarations are standalone constructs and they cannot be nested inside a functional block1](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/).
- [They are executed before any other code](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/)[2](https://stackoverflow.com/questions/1013385/what-is-the-difference-between-a-function-expression-vs-declaration-in-javascrip)[1](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/). This is known as hoisting.
- [The function in function declaration can be accessed before and after the function definition1](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/).
- Syntax:

```jsx
function functionName (param1, param2) {
  // Set of statements
}

```

**Function Expression**:

- [A function expression is similar to a function declaration without the function name1](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/). This creates an anonymous function.
- [Function expressions can be stored in a variable assignment1](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/).
- [Function expressions load and execute only when the program interpreter reaches the line of code](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/)[2](https://stackoverflow.com/questions/1013385/what-is-the-difference-between-a-function-expression-vs-declaration-in-javascrip)[1](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/).
- [The function in function expression can be accessed only after the function definition1](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/).
- Syntax:

```jsx
var functionName = function (param1, param2) {
  // Set of statements
}

```

The main difference lies in how the browser loads them into the execution context. [If you try to call a function expression before it’s loaded, you’ll get an error! If you call a function declaration instead, it’ll always work, because no code can be called until all declarations are loaded](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/)[2](https://stackoverflow.com/questions/1013385/what-is-the-difference-between-a-function-expression-vs-declaration-in-javascrip).

Here’s an example to illustrate this:

**Function Expression**

```jsx
alert(foo()); // ERROR! foo wasn't loaded yet
var foo = function() {
  return 5;
}

```

**Function Declaration**

```jsx
alert(foo()); // Alerts 5. Declarations are loaded before any code can run.
function foo() {
  return 5;
}

```

3)  what is prototype property?

[The prototype property in JavaScript is a global property available with all JavaScript objects1](https://www.w3schools.com/jsref/jsref_object_prototype.asp). [It’s an object which contains a constructor property2](https://www.freecodecamp.org/news/javascript-prototype-explained-with-examples/). [This property allows you to add new properties and methods to objects1](https://www.w3schools.com/jsref/jsref_object_prototype.asp).

[JavaScript is a prototype-based language, so whenever we create a function using JavaScript, the JavaScript engine adds a prototype property inside the function3](https://www.geeksforgeeks.org/prototype-in-javascript/). [The prototype property is basically an object (also known as Prototype object), where we can attach methods and properties in a prototype object, which enables all the other objects to inherit these methods and properties3](https://www.geeksforgeeks.org/prototype-in-javascript/).

All JavaScript objects inherit properties and methods from a prototype. [For example, Date objects inherit from Date.prototype, Array objects inherit from Array.prototype, and so on4](https://www.w3schools.com/js/js_object_prototypes.asp). [The Object.prototype is on the top of the prototype inheritance chain: Date objects, Array objects, and Person objects inherit from Object.prototype4](https://www.w3schools.com/js/js_object_prototypes.asp).

Here’s an example:

```jsx
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

Person.prototype.nationality = "English";

```

In this example, `Person.prototype.nationality` adds a new property to the `Person` object constructor. [Now all `Person` objects will have a `nationality` property with the value "English"](https://www.w3schools.com/jsref/jsref_object_prototype.asp)[4](https://www.w3schools.com/js/js_object_prototypes.asp).

4) What are ARROW FUNCTIONS?

A function that allows cleaner way of writing compared to the regular one.

Syntax:

```jsx
let myFunction = (arg1,arg2,...,argN ) => {
    statement(s)
}
```

```jsx
  //function expression 
let fun= function(x,y){
return x + y;
}
//alternative way using arrow functions
let x= (x,y) => x + y; 
```

Arrow functions can have only one argument:

```jsx
 let greet = x => console.log(x);
greet('Hello');
```

```jsx
const changeToUpperCase = arr => {
  const newArr = []
  for (const element of arr) {
    newArr.push(element.toUpperCase())
  }
  return newArr
}

const countries = ['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']
console.log(changeToUpperCase(countries))

// ["FINLAND", "SWEDEN", "NORWAY", "DENMARK", "ICELAND"]
```

PROPERTIES OF ARROW FUNCTIONS

1. **Arrow functions do not have the prototype property**: In JavaScript, every function has a `prototype` property (except for arrow functions) that is used for inheritance. Arrow functions, however, do not have a `prototype` property. This means you cannot use them as constructor functions and you cannot add new properties to them.
2. **Arrow functions cannot be used with the new keyword**: The `new` keyword in JavaScript is used to create an instance of an object that has a constructor. Since arrow functions do not have their own `this` context and they do not have a `prototype` property, they cannot be used as constructors. Therefore, if you try to use the `new` keyword with an arrow function, it will throw an error.
3. **Arrow functions cannot be used as constructors**: As mentioned above, arrow functions do not have a `prototype` property and do not have their own `this` context. This makes them unsuitable for use as constructors. A constructor in JavaScript is a special method that is used to create and initialize an object. Since arrow functions don’t have these capabilities, they can’t be used in this way.
4. **Arrow functions cannot be used as generator functions that use the yield keyword to return multiple values over time**: Generator functions in JavaScript are special functions that can be exited and later re-entered, allowing them to produce a sequence of values over time. They are defined using the `function*` syntax and make use of the `yield` keyword. However, arrow functions cannot be defined with the `function*` syntax and therefore cannot be used as generator functions.

**Arrow functions do not have the prototype property**:

```jsx
let arrowFunc = () => {};
console.log(arrowFunc.prototype);  // undefined

```

In this example, we define an arrow function `arrowFunc` and then try to log its `prototype` property. The output is `undefined`, showing that arrow functions do not have a `prototype` property.

**Arrow functions cannot be used with the new keyword**:

```jsx
let arrowFunc = () => {};
let instance = new arrowFunc();  // TypeError: arrowFunc is not a constructor

```

In this example, we again define an arrow function `arrowFunc`. Then we try to create a new instance of `arrowFunc` using the `new` keyword. This throws a Type Error, showing that arrow functions cannot be used as constructors.

**Arrow functions cannot be used as constructors**: This is similar to the previous point. Since arrow functions don’t have their own `this` binding and don’t have a `prototype` property, they can’t be used as constructors.

**These functions are anonymous and it is hard to debug the code**: When you’re debugging JavaScript code and you come across an error in an arrow function, the stack trace won’t give you a function name. This can make it harder to find where the error occurred.

**Arrow functions cannot be used as generator functions that use the yield keyword to return multiple values over time**:

```jsx
let arrowGenerator = *() => { yield 1; };  // SyntaxError: Unexpected token '*'

```

In this example, we try to define an arrow function `arrowGenerator` as a generator function using the `*` syntax and the `yield` keyword. This throws a Syntax Error, showing that arrow functions cannot be used as generator functions.

5) What are Anonymous FUNCTIONS?

They are functions without names.

```jsx
(function () { //...     })
//the above function alone is not accessible 

//it needs to be assigned to a variable that is called expression function
let show = function () { console.log('Anonymous function');     };
show();

```

Using anonymous functions as arguments:

```jsx
setTimeout(function() {
    console.log('Execute later after 1 second')
}, 1000);
```

6) what are constructor functions and generator functions in js?

In JavaScript, both constructor functions and generator functions are special types of functions that serve different purposes:

**Constructor Functions**:

- [A constructor function is a regular JavaScript function that is used to construct objects1](https://www.w3schools.com/JS/js_object_constructors.asp)[2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor)[3](https://rollbar.com/blog/javascript-constructors/)[4](https://www.tektutorialshub.com/javascript/constructor-function-new-operator-in-javascript/).
- The `this` keyword in a constructor function does not have a value. It is a substitute for the new object. [The value of `this` will become the new object when a new object is created1](https://www.w3schools.com/JS/js_object_constructors.asp).
- [Constructor functions are typically written with an uppercase first letter1](https://www.w3schools.com/JS/js_object_constructors.asp).
- [When we invoke it using the `new` keyword, it creates a new instance of the object and returns it](https://www.w3schools.com/JS/js_object_constructors.asp)[3](https://rollbar.com/blog/javascript-constructors/)[4](https://www.tektutorialshub.com/javascript/constructor-function-new-operator-in-javascript/).
- [You can add properties and methods to a JavaScript object through its constructor function1](https://www.w3schools.com/JS/js_object_constructors.asp).
- Here’s an example of a constructor function:

```jsx
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}

```

In this example, `Person` [is a constructor function`Person` constructs objects with properties `firstName`, `lastName`, `age`, and `eyeColor`1](https://www.w3schools.com/JS/js_object_constructors.asp).

**Generator Functions**:

- [A generator function is a special kind of function that works as a factory for iterators](https://www.w3schools.com/JS/js_object_constructors.asp)[5](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)[6](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/GeneratorFunction)[7](https://www.tutorialspoint.com/explain-generator-functions-in-javascript).
- [A generator function is defined with the `function*` syntax](https://www.w3schools.com/JS/js_object_constructors.asp)[5](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)[6](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/GeneratorFunction)[7](https://www.tutorialspoint.com/explain-generator-functions-in-javascript).
- [The function now becomes a generator and gets a new keyword, `yield`, that it can use to pass out data](https://www.w3schools.com/JS/js_object_constructors.asp)[7](https://www.tutorialspoint.com/explain-generator-functions-in-javascript).
- [Generator functions provide a powerful alternative: they allow you to define an iterative algorithm by writing a single function whose execution is not continuous](https://www.w3schools.com/JS/js_object_constructors.asp)[5](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators).
- When called, generator functions do not initially execute their code. [Instead, they return a special type of iterator, called a Generator](https://www.w3schools.com/JS/js_object_constructors.asp)[5](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)[6](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/GeneratorFunction).
- [When a value is consumed by calling the generator’s next method, the Generator function executes until it encounters the `yield` keyword](https://www.w3schools.com/JS/js_object_constructors.asp)[5](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators).
- Here’s an example of a generator function:

```jsx
function* idMaker() {
  var index = 0;
  while (true)
    yield index++;
}

```

[In this example, `idMaker` is a generator function that produces an infinite sequence of IDs](https://www.w3schools.com/JS/js_object_constructors.asp)[5](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators).

7) what are the categories of expressions in js?

1. PRIMARY( EX. this keyword)
2. ARITHMETIC ( TAKES NUMERICAL VALUES AS OPERANDS)
3. STRING ( WHEN STRINGS ARE CONCATENATED)
4. LOGICAL ( VALUES ARE COMPARED)
5. LEFT-HAND SIDE ( WHERE VALUES ARE ASSIGNED TO A VARIABLE)

8) **this Keyword**:

 The handling of **`this`** is different in arrow functions compared to regular functions. In regular functions the **`this`** keyword represented the object that called the function, which could be the window, the document, a button or whatever. [With arrow functions the **`this`** keyword always represents the object that defined the arrow function1](https://www.w3schools.com/Js/js_arrow_function.asp). IT CAN BE USED IN AN OBJECT , ALONE AND IN OBJECT METHOD BINDINGS.

```jsx
intro : function() {
 return "My name is " + this.name "and, I am a" + this.occupation;
}
```

```jsx
let wes = this;
```

```jsx
let student = {
firstName : "Juliana",
lastName : "Carpe",
myFunction : function() {
 return this;
   }
};
```

1. What is the difference between  isNaN and Number.isNaN?

**NaN:** non writable- can’t be overwritten, non- configurable - doesn’t show up in for-in loop, non enumurable- attributes can’t be redefined.

**`[isNaN()`** and **`Number.isNaN()`** are two different methods in JavaScript that are used to check if a value is **`NaN`** (Not a Number) 1](https://www.w3schools.com/jsref/jsref_isNaN.asp)[2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN)[3](https://dev.to/mang0088/isnan-vs-numberisnan-5e01).

[The **`isNaN()`** method returns **`true`** if the passed value is **`NaN`** or cannot be converted to a number, and **`false`** otherwise 1](https://www.w3schools.com/jsref/jsref_isNaN.asp)[2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN)[3](https://dev.to/mang0088/isnan-vs-numberisnan-5e01). However, this method has some issues when checking for **`NaN`**, as it coerces the passed value to a number before checking if it’s **`NaN`**. [This means that it can return **`true`** for values that are not actually **`NaN`**, such as empty strings or objects](https://www.w3schools.com/jsref/jsref_isNaN.asp) .

On the other hand, the **`Number.isNaN()`** method returns **`true`** only if the passed value is of type **`number`** and is equal to **`NaN`**. [It does not coerce the passed value to a number before checking if it’s **`NaN`**, so it avoids the issues of the **`isNaN()`** method 1](https://www.w3schools.com/jsref/jsref_isNaN.asp)[2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN)[3](https://dev.to/mang0088/isnan-vs-numberisnan-5e01).

In summary, use **`isNaN()`** when you want to check if a value is not a number or cannot be converted to a number, and use **`Number.isNaN()`** when you want to check if a value is of type **`number`** and is equal to **`NaN`**

`console.log(isNaN("hello")); // true
console.log(Number.isNaN("hello")); // false`

`console.log(isNaN({})); // true
console.log(Number.isNaN({})); // false`

`console.log(isNaN(NaN)); // true
console.log(Number.isNaN(NaN)); // true`

1. The difference between primitive and non primitive datatypes?

JavaScript classifies data into two main categories: **primitives** and **non-primitives**. Understanding these differences is crucial for writing efficient and effective code. Let's explore the key distinctions with code examples:

**1. Mutability:**

- **Primitive:** Immutable. Their value cannot be changed once assigned.
- **Non-Primitive:** Mutable. Their value can be modified after creation.

**Example:**

**JavaScript**

```jsx
let num1 = 10; // Primitive, value cannot be changed directly
let arr = [1, 2, 3]; // Non-Primitive, value can be changed

// Modifying arr modifies its content, not its reference
arr[1] = 5;
console.log(arr); // Output: [1, 5, 3]

// Trying to modify num1 directly throws an error
num1++;
console.error("Cannot assign to a read-only property '++num1'");

```

**2. Comparison:**

- **Primitive:** Compared by value. Two primitives are equal if they have the same value.
- **Non-Primitive:** Compared by reference. Two non-primitives are equal if they point to the same memory location.

**Example:**

**JavaScript**

```jsx
let str1 = "hello";
let str2 = "hello";
let obj1 = {};
let obj2 = {};

console.log(str1 === str2); // true - same value, same reference
console.log(obj1 === obj2); // false - different references, even if values are similar

```

**3. Storage:**

- **Primitive:** Stored directly in memory.
- **Non-Primitive:** Stored as references to their values in memory.

**4. Examples:**

- **Primitive:** Number, String, Boolean, Null, Undefined, Symbol, BigInt
- **Non-Primitive:** Object, Array, Function

**5. Key Takeaways:**

- Primitives represent simple data values like numbers and strings.
- Non-primitives are complex structures like objects and arrays that hold collections of data.
- Understanding these differences allows you to leverage the right data type for the task, optimize memory usage, and write code with better clarity and performance.

# String

Strings are useful for holding data that can be represented in text form. Some of the most-used operations on strings are to check their `[length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length)`, to build and concatenate them using the `[+` and `+=` string operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_operators#string_operators), checking for the existence or location of substrings with the `[indexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)` method, or extracting substrings with the `[substring()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring)` method.

```jsx
// using string literals
const string1 = "A string primitive";
const string2 = 'Also a string primitive';
const string3 = `Yet another string primitive`;
// as objects using string constructor
const string4 = new String("A String object");
```

### Methods

- Anchor( )
    
    The code below creates an HTML string and then replaces the document's body with it:
    
    ```jsx
    const contentString = "Hello, world";
    
    document.body.innerHTML = contentString.anchor("hello");
    ```
    
    It creates:
    
    ```html
    <a name="hello">Hello, world</a>
    ```
    
- At( )
    
    The **`at()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values takes an integer value and returns a new `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` consisting of the single UTF-16 code unit located at the specified offset. This method allows for positive and negative integers. Negative integers count back from the last string character.
    
    ```jsx
    const sentence = 'The quick brown fox jumps over the lazy dog.';
    
    let index = 5;
    
    console.log(`An index of ${index} returns the character ${sentence.at(index)}`);
    // Expected output: "An index of 5 returns the character u"
    
    index = -4;
    
    console.log(`An index of ${index} returns the character ${sentence.at(index)}`);
    // Expected output: "An index of -4 returns the character d"
    ```
    
    ```jsx
    const atWay = myString.at(-2);
    console.log(atWay); // 't'
    ```
    
- charAt( )
    
    The **`charAt()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values returns a new string consisting of the single UTF-16 code unit at the given index.
    
    ```jsx
    const sentence = 'The quick brown fox jumps over the lazy dog.';
    
    const index = 4;
    
    console.log(`The character at index ${index} is ${sentence.charAt(index)}`);
    // Expected output: "The character at index 4 is q"
    ```
    
- charCodeAt( )
    
    The **`charCodeAt()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values returns an integer between `0` and `65535` representing the UTF-16 code unit at the given index.
    
    ```jsx
    const sentence = 'The quick brown fox jumps over the lazy dog.';
    
    const index = 4;
    
    console.log(
      `Character code ${sentence.charCodeAt(index)} is equal to ${sentence.charAt(
        index,
      )}`,
    );
    // Expected output: "Character code 113 is equal to q"
    ```
    
- codePointAt( )
    
    The **`codePointAt()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values returns a non-negative integer that is the Unicode code point value of the character starting at the given index. Note that the index is still based on UTF-16 code units, not Unicode code points.
    
    ```jsx
    const icons = '☃★♲';
    
    console.log(icons.codePointAt(1));
    // Expected output: "9733"
    ```
    
- concat( )
    
    The **`concat()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values concatenates the string arguments to this string and returns a new string.
    
    ```jsx
    const str1 = 'Hello';
    const str2 = 'World';
    
    console.log(str1.concat(' ', str2));
    // Expected output: "Hello World"
    
    console.log(str2.concat(', ', str1));
    // Expected output: "World, Hello"
    ```
    
- endsWith( )
    
    The **`endsWith()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values determines whether a string ends with the characters of this string, returning `true` or `false` as appropriate.
    
    ```jsx
    const str1 = 'Cats are the best!';
    
    console.log(str1.endsWith('best!'));
    // Expected output: true
    
    console.log(str1.endsWith('best', 17));
    // Expected output: true
    
    const str2 = 'Is this a question?';
    
    console.log(str2.endsWith('question'));
    // Expected output: false
    ```
    
- fromCharCode( )
    
    The **`String.fromCharCode()`** static method returns a string created from the specified sequence of UTF-16 code units.
    
    ```jsx
    console.log(String.fromCharCode(189, 43, 190, 61));
    // Expected output: "½+¾="
    ```
    
- fromCodePoint( )
    
    The **`String.fromCodePoint()`** static method returns a string created from the specified sequence of code points.
    
    ```jsx
    console.log(String.fromCodePoint(9731, 9733, 9842, 0x2f804));
    // Expected output: "☃★♲你"
    ```
    
- isWellFormed( )
    
    The **`isWellFormed()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values returns a boolean indicating whether this string contains any [lone surrogates](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#utf-16_characters_unicode_code_points_and_grapheme_clusters).
    
    ```jsx
    console.log(String.fromCodePoint(9731, 9733, 9842, 0x2f804));
    // Expected output: "☃★♲你"
    ```
    
- match( )
    
    The **`match()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values retrieves the result of matching this string against a [regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions).
    
    ```jsx
    const paragraph = 'The quick brown fox jumps over the lazy dog. It barked.';
    const regex = /[A-Z]/g;
    const found = paragraph.match(regex);
    
    console.log(found);
    // Expected output: Array ["T", "I"]
    ```
    
- matchAll( )
    
    The **`matchAll()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values returns an iterator of all results matching this string against a [regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions), including [capturing groups](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Groups_and_backreferences).
    
    ```jsx
    const regexp = /t(e)(st(\d?))/g;
    const str = 'test1test2';
    
    const array = [...str.matchAll(regexp)];
    
    console.log(array[0]);
    // Expected output: Array ["test1", "e", "st1", "1"]
    
    console.log(array[1]);
    // Expected output: Array ["test2", "e", "st2", "2"]
    ```
    
- padEnd( )
    
    The **`padEnd()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values pads this string with a given string (repeated, if needed) so that the resulting string reaches a given length. The padding is applied from the end of this string.
    
    ```jsx
    const str1 = 'Breaded Mushrooms';
    
    console.log(str1.padEnd(25, '.'));
    // Expected output: "Breaded Mushrooms........"
    
    const str2 = '200';
    
    console.log(str2.padEnd(5));
    // Expected output: "200  "
    ```
    
- padStart( )
    
    The **`padStart()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values pads this string with another string (multiple times, if needed) until the resulting string reaches the given length. The padding is applied from the start of this string.
    
    ```jsx
    const str1 = '5';
    
    console.log(str1.padStart(2, '0'));
    // Expected output: "05"
    
    const fullNumber = '2034399002125581';
    const last4Digits = fullNumber.slice(-4);
    const maskedNumber = last4Digits.padStart(fullNumber.length, '*');
    
    console.log(maskedNumber);
    // Expected output: "************5581"
    ```
    
- String.raw( )
    
    The **`String.raw()`** static method is a tag function of [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals). This is similar to the `r` prefix in Python, or the `@` prefix in C# for string literals. It's used to get the raw string form of template literals — that is, substitutions (e.g. `${foo}`) are processed, but escape sequences (e.g. `\n`) are not.
    
    ```jsx
    // Create a variable that uses a Windows
    // path without escaping the backslashes:
    const filePath = String.raw`C:\Development\profile\aboutme.html`;
    
    console.log(`The file was uploaded from: ${filePath}`);
    // Expected output: "The file was uploaded from: C:\Development\profile\aboutme.html"
    ```
    
- Slice( ): The **`slice()`** method of `[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)` values extracts a section of this string and returns it as a new string, without modifying the original string.

`slice()` extracts the text from one string and returns a new string. Changes to the text in one string do not affect the other string.

```jsx
slice(indexStart)
slice(indexStart, indexEnd)
const str = 'The quick brown fox jumps over the lazy dog.';

console.log(str.slice(31));
// Expected output: "the lazy dog."

console.log(str.slice(4, 19));
// Expected output: "quick brown fox"

console.log(str.slice(-4));
// Expected output: "dog."

console.log(str.slice(-9, -5));
// Expected output: "lazy"

const str1 = "The morning is upon us."; // The length of str1 is 23.
const str2 = str1.slice(1, 8);
const str3 = str1.slice(4, -2);
const str4 = str1.slice(12);
const str5 = str1.slice(30);
console.log(str2); // he morn
console.log(str3); // morning is upon u
console.log(str4); // is upon us.
console.log(str5); // ""
console.log(str.slice(-11, 16)); // "is u"
console.log(str.slice(11, -7)); // " is u"
```

# Array

Slice: To cut out a multiple items in range. It takes two parameters: starting and ending position. It doesn't include the ending position.

```jsx
const numbers = [1,2,3,4,5]

  console.log(numbers.slice()) // -> it copies all  item
  console.log(numbers.slice(0)) // -> it copies all  item
  console.log(numbers.slice(0, numbers.length)) // it copies all  item
  console.log(numbers.slice(1,4)) // -> [2,3,4] // it doesn't include the ending position
```

Splice: It takes three parameters: Starting position, number of times to be removed and number of items to be added.

```jsx
const numbers = [1, 2, 3, 4, 5]
  numbers.splice()
  console.log(numbers)                // -> remove all items
const numbers = [1, 2, 3, 4, 5]
	numbers.splice(0,1)
  console.log(numbers)            // remove the first item
const numbers = [1, 2, 3, 4, 5, 6]
	numbers.splice(3, 3, 7, 8, 9)
  console.log(numbers.splice(3, 3, 7, 8, 9))  // -> [1, 2, 3, 7, 8, 9] //it removes three item and replace three items
```

# Loops

### for of loop

We use for of loop for arrays. It is very hand way to iterate through an array if we are not interested in the index of each element in the array.

```jsx
const numbers = [1, 2, 3, 4, 5]

for (const num of numbers) {
  console.log(num)
}

// 1 2 3 4 5

for (const num of numbers) {
  console.log(num * num)
}

// 1 4 9 16 25

// adding all the numbers in the array
let sum = 0
for (const num of numbers) {
  sum = sum + num  
	// can be also shorten like this, sum += num
  // after this we will use the shorter synthax(+=, -=, *=, /= etc)
}
console.log(sum) // 15

const webTechs = [
  'HTML',
  'CSS',
  'JavaScript',
  'React',
  'Redux',
  'Node',
  'MongoDB'
]

for (const tech of webTechs) {
  console.log(tech.toUpperCase())
}

// HTML CSS JAVASCRIPT REACT NODE MONGODB

for (const tech of webTechs) {
  console.log(tech[0]) // get only the first letter of each element,  H C J R N M
}
const countries = ['Finland', 'Sweden', 'Norway', 'Denmark', 'Iceland']
const newArr = []
for(const country of countries){
  newArr.push(country.toUpperCase())
}

console.log(newArr)  // ["FINLAND", "SWEDEN", "NORWAY", "DENMARK", "ICELAND"]
```

# Functions

### Function with unlimited number of parameters

Sometimes we do not know how many arguments the user going to pass. Therefore, we should know how to write a function which can take unlimited number of arguments. The way we do it has a significant difference between a function declaration(regular function) and arrow function. Let us see examples both in function declaration and arrow function.

### Unlimited number of parameters in regular function

A function declaration provides a function scoped arguments array like object. Any thing we passed as argument in the function can be accessed from arguments object inside the functions. Let us see an example

```jsx
// Let us access the arguments object

function sumAllNums() {
 console.log(arguments)
}

sumAllNums(1, 2, 3, 4)
// Arguments(4) [1, 2, 3, 4, callee: ƒ, Symbol(Symbol.iterator): ƒ]
// function declaration

function sumAllNums() {
  let sum = 0
  for (let i = 0; i < arguments.length; i++) {
    sum += arguments[i]
  }
  return sum
}

console.log(sumAllNums(1, 2, 3, 4)) // 10
console.log(sumAllNums(10, 20, 13, 40, 10))  // 93
console.log(sumAllNums(15, 20, 30, 25, 10, 33, 40))  // 173
```

### Unlimited number of parameters in arrow function

Arrow function does not have the function scoped arguments object. To implement a function which takes unlimited number of arguments in an arrow function we use spread operator followed by any parameter name. Any thing we passed as argument in the function can be accessed as array in the arrow function. Let us see an example

```jsx
// Let us access the arguments object

const sumAllNums = (...args) => {
 // console.log(arguments), arguments object not found in arrow function
 // instead we use a parameter followed by spread operator (...)
 console.log(args)
}

sumAllNums(1, 2, 3, 4)
// [1, 2, 3, 4]

// function declaration

const sumAllNums = (...args) => {
  let sum = 0
  for (const element of args) {
    sum += element
  }
  return sum
}

console.log(sumAllNums(1, 2, 3, 4)) // 10
console.log(sumAllNums(10, 20, 13, 40, 10))  // 93
console.log(sumAllNums(15, 20, 30, 25, 10, 33, 40))  // 173
```

### Self Invoking Functions

Self invoking functions are anonymous functions which do not need to be called to return a value.

```jsx
(function(n) {
  console.log(n * n)
})(2) // 4, but instead of just printing if we want to return and store the data, we do as shown below

let squaredNum = (function(n) {
  return n * n
})(10)

console.log(squaredNum)
```

# Objects

We can access values of object using two methods:

- using . followed by key name if the key-name is a one word
- using square bracket and a quote

```jsx
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName}${this.lastName}`
  },
  'phone number': '+3584545454545'
}

// accessing values using .
console.log(person.firstName)
console.log(person.lastName)
console.log(person.age)
console.log(person.location) // undefined

// value can be accessed using square bracket and key name
console.log(person['firstName'])
console.log(person['lastName'])
console.log(person['age'])
console.log(person['age'])
console.log(person['location']) // undefined

// for instance to access the phone number we only use the square bracket method
console.log(person['phone number'])
```

### Creating object methods

Now, the person object has getFullName properties. The getFullName is function inside the person object and we call it an object method. The *this* key word refers to the object itself. We can use the word *this* to access the values of different properties of the object. We can not use an arrow function as object method because the word this refers to the window inside an arrow function instead of the object itself. Example of object:

```jsx
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName} ${this.lastName}`
  }
}

console.log(person.getFullName())
// Asabeneh Yetayeh
```

### Setting new key for an object

An object is a mutable data structure and we can modify the content of an object after it gets created.

Setting a new keys in an object

```jsx
const person = {
  firstName: 'Asabeneh',
  lastName: 'Yetayeh',
  age: 250,
  country: 'Finland',
  city: 'Helsinki',
  skills: [
    'HTML',
    'CSS',
    'JavaScript',
    'React',
    'Node',
    'MongoDB',
    'Python',
    'D3.js'
  ],
  getFullName: function() {
    return `${this.firstName} ${this.lastName}`
  }
}
person.nationality = 'Ethiopian'
person.country = 'Finland'
person.title = 'teacher'
person.skills.push('Meteor')
person.skills.push('SasS')
person.isMarried = true

person.getPersonInfo = function() {
  let skillsWithoutLastSkill = this.skills
    .splice(0, this.skills.length - 1)
    .join(', ')
  let lastSkill = this.skills.splice(this.skills.length - 1)[0]

  let skills = `${skillsWithoutLastSkill}, and ${lastSkill}`
  let fullName = this.getFullName()
  let statement = `${fullName} is a ${this.title}.\nHe lives in ${this.country}.\nHe teaches ${skills}.`
  return statement
}
console.log(person)
console.log(person.getPersonInfo())
```

**Object Methods**

There are different methods to manipulate an object. Let us see some of the available methods.

*Object.assign*: To copy an object without modifying the original object

```jsx
const person = {
  firstName: 'Asabeneh',
  age: 250,
  country: 'Finland',
  city:'Helsinki',
  skills: ['HTML', 'CSS', 'JS'],
  title: 'teacher',
  address: {
    street: 'Heitamienkatu 16',
    pobox: 2002,
    city: 'Helsinki'
  },
  getPersonInfo: function() {
    return `I am ${this.firstName} and I live in ${this.city}, ${this.country}. I am ${this.age}.`
  }
}

//Object methods: Object.assign, Object.keys, Object.values, Object.entries
//hasOwnProperty

const copyPerson = Object.assign({}, person)
console.log(copyPerson)
```

*Object.keys*: To get the keys or properties of an object as an array

```jsx
const keys = Object.keys(copyPerson)
console.log(keys) //['firstName', 'age', 'country','city', 'skills','title', 'address', 'getPersonInfo']
const address = Object.keys(copyPerson.address)
console.log(address) //['street', 'pobox', 'city']
```

*Object.values*:To get values of an object as an array

```jsx
const values = Object.values(copyPerson)
console.log(values)
```

*Object.entries*:To get the keys and values in an array

```jsx
const entries = Object.entries(copyPerson)
console.log(entries)
```

*hasOwnProperty*: To check if a specific key or property exist in an object

```jsx
console.log(copyPerson.hasOwnProperty('name'))
console.log(copyPerson.hasOwnProperty('score'))
```

### Returning function

Higher order functions return function as a value

Let us see were we use call back functions. For instance the *forEach* method uses call back.

```jsx
const numbers = [1, 2, 3, 4, 5]
const sumArray = arr => {
  let sum = 0
  const callback = function(element) {
    sum += element
  }
  arr.forEach(callback)
  return sum

}
console.log(sumArray(numbers)) //15
//or 
const numbers = [1, 2, 3, 4]

const sumArray = arr => {
  let sum = 0
  arr.forEach(function(element) {
    sum += element
  })
  return sum

}
console.log(sumArray(numbers))
```

### Higher Order Functions

### Setting time

In JavaScript we can execute some activities in a certain interval of time or we can schedule(wait) for some time to execute some activities.

- setInterval
- setTimeout

### Setting Interval using a setInterval function

In JavaScript, we use setInterval higher order function to do some activity continuously with in some interval of time. The setInterval global method take a callback function and a duration as a parameter. The duration is in milliseconds and the callback will be always called in that interval of time.

```jsx
function sayHello() {
  console.log('Hello')
}
setInterval(sayHello, 1000) // it prints hello in every second, 1000ms is 1s
```

### Setting a time using a setTimeout

In JavaScript, we use setTimeout higher order function to execute some action at some time in the future. The setTimeout global method take a callback function and a duration as a parameter. The duration is in milliseconds and the callback wait for that amount of time.

```jsx
function sayHello() {
  console.log('Hello')
}
setTimeout(sayHello, 2000) // it prints hello after it waits for 2 seconds.
```

Functional Programming

*forEach*: Iterate an array elements. We use *forEach* only with arrays. It takes a callback function with elements, index parameter and array itself. The index and the array optional.

```jsx
arr.forEach(function (element, index, arr) {
  console.log(index, element, arr)
})
// The above code can be written using arrow function
arr.forEach((element, index, arr) => {
  console.log(index, element, arr)
})
// The above code can be written using arrow function and explicit return
arr.forEach((element, index, arr) => console.log(index, element, arr))
let sum = 0;
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(num => console.log(num))
console.log(sum)

const countries = ['Finland', 'Denmark', 'Sweden', 'Norway', 'Iceland']
countries.forEach((element) => console.log(element.toUpperCase()))
// FINLAND
// DENMARK
// SWEDEN
// NORWAY
// ICELAND
```

*map*: Iterate an array elements and modify the array elements. It takes a callback function with elements, index , array parameter and return a new array.

```jsx
const modifiedArray = arr.map(function (element, index, arr) {
  return element
})
/*Arrow function and explicit return
const modifiedArray = arr.map((element,index) => element);
*/
//Example
const numbers = [1, 2, 3, 4, 5]
const numbersSquare = numbers.map((num) => num * num)

console.log(numbersSquare)
```

*Filter*: Filter out items which full fill filtering conditions and return a new array.

```jsx
//Filter countries containing land
const countriesContainingLand = countries.filter((country) =>
  country.includes('land')
)
console.log(countriesContainingLand) //['Finland', 'Ireland']
const countriesEndsByia = countries.filter((country) => country.endsWith('ia'))
console.log(countriesEndsByia) //['Albania', 'Bolivia','Ethiopia']
```

*reduce*: Reduce takes a callback function. The call back function takes accumulator, current, and optional initial value as a parameter and returns a single value. It is a good practice to define an initial value for the accumulator value. If we do not specify this parameter, by default accumulator will get array `first value`. If our array is an *empty array*, then `Javascript` will throw an error.

```jsx
arr.reduce((acc, cur) => {
  // some operations goes here before returning a value
 return 
}, initialValue)

const numbers = [1, 2, 3, 4, 5]
const sum = numbers.reduce((acc, cur) => acc + cur, 0)

console.log(sum)
```

*every*: Check if all the elements are similar in one aspect. It returns boolean

```jsx
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const areAllStr = names.every((name) => typeof name === 'string') // Are all strings?

console.log(areAllStr) // true

const bools = [true, true, true, true]
const areAllTrue = bools.every((b) => b === true) // Are all true? 

console.log(areAllTrue) // true
```

*find*: Return the first element which satisfies the condition

```jsx
const ages = [24, 22, 25, 32, 35, 18]
const age = ages.find((age) => age < 20)

console.log(age) //18

const scores = [
  { name: 'Asabeneh', score: 95 },
  { name: 'Mathias', score: 80 },
  { name: 'Elias', score: 50 },
  { name: 'Martha', score: 85 },
  { name: 'John', score: 100 },
]

const score = scores.find((user) => user.score > 80)
console.log(score) //{ name: "Asabeneh", score: 95 }
```

*findIndex*: Return the position of the first element which satisfies the condition

```jsx
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const ages = [24, 22, 25, 32, 35, 18]

const result = names.findIndex((name) => name.length > 7)
console.log(result) // 0

const age = ages.findIndex((age) => age < 20)
console.log(age) // 5
```

*some*: Check if some of the elements are similar in one aspect. It returns boolean

```jsx
const names = ['Asabeneh', 'Mathias', 'Elias', 'Brook']
const bools = [true, true, true, true]

const areSomeTrue = bools.some((b) =>  b === true)

console.log(areSomeTrue) //true

const areAllStr = names.some((name) => typeof name === 'number') // Are all strings ?
console.log(areAllStr) // false
```

*sort*: The sort methods arranges the array elements either ascending or descending order. By default, the ***sort()*** method sorts values as strings.This works well for string array items but not for numbers. If number values are sorted as strings and it give us wrong result. Sort method modify the original array. It is recommended to copy the original data before you start using *sort* method.

### Sorting string values

```jsx
const products = ['Milk', 'Coffee', 'Sugar', 'Honey', 'Apple', 'Carrot']
console.log(products.sort()) // ['Apple', 'Carrot', 'Coffee', 'Honey', 'Milk', 'Sugar']
//Now the original products array  is also sorted
```

### Sorting Numeric values

As you can see in the example below, 100 came first after sorted in ascending order. Sort converts items to string , since '100' and other numbers compared, 1 which the beginning of the string '100' became the smallest. To avoid this, we use a compare call back function inside the sort method, which return a negative, zero or positive.

```jsx
const numbers = [9.81, 3.14, 100, 37]
// Using sort method to sort number items provide a wrong result. see below
console.log(numbers.sort()) //[100, 3.14, 37, 9.81]
numbers.sort(function (a, b) {
  return a - b
})

console.log(numbers) // [3.14, 9.81, 37, 100]

numbers.sort(function (a, b) {
  return b - a
})
console.log(numbers) //[100, 37, 9.81, 3.14]
```

### Sorting Object Arrays

Whenever we sort objects in an array, we use the object key to compare. Let us see the example below.

```jsx
objArr.sort(function (a, b) {
  if (a.key < b.key) return -1
  if (a.key > b.key) return 1
  return 0
})

// or

objArr.sort(function (a, b) {
  if (a['key'] < b['key']) return -1
  if (a['key'] > b['key']) return 1
  return 0
})

const users = [
  { name: 'Asabeneh', age: 150 },
  { name: 'Brook', age: 50 },
  { name: 'Eyob', age: 100 },
  { name: 'Elias', age: 22 },
]
users.sort((a, b) => {
  if (a.age < b.age) return -1
  if (a.age > b.age) return 1
  return 0
})
console.log(users) // sorted ascending
// [{…}, {…}, {…}, {…}]
```