# ECMAScript 6 Overview in simple terms
Here is **ECMAScript 6 Overview in simple terms**.  
And let me mention this overview is heavily influenced by [es6features repo](https://github.com/lukehoban/es6features#readme), thanks to [Luke Hoban](https://twitter.com/lukehoban) for such a great work. And [Axel Rauschmayer](https://twitter.com/rauschma) for his awesome [comprehensive book](http://exploringjs.com/es6/).

At first when I myself heard about ES6, I had a hard time to digest it and learn about its fundamentals. I have gone through that path, but you don't have to!  
So I here is a brief introduction to ES6 and its new features, all explained in simple terms for dummies like me :smile:




# Introduction
ECMAScript 6, also known as ECMAScript 2015 is the next version of Javascript and became a standard in June 2015.  
ES6 is a significant update to the language since ES5 back in 2009.

**Is it a brand new language?**  
Nope! It's the same old Javascript as we know but with a more beautiful syntax and more features.

**Does it mean my current Javascript codes are not going to work soon?**  
Nope! That would break the web! Javascript always be backwards-compatible. i.e new features will be added to it and its existing features will become more powerful. This is called [One JavaScript](http://exploringjs.com/es6/ch_one-javascript.html#ch_one-jacvascript).

**What is its goal?**  
Generally be a better language! It lets us code faster, safer and more efficient.

**What is after ES6?**  
ECMAScript 7 is on its way... TC39 has plans to release a new version of ECMAScript every year. i.e from now on, ECMAScript versions will be relatively small upgrades. So everything you learn about ES6 today will be useful when you wanna start learning ES7 and later versions.




# Installation
This section is for those web designers who are not still so familiar with the command line tools. So if you already know how to install [node.js](https://nodejs.org/en/) and [Babeljs](https://babeljs.io/), the ES6 compiler, you can skip this section.

**Do I need to install something?**  
Yes! As ES6 is new, most of its features are not supported in browsers just yet. But there's no need to wait! We can start coding in ES6 today with the help of [node.js](https://nodejs.org/en/) and [Babeljs](https://babeljs.io/), the ES6 compiler!  
[Babeljs](https://babeljs.io/) will transform our ES6 syntax into ES5, so that the current browsers can read our code as if we've written it all in ES5 from the beginning. Isn't that cool? Yes it is! So let's just see how to install all of this and get started.

1. First download and install [node.js](https://nodejs.org/en/) on your machine.

2. Now open your Terminal / Command Prompt and type: `npm install --global babel`.  
Hit Enter on your keyboard to run the command and install [Babeljs](https://babeljs.io/) the very first time on your machine.  
**Babeljs** is the ES6 compiler.

3. Run: `npm install -g browserify`.  
To install [Browserify](http://browserify.org/) too if you like to use ES6 module loader syntax.  
**Browserify** lets you write modular JavaScript codes in separate Javascript files and then bundle them all up and feed your html page with only one bundled Javascript file.

4. Run: `cd path/to/my/project` to change directory to your project directory.

4. Run: `babel src --out-dir build`. This command transforms any .js files in 'src' folder from ES6 to ES5 syntax and puts the new transformed files into 'build' folder.  
Now you're good to go! You can feed you html with the new transformed .js files and the browser should run your codes just fine as always :thumbsup:




# ECMAScript 6 Features
- [string + array + object APIs](#string--array--object-apis)
- [Symbols](#symbols)
- [Template Strings](#template-strings)
- [Let + Const](#let--const)
- [Destructuring](#destructuring)
- [Default + Rest + Spread](#default--rest--spread)
- [Arrows and Lexical this](#arrows-and-lexical-this)
- [Classes](#classes)
- [Enhanced Object Literals](#enhanced-object-literals)
- [Iterators + for..of](#iterators--forof)
- [Modules](#modules)
- [Map + Set + WeakMap + WeakSet](#map--set--weakmap--weakset)
- [Promises](#promises)




## string + array + object APIs
In ES6 we have many new library additions, including core Math libraries, Array conversion helpers and `Object.assign()` for copying.

```javascript
'hello'.startsWith('hell'); // true
'hello'.endsWith('ello'); // true
'hello'.includes('ell'); // true
'doo '.repeat(3); // 'doo doo doo '

Array.from(document.querySelectorAll("*")); // Returns a real Array
Array.of(1, 2, 3); // Similar to new Array(...), but without special one-arg behavior
[0, 0, 0].fill(7, 1); // [0,7,7]
[1, 2, 3].findIndex(x => x == 2); // 1
['a', 'b', 'c'].entries(); // iterator [0, 'a'], [1,'b'], [2,'c']
['a', 'b', 'c'].keys(); // iterator 0, 1, 2
['a', 'b', 'c'].values(); // iterator 'a', 'b', 'c'

Object.assign(Point, { origin: new Point(0,0) }); // Assigns new parameters for 'Point' object.
```




## Symbols
Symbol is a new primitive type in ECMAScript 6. They are tokens that serve as unique IDs. You create symbols via the factory function `Symbol()`.
They are always unique. Each time we create a new symbol, we're actually creating a new unique identifier which never clashes with anything else in our project. So that's why it makes them useful in some cases. For example when we wanna define a constant!

In ES5 we used to use two different unique Strings to define constants... We should have to rely on a String! But as we know String is not something unique! We may accidentally change them or type them in different places and that will break our constant behavior. But now, we can easily use `Symbol()` when defining our constant variables and we're sure that each time we call `Symbol()` it's an unique identifier in our project that never clashes. Cool!

```javascript
const COLOR_RED    = Symbol();
const COLOR_ORANGE = Symbol();

console.log( 'each Symbol() is always unique: ', Symbol() === Symbol() ); // Yes, it returns false.

// They can also help us create unique dynamic methods for our objects and classes.
const MY_KEY = Symbol();
let obj0 = {};

obj0[MY_KEY] = 123;
console.log('my dynamic object method: ', obj0[MY_KEY]); // 123
```




## Template Strings
Template strings provide syntactic sugar for constructing strings.
The literal itself is delimited by backticks, the interpolated expressions inside the literal are delimited by `${var}`. Template literals always produce strings.

```javascript
// Multiline strings
const HTML5_SKELETON = `
  <!doctype html>
  <html>
  <head>
    <meta charset="UTF-8">
    <title></title>
  </head>
  <body>
  </body>
  </html>`;

// Interpolate variable bindings
let name = 'Bob', time = 'today';
let greeting = `Hello ${name}, how are you ${time}?`;

// Tagged templates
let str = String.raw`This is a text
with multiple lines.
Escapes are not interpreted,
\n is not a newline.`;
```




## Let + Const
ES6 provides two new ways to declare variables: `let` and `const`, which mostly replace the ES5 way of declaring variables, `var`.
`let` works similarly to `var`, but the variable it declares is block-scoped, it only exists within the current block. `var` is function-scoped.

```javascript
function func(randomize) {
  if (randomize) {
    let x = Math.random(); // NOTE: x exists ONLY in this if statement
    var y = Math.random(); // NOTE: But y exists in the whole function.
  }

  // Block scoping means that we can shadow variables within a function
  // which means the x variable here has nothing to do with the above one that
  // we've defined inside of the if statement.
  let x = 5;

  return y;
}
```

`const` works like `let`, but the variable you declare must be immediately initialized, with a value that cannot be changed afterwards.

```javascript
const a = 123;
```

**NOTE:** `const` pitfall! `const` only means that the variable itself is immutable. So if the variable is an object, the properties of that object are still mutable! So the solution to that is the Javascript `freeze()` method.

```javascript
const freezObj = Object.freeze({});
```




## Destructuring
Destructuring allows binding using pattern matching, with support for matching arrays and objects.  
Destructuring is actually a convenient way to extract values from data stored in (possibly nested) objects and Arrays.

```javascript
// Let's understand destructuring better...
let obj1 = {}; obj1.first = 'Jane'; obj1.last = 'Doe'; // This is how we can construct data
let f1 = obj1.first; let l1 = obj1.last; // And this is how we can extract data out of it. right?

// Now for constructing we could also use object literal:
let obj2 = { first: 'Jane', last: 'Doe' };

// destructuring is also similar to it! it's just the opposite of
// constructing. It lets us to extract data easier.
let { first: f2, last: l2 } = obj2; // Now we have f2 and l2 variables available.

// Destructing works with arrays too
let [x1, y1] = ['a', 'b']; // x1 = 'a'; y1 = 'b'

// Computed property keys
const FOO = 'foo';
let { [FOO]: f4 } = { foo: 123 }; // f4 = 123
```

We can also use a pattern for our destruct.  
**NOTE:** It's important to mention that when we destruct, we just need to mention the variable that we like to extract out of the array or object. That's it! e.g. In the following example we just like to extract 'foo' from 'obj3' and save it as 'f3' variable. So we just create the pattern to access 'foo' in the object and mention only that, because that's all that we need.

```javascript
let obj3 = { a: [{ foo: 123, bar: 'abc' }, {}], b: true };
let { a: [{foo: f3}] } = obj3; // f3 = 123
```

We can also have default values:

```javascript
let [x3 = 3, y3] = []; // x3 = 3; y3 = undefined
let {foo: x4 = 3, bar: y4} = {}; // x4 = 3; y4 = undefined

// Of course default values can be functions too:
function log() { return 'YES' }
let [aa=log()] = [];

// Default values can refer to other variables in the pattern.
// However order of them matters! The following produces referenceError:
// let [x=y, y=3] = [];
// Why? because y is not defined yet when x says that my default value is y!
let [xx=3, yy=xx] = [];
```

It can also be used in for-of.  
**NOTE:** In ES6 we have a new kind of loop which is called for-of. Before ES5, when we liked to loop through an array we simply used for, in ES5 array had a method called `forEach()` which lets us to do that. Now we have for-of which is easier to use.

```javascript
// a for-of example and a loop through the array
let arr = ['a', 'b', 'c'];
for ( let item of arr ) {
  //console.log(item);
}

// Via the new Array method entries() and destructuring, we can get both index
// and value of each array element.
for ( let [index, item] of arr.entries() ) {
  //console.log(index + '. ' + item);
}

// We can also do it like this too
for ( {name: n, age: a} of arr ) {
  // do something
}

// Array patterns work with iterables
let [x2,...y2] = 'abc'; // x2='a'; y2=['b', 'c']; 'rest' operator
let [,,x] = ['a', 'b', 'c', 'd']; // x = 'c'; We can also use 'Elision' to skip elements
```

Alright, so in what other situations destructuring is useful?

```javascript
// To split an Array
let [first1, ...rest1] = ['a', 'b', 'c'];

// Multiple return values
function testing() {
  return {element: undefined, index: -1};
}
```




## Default + Rest + Spread
ES6 provides a new and better way of defining default values for parameters in our functions:

```javascript
// In ES5, you specify default values for parameters like this:
function foo(x, y) {
  x = x || 0; y = y || 0;

  // do something
}

// ES6 has nicer syntax:
function foo(x=0, y=0) {
  // y is 0 if not passed (or passed as undefined)
}

// In ES6, you can use destructuring in parameter definitions and the code
// becomes simpler:
function selectEntries1({ start=0, end=-1, step=1 } = {}) {
  // do something
}

// Above function is equivalent to this one.
function selectEntries2(options) {
  options = options || {};
  var start = options.start || 0;
  var end = options.end || -1;
  var step = options.step || 1;

  // do something
}
```

ES6 also lets us have rest parameters:

```javascript
function format(pattern, ...params) {
  return params;
}

format('a', 'b', 'c'); // ['b', 'c'] // params will be an array


// In ES6 we have '...' which is the spread operator.
// In ES5, this is how we used to turn an array into parameters: We used apply()
Math.max.apply(null, [-1, 5, 11, 3]);

// Now we can simply do this! As spread operator will extract its items and
// turns them into parameters
Math.max(...[-1, 5, 11, 3]);
```




## Arrows and Lexical this
Arrows are a function shorthand using the `=>` syntax. But unlike functions, arrows share the same lexical this as their surrounding code.

Expression bodies:
```javascript
var evens = [0,2,4];

// These two are equivalent:
var odds = evens.map(v => v + 1);
var odds = evens.map(function(v){ return v + 1; });

// These two are equivalent:
var nums = evens.map((v, i) => v + i);
var nums = evens.map(function(v, i){ return v + i; });
```

Statement bodies:

```javascript
var fives = [];
nums.forEach(v => {
  // See? for more complex statement we can put everything inside {} just like
  // how we do it with normal functions.
  if (v % 5 === 0) fives.push(v);
});
```

Lexical this:

```javascript
var bob = {
  _name: 'Bob',
  _friends: [],
  printFriends() {
    this._friends.forEach(f =>
      // 'this' keyword simply refers to the 'bob' Object in our closure not
      // the closure itself.
      console.log(this._name + ' knows ' + f));
  },
};

class UiComponent {
  constructor() {
    let button = document.getElementById('myButton');
    button.addEventListener('click', () => {
      // By using arrow functions, 'this' keyword simply refers to our
      // own 'UiComponent' class not the closure. This is awesome in ES6.
      // We no more need to use bind() in such cases...
      this.handleClick();
    });
  }

  handleClick() {
    console.log('CLICK');
  }
}
```




## Classes
ES2015 classes are a simple sugar over the prototype-based OO pattern.

```javascript
class Person {
  // constructor will be called automatically when the class is initialized.
  constructor(fname, lname) {
    // A class body can only contain methods, but not data properties.
    // So that's why we should set our properties here in the constructor.
    this.fname = fname;
    this.lname = lname;
  }
}


class Employee extends Person {
  constructor(fname, lname, name = 'no name') {
    // In a derived class(extended class), you must call super() before
    // you can use 'this' keyword to define a property. e.g. this.name. Also
    // if we don't use super() we get ReferenceError when we're trying to
    // initialize the sub class.
    super(fname, lname);

    if (name === 'no name') this.name = this.fname + ' ' + this.lname;
  }

  setJob(title) {
    this.job = title;
  }

  static greeting() {
    return 'Hello World!';
  }

  // At the time being, classes only let us create static methods, but not
  // static data properties. But we can create a static getter instead.
  static get JOHN() {
    return new Employee('John', 'Doe');
  }

  // Getters and setters
  get prop() {
    return this.prop;
  }

  set prop(value) {
    this.prop = value;
  }

  // Computed method names
  ['my'+'Method']() {
    // do something
  }
}

var john = new Employee('John', 'Doe');
john.setJob('Designer');

console.log('Class-> Employee class, just initialized: ', Employee.JOHN);
console.log('Class-> Employee class, greeting: ', Employee.greeting());
console.log('Class-> John: ', john);
```




## Enhanced Object Literals
Object literals are extended to support setting the prototype at construction, shorthand for `foo: foo` assignments, defining methods and making super calls.

```javascript
let first = 'Jane';
let last = 'Doe';
let propKey = 'foo';

let obj = {

  // Method definition
  myMethod(x, y) {
    // do something
  },

  // Property value shorthands. The following:
  // let obj = { first, last };
  // is as same as:
  // let obj = { first: first, last: last };
  first,
  last,

  // Computed property keys
  [propKey]: true,
  ['b'+'ar']: 123,

  ['h'+'ello']() {
    // console.log(obj.hello());
    return 'hi';
  },

  // Setters & Getters
  get sth() {
    console.log('Object Literal-> ', 'sth getter');
    return 123;
  },
  set sth(value) {
    console.log('Object Literal-> ', 'sth setter');
    // Return value is ignored
  }
};

// New methods in Object
// The most important new method of Object is assign().
Object.assign(obj, { bar: true }); // it assigns new parameters for our object.
console.log('Object Literal-> ', JSON.stringify(obj)); // {"first":"Jane","last":"Doe","foo":true,"bar":true,"sth":123}
```




## Iterators + for..of
ECMAScript 6 introduces a new interface for iteration, iterable. (Iterable actually means anything that can be repeated)
Arrays, Strings, Maps, Sets, DOM data structures (work in progress) are all iterable.

So in simple terms, iterator is a structure, that each time it is called, it will return the next results in a sequence. e.g. `entries()` method of an array. `arr.entries()` each time we call it, it returns the next item in an array.

**NOTE:** Some iterable structures are not something new, such as a for loop... But here I just wanna explain what iteration protocol is, make it more clear and also introduce the new ES6 features about it :smile:

Language constructs that access data via the iteration protocol:

```javascript
// Destructuring actually is doing an iterable job(a repeated job, multiple job)
// to extract data out of the array. It should be repeated a job on a specific
// pattern to accomplish this.
let [a,b] = new Set(['a', 'b', 'c']);

// for-of is obviously iterable.
for (let x of ['a', 'b', 'c']) {
  console.log('for-of iteration-> ', x);
}

let arr2 = Array.from(new Set(['a', 'b', 'c'])); // Array.from()
let arr3 = [...new Set(['a', 'b', 'c'])]; // Spread operator (...)
let map0 = new Map([[false, 'no'], [true, 'yes']]); // Constructors of Maps
let set0 = new Set(['a', 'b', 'c']); // Constructors of Sets
// Promise.all(iterableOverPromises).then(); // Promise.all()
// Promise.race(iterableOverPromises).then(); // Promise.race()

// yield* an Iterable
// NOTE: 'yield' is related to Generators when we wanna create a nGenerator
// (Generator is a new feature in ES6)
```

Let's use iteration:

```javascript
let arr4 = ['a', 'b'];
let iter = arr4[Symbol.iterator](); // we create an iterator via the method whose key is Symbol.iterator

// Then we call the iterator’s method next() repeatedly to retrieve the items
// “inside” the Array:
iter.next(); // returns an object: { value: 'a', done: false }
iter.next(); // { value: 'b', done: false }
iter.next(); // { value: undefined, done: true }
// NOTE: The boolean property 'done' indicates when the end of the sequence of
// items has been reached.
```

See? It's somehow like how a loop works... It each time returns something new.  
**NOTE:** A key characteristic of iteration protocol is that it is sequential: The iterator returns values one at a time. That means that if an iterable data structure is non-linear (such as a tree), iteration will linearize it.

Now let's use Symbols in an Object that we like it to act like an iterator:

```javascript
let iterableObject = {
  // Our object must have a dynamic method which is actually using Symbol
  // primitive. As we know Symbols are always unique and that's one of their
  // use cases, to create a unique dynamic method for our classes.
  [Symbol.iterator]() {

    let data = ['hello', 'world'];
    let index = 0;

    // Now our iterator method must return an object which has next() method.
    return {
      // Here is our iterator logic! In our example here, we check 'index'
      // variable and act accordingly based on its value.
      next() {
        if (index < data.length) {
          return { value: data[index++] };
        } else {
          return { done: true };
        }
      }
    };
  }
};

// Now that's how we can use our iterable object.
for (let x of iterableObject) {
  // x is different each time. The first time in the loop it's 'hello' and the
  // second time it's 'world'.
  console.log('iterableObject-> ', x);
}
```

**NOTE:** As we know have used a symbol as the key of the method in our object. This unique marker makes the object iterable and enables us to use the for-of loop. Cool! Now we have created a custom iterable object(or class) in our code that this enables us to make iterable codes easier in our projects.

If the above iterable object was a real sample, it could be really helpful in a project. There was no need for me to put all of my logic in the for-of loop to do a iterable job, I could easily create a meaningful iterable class and inside of that put my logic, then I could use my class in a for-of loop in different places and easily do my iterable job. Easy! This would make my code cleaner and dry.




## Modules
Language-level support for modules for component definition. Codifies patterns from popular JavaScript module loaders (AMD, CommonJS).
In ECMAScript 6, modules are stored in files. There is exactly one module per file and one file per module.

```javascript
// lib/math.js
// We simply export any variable or function in our file.
export function sum(x, y) { return x + y; }
export var pi = 3.141593;

// app.js
// Import anything that we like in an other file.
import * as math from "lib/math";

// Now we can access all the things that we've exported in math.js like this:
alert("2π = " + math.sum(math.pi, math.pi));

// otherApp.js
// We can also import each functionality explicitly instead of importing them
// 'as' one general name.
import {sum, pi} from "lib/math";
alert("2π = " + sum(pi, pi));
```

There can also be a **single default export**. Modules that only export single values are very popular in the Node.js community. We can simply have a module that export only one class or function.

```javascript
// myFunc.js
// Of course our function can have a name too: export default function foo() {}
export default function() { }
import myFunc from 'myFunc';
myFunc();

// MyClass.js
// Of course our class can have a name too: export default class Bar {}
export default class { }
import MyClass from 'MyClass';
let inst = new MyClass();
```

As we know in ECMAScript 5 code that doesn’t use modules via libraries (such as RequireJS, browserify or webpack), the revealing module pattern is popular, and based on an IIFE. Its advantage is that it clearly separates between what is public and what is private.

```javascript
// How to create properly a module in ES5:
// my_module.js

var my_module = (function () {
  // Module-private variable:
  var countInvocations = 0;

  function myFunc(x) {
    countInvocations++;
  }

  // Exported by module:
  return {
    myFunc: myFunc
  };
}());

// This module pattern produces a global variable and is used as follows
my_module.myFunc(33);
```

In ECMAScript 6, modules are built in, which is why the barrier to adopting them is low:

```javascript
// How to create properly a module in ES6:
// my_module.js

// Module-private variable:
let countInvocations = 0;

// export the module
export function myFunc(x) {
  countInvocations++;
}
```




## Map + Set + WeakMap + WeakSet
Efficient data structures for common algorithms.
The following four data structures are new in ECMAScript 6: Map, WeakMap, Set and WeakSet.

**Maps**: What was missing in ES5 was a data structure for mapping values to values. The Map data structure in ECMAScript 6 lets you use arbitrary values as keys and is highly welcome.

```javascript
// Create an empty Map
let map = new Map();

// We can also fill out the map right at the moment that we're initializing it.
let map = new Map([ [ 1, 'one' ], [ 2, 'two' ] ]);

// The set() method of Map is chain-able. So we can fill out the map like this too.
let map = new Map().set(1, 'one').set(2, 'two');

// Any value can be a key, even an object!
// We can also set an OR operator if what we're going to get was undefined for
// some reasons: map.get(KEY) || 0;
const KEY = {};
map.set(KEY, 123);
map.get(KEY); // 123
map.has(KEY); // true
map.delete(KEY); // true
map.size; // 1
map.clear(); // To empty the map

// keys() returns an iterable over the keys in the Map.We can use it in a
// for-of loop for instance.
map.keys();

// values() returns an iterable over the values in the Map.
map.values();

// entries() returns the entries of the Map as an iterable over [key,value]
// pairs (Arrays).
// NOTE: We can use destructuring in a for-of loop to access both, keys and
// values, just like what we can do with the entries() method of an array.
map.entries();
```

**WeakMap**: It's a Map that doesn’t prevent its keys from being garbage-collected. That means that you can associate data with objects without having to worry about memory leaks. A WeakMap is a data structure whose keys must be objects and whose values can be arbitrary values. It has the same API as Map, with one significant difference: you can’t iterate over the contents – neither the keys, nor the values, nor the entries. You can’t clear a WeakMap, either.

**Sets**: ECMAScript 5 doesn’t have a Set data structure, either. There are two possible work-arounds:
1. Use the keys of an object to store the elements of a set of strings.
2. Store (arbitrary) set elements in an Array: Check whether it contains an element via `indexOf()`, remove elements via `filter()`, etc. This is not a very fast solution, but it’s easy to implement. One issue to be aware of is that `indexOf()` can’t find the value NaN.

ECMAScript 6 has the data structure Set which works for arbitrary values, is fast and handles NaN correctly.

```javascript
let set = new Set();

// We can also fill out the set right at the moment that we're initializing it.
let set = new Set(['red', 'green', 'blue']);

// The add() method of Set is chain-able. So we can fill out the set like this too.
let set = new Set().add('red').add('green').add('blue');

set.add('red');
set.has('red'); // true
set.delete('red'); // true
set.size; // 1
set.clear(); // To empty the set
```

**WeakSet**: It's a Set that doesn’t prevent its elements from being garbage-collected.

**NOTE:** Why do Maps and Sets have the property 'size' and not 'length'(like Arrays)? The reason for this difference is that length is for sequences, data structures that are indexable – like Arrays. size is for collections that are primarily unordered – like Maps and Sets.




## Promises
Promises are a library for asynchronous programming.
We are already familiar with promise pattern in Javascript. But in simple terms, it actually makes asynchronous behavior easier. We can set a new promise and inside of it code any Asynchronous Behavior. Like an ajax call or timeout or etc..

```javascript
function getJSON (url) {
  let promise = new Promise(function (resolve, reject) {
    // Ok, now here in the promise, we simply write our asynchronous behavior.
    // e.g. an ajax call.

    // resolve(value); // if our ajax call succeses, we call resolve() and pass
    // the necessary argument to it. What is the argument? Well, we ourselves
    // decide what is should be according to our asynchronous job. e.g. for an
    // ajax job, the jquery's ajax() method calls our own seccessful function
    // when it loads our file successfully. It also pass it an argument which
    // is actually the data that it loaded. So data is our argument here.

    // reject(error); // if it fails, we call reject() and pass the necessary
    // argument to it.
  });

  return promise; // remember to return the promise.
}

// now this is how we use our promise. its then() method will be called when
// our promise is resolved, catch() will be called when it has been rejected.
getJSON('promised.json')
.then(value => {})
.catch(error => {});

// NOTE: There's also an optional second argument for the then() method, which
// is the error actually. This code is equivalent to the above one. We can use
// any one of them that we wish.
getJSON('promised.json')
.then(value => {}, error => {});

// We can also chain our promise. then() method returns a new Promise Q.
getJSON('promised.json')
.then(value1 => 123) // whatever the first then() returns, is the argument of the next then()
.then(value2 => {}); // so 'value2' is equal to 123.

// In chaining, if any one of our promises fail, we can still continue chaining
// by returning a default value in the catch() method of the one that failed.
getJSON('promised.json')
.catch(() => 'default value') // whatever the first then() returns, is the argument of the next then()
.then(value2 => {}); // so 'value2' is equal to 'default value'.

// We can also manually throw an exception and it will be passed on to the next
// error handler.
getJSON('promised.json')
.then(value => {throw new Error();})
.then(err => {});


// with chain-able promises, as we know we can easily do something like this
// and have nested promises:
asyncFunc1()
.then(function (value1) {
  asyncFunc2()
    .then(function (value2) {
      // do something else...
  });
});

// or make it flat, and do it like this:
asyncFunc1()
.then(function (value1) {
  return asyncFunc2();
})
.then(function (value2) {
  // do something else...
});
```




# What's next?
This was just a brief introduction to get you familiar with ES6 and its new features. Now you wanna learn more, right? So prepare yourself for lots of awesomeness! Here are some great resources that help you learn more:

* [The Command Line for Web Design](http://webdesign.tutsplus.com/series/the-command-line-for-web-design--cms-777),
This tutorial series has nothing to do with ES6 directly! But it's a great start for those web designers who are not familiar with command line tools yet but they should be!

* [es6features repo](https://github.com/lukehoban/es6features#readme) explained ES6 features in more details.

* [Babeljs](https://babeljs.io/) Javascript compiler.

* [Javascript Style Guide](Airbnb JavaScript Style Guide) teaches a mostly reasonable approach to JavaScript.

* [Exploring ES6 Book](http://exploringjs.com/es6/) is a comprehensive book about ES6 written by [Axel Rauschmayer](https://twitter.com/rauschma).

* [List of more resources](https://github.com/ericdouglas/ES6-Learning) is here to get you started even faster.
