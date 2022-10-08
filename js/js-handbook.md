# JS Handbook

#### Modern JS

**‘use strict’**

The directive looks like a string: `"use strict"`or `'use strict'`. When it is located at the top of a script, the whole script works the “modern” way.

Key thing to remember here is always use “use strict” on top of the script you can’t use that in middle of any script

How to run use strict on developer console

```jsx
(function() {
  'use strict';

  // ...your code here...
})()
```

***

#### Variables

We can declare variables to store data by using the `var`, `let`, or `const` keywords.

* `let` – is a modern variable declaration.
* `var` – is an old-school variable declaration. Normally we don’t use it at all, but we’ll cover subtle differences from `let` in the chapter [The old "var"](https://javascript.info/var), just in case you need them.
* `const` – is like `let`, but the value of the variable can’t be changed.

***

#### Data type

* Number
  * 12
  * 12.345
  * NaN
  * Infinity
*   Bigint

    * In JavaScript, the “number” type cannot safely represent integer values larger than  `(2^53-1)` (that’s `9007199254740991`), or less than `-(2^53-1)`for negatives.
    * To be really precise, the “number” type can store larger integers (up to `1.7976931348623157 * 10^308`), but outside of the safe integer range `±(2^53-1)` there’ll be a precision error, because not all digits fit into the fixed 64-bit storage. So an “approximate” value may be stored.
    * A `BigInt` value is created by appending `n` to the end of an integer:

    ```jsx
    // the "n" at the end means it's a BigInt
    const bigInt = 1234567890123456789012345678901234567890n
    ``
    ```
*   String

    * Inside quotes(” or ‘) everything treated as string
    * Backtick ( \` ) is also used in some case it is mostly use to create template string like

    ```jsx
    // Here is the example of template string
    const title = "Layek"

    const name = `Sourav ${title}` // name = `Sourav Layek`

    const c = 10

    const count  = `Count: ${c}`  // count = `Count: 10`
    ```
* Boolean
  * Boolean is a logical type
* null
  * null is a special data type it is a reference to a non existing object, it mostly use to show empty or nothing.
* undefined
  * The meaning of undefined is “value is not assigned”.
*   Object and symbol

    * The object type is special.
    * All other types are called “primitive” because their values can contain only a single thing (be it a string or a number or whatever). In contrast, objects are used to store collections of data and more complex entities.
    * Being that important, objects deserve a special treatment. We’ll deal with them later in the chapter Objects, after we learn more about primitives.
    * The symbol type is used to create unique identifiers for objects. We have to mention it here for the sake of completeness, but also postpone the details till we know objects.

    ```jsx
    typeof undefined // "undefined"

    typeof 0 // "number"

    typeof 10n // "bigint"

    typeof true // "boolean"

    typeof "foo" // "string"

    typeof Symbol("id") // "symbol"

    typeof Math // "object"  (1)

    typeof null // "object"  (2)

    typeof alert // "function"  (3)
    ```

    * The last three lines may need additional explanation:
      * `Math` is a built-in object that provides mathematical operations. We will learn it in the chapter [Numbers](https://javascript.info/number). Here, it serves just as an example of an object.
      * The result of `typeof null` is `"object"`. That’s an officially recognized error in `typeof`, coming from very early days of JavaScript and kept for compatibility. Definitely, `null` is not an object. It is a special value with a separate type of its own. The behavior of `typeof` is wrong here.
      * The result of `typeof alert` is `"function"`, because `alert` is a function. We’ll study functions in the next chapters where we’ll also see that there’s no special “function” type in JavaScript. Functions belong to the object type. But `typeof` treats them differently, returning `"function"`. That also comes from the early days of JavaScript. Technically, such behavior isn’t correct, but can be convenient in practice.
*   **Summary**

    There are 8 basic data types in JavaScript.

    * Seven primitive data types:
      * `number` for numbers of any kind: integer or floating-point, integers are limited by `±(2531)`.
      * `bigint` for integer numbers of arbitrary length.
      * `string` for strings. A string may have zero or more characters, there’s no separate single-character type.
      * `boolean` for `true`/`false`.
      * `null` for unknown values – a standalone type that has a single value `null`.
      * `undefined` for unassigned values – a standalone type that has a single value `undefined`.
      * `symbol` for unique identifiers.
    * And one non-primitive data type:
      * `object` for more complex data structures.

    The `typeof` operator allows us to see which type is stored in a variable.

    * Usually used as `typeof x`, but `typeof(x)` is also possible.
    * Returns a string with the name of the type, like `"string"`.
    * For `null` returns `"object"` – this is an error in the language, it’s not actually an object.

***

#### Type conversion

The three most widely used type conversions are to string, to number, and to boolean.

String Conversion – Occurs when we output something. Can be performed with String(value). The conversion to string is usually obvious for primitive values.

Numeric Conversion – Occurs in math operations. Can be performed with Number(value).

The conversion follows the rules:

| Value        | Becomes                                                                                                             |
| ------------ | ------------------------------------------------------------------------------------------------------------------- |
| undefined    | NaN                                                                                                                 |
| null         | 0                                                                                                                   |
| true / false | 1 / 0                                                                                                               |
| string       | The string is read “as is”, whitespaces from both sides are ignored. An empty string becomes 0. An error gives NaN. |

Boolean Conversion – Occurs in logical operations. Can be performed with Boolean(value).

Follows the rules:

| Value                       | Becomes |
| --------------------------- | ------- |
| 0, null, undefined, NaN, "" | false   |
| any other value             | true    |

Most of these rules are easy to understand and memorize. The notable exceptions where people usually make mistakes are:

undefined is NaN as a number, not 0. "0" and space-only strings like " " are true as a boolean.

***

#### Operators

In logical operator the or ( || ) returns the first truthy value

```jsx
alert( 1 || 0 ); // 1 (1 is truthy)

alert( null || 1 ); // 1 (1 is the first truthy value)
alert( null || 0 || 1 ); // 1 (the first truthy value)

alert( undefined || null || 0 ); // 0 (all falsy, returns the last value)
```

and finds the first falsy value

```jsx
// if the first operand is truthy,
// AND returns the second operand:
alert( 1 && 0 ); // 0
alert( 1 && 5 ); // 5

// if the first operand is falsy,
// AND returns it. The second operand is ignored
alert( null && 5 ); // null
alert( 0 && "no matter what" ); // 0
```

*   The nullish coalescing operator `??` provides a short way to choose the first “defined” value from a list.

    It’s used to assign default values to variables:

    `// set height=100, if height is null or undefined height = height ?? 100;`
* The operator `??` has a very low precedence, only a bit higher than `?` and `=`, so consider adding parentheses when using it in an expression.
* It’s forbidden to use it with `||` or `&&` without explicit parentheses.

***

#### Function

* In function default parameter if any parameter isn’t given then we can call a function to handle that here is the example

```jsx
function showMessage(from, text = anotherFunction()) {
  // anotherFunction() only executed if no text given
  // its result becomes the value of text
}
```

A function declaration looks like this:

```jsx
function name(parameters, delimited, by, comma) {
  /* code */
}
```

* Values passed to a function as parameters are copied to its local variables.
* A function may access outer variables. But it works only from inside out. The code outside of the function doesn’t see its local variables.
* A function can return a value. If it doesn’t, then its result is `undefined`.

To make the code clean and easy to understand, it’s recommended to use mainly local variables and parameters in the function, not outer variables.

It is always easier to understand a function which gets parameters, works with them and returns a result than a function which gets no parameters, but modifies outer variables as a side effect.

Function naming:

* A name should clearly describe what the function does. When we see a function call in the code, a good name instantly gives us an understanding what it does and returns.
* A function is an action, so function names are usually verbal.
* There exist many well-known function prefixes like `create…`, `show…`, `get…`, `check…` and so on. Use them to hint what a function does.
* Functions are values. They can be assigned, copied or declared in any place of the code.
* If the function is declared as a separate statement in the main code flow, that’s called a “Function Declaration”.
* If the function is created as a part of an expression, it’s called a “Function Expression”.
* Function Declarations are processed before the code block is executed. They are visible everywhere in the block.
* Function Expressions are created when the execution flow reaches them.

***

#### Polyfills and transpilers

#### [Transpilers](https://javascript.info/polyfills#transpilers)

A [transpiler](https://en.wikipedia.org/wiki/Source-to-source\_compiler) is a special piece of software that translates source code to another source code. It can parse (“read and understand”) modern code and rewrite it using older syntax constructs, so that it’ll also work in outdated engines.

E.g. JavaScript before year 2020 didn’t have the “nullish coalescing operator” `??`. So, if a visitor uses an outdated browser, it may fail to understand the code like `height = height ?? 100`.

A transpiler would analyze our code and rewrite `height ?? 100` into `(height !== undefined && height !== null) ? height : 100`.

```jsx
// before running the transpiler
height = height ?? 100;

// after running the transpiler
height = (height !== undefined && height !== null) ? height : 100;
```

Now the rewritten code is suitable for older JavaScript engines.

Usually, a developer runs the transpiler on their own computer, and then deploys the transpiled code to the server.

Speaking of names, [Babel](https://babeljs.io/) is one of the most prominent transpilers out there.

Modern project build systems, such as [webpack](https://webpack.js.org/), provide a means to run a transpiler automatically on every code change, so it’s very easy to integrate into the development process.

In this chapter we’d like to motivate you to study modern and even “bleeding-edge” language features, even if they aren’t yet well-supported by JavaScript engines.

Just don’t forget to use a transpiler (if using modern syntax or operators) and polyfills (to add functions that may be missing). They’ll ensure that the code works.

For example, later when you’re familiar with JavaScript, you can setup a code build system based on [webpack](https://webpack.js.org/) with the [babel-loader](https://github.com/babel/babel-loader) plugin.

Good resources that show the current state of support for various features:

* [https://kangax.github.io/compat-table/es6/](https://kangax.github.io/compat-table/es6/) – for pure JavaScript.
* [https://caniuse.com/](https://caniuse.com/) – for browser-related functions.

***

#### Objects

There’s a special operator `"in"` to check if the property is in the object or not.

syntax is

```jsx
"key" in object

// example

let user = { name: "John", age: 30 };

alert( "age" in user ); // true, user.age exists
alert( "blabla" in user ); // false, user.blabla doesn't exist
```

Why does the `in` operator exist? Isn’t it enough to compare against `undefined`?

Well, most of the time the comparison with `undefined` works fine. But there’s a special case when it fails, but `"in"` works correctly.

It’s when an object property exists, but stores `undefined`:

```jsx
let obj = {
  test: undefined
};

alert( obj.test ); // it's undefined, so - no such property?

alert( "test" in obj ); // true, the property does exist!
```

#### [The "for..in" loop](https://javascript.info/object#forin)

To walk over all keys of an object, there exists a special form of the loop: for..in. This is a completely different thing from the for(;;) construct that we studied before.

```jsx
let user = {
  name: "John",
  age: 30,
  isAdmin: true
};

for (let key in user) {
  // keys
  alert( key );  // name, age, isAdmin
  // values for the keys
  alert( user[key] ); // John, 30, true
}
```

**Summary of object**

Objects are associative arrays with several special features.

They store properties (key-value pairs), where:

* Property keys must be strings or symbols (usually strings).
* Values can be of any type.

To access a property, we can use:

* The dot notation: `obj.property`.
* Square brackets notation `obj["property"]`. Square brackets allow taking the key from a variable, like `obj[varWithKey]`.

Additional operators:

* To delete a property: `delete obj.prop`.
* To check if a property with the given key exists: `"key" in obj`.
* To iterate over an object: `for (let key in obj)` loop.

What we’ve studied in this chapter is called a “plain object”, or just `Object`.

There are many other kinds of objects in JavaScript:

* `Array` to store ordered data collections,
* `Date` to store the information about the date and time,
* `Error` to store the information about an error.
* …And so on.

They have their special features that we’ll study later. Sometimes people say something like “Array type” or “Date type”, but formally they are not types of their own, but belong to a single “object” data type. And they extend it in various ways.

Objects in JavaScript are very powerful. Here we’ve just scratched the surface of a topic that is really huge. We’ll be closely working with objects and learning more about them in further parts of the tutorial.

#### Object copy or cloning

Objects are assigned and copied by reference. In other words, a variable stores not the “object value”, but a “reference” (address in memory) for the value. So copying such a variable or passing it as a function argument copies that reference, not the object itself.

All operations via copied references (like adding/removing properties) are performed on the same single object.

To make a “real copy” (a clone) we can use `Object.assign` for the so-called “shallow copy” (nested objects are copied by reference) or a “deep cloning” function, such as [\_.cloneDeep(obj)](https://lodash.com/docs#cloneDeep).

#### Garbage collection

The main things to know:

* Garbage collection is performed automatically. We cannot force or prevent it.
* Objects are retained in memory while they are reachable.
* Being referenced is not the same as being reachable (from a root): a pack of interlinked objects can become unreachable as a whole, as we’ve seen in the example above.

Modern engines implement advanced algorithms of garbage collection.

A general book “The Garbage Collection Handbook: The Art of Automatic Memory Management” (R. Jones et al) covers some of them.

If you are familiar with low-level programming, more detailed information about V8’s garbage collector is in the article [A tour of V8: Garbage Collection](http://jayconrod.com/posts/55/a-tour-of-v8-garbage-collection).

The [V8 blog](https://v8.dev/) also publishes articles about changes in memory management from time to time. Naturally, to learn more about garbage collection, you’d better prepare by learning about V8 internals in general and read the blog of [Vyacheslav Egorov](http://mrale.ph/) who worked as one of the V8 engineers. I’m saying: “V8”, because it is best covered by articles on the internet. For other engines, many approaches are similar, but garbage collection differs in many aspects.

In-depth knowledge of engines is good when you need low-level optimizations. It would be wise to plan that as the next step after you’re familiar with the language.

#### [Constructor function](https://javascript.info/constructor-new#constructor-function)

Constructor functions technically are regular functions. There are two conventions though:

1. They are named with capital letter first.
2. They should be executed only with `"new"` operator.

For instance:

\`function User(name) { this.name = name; this.isAdmin = false; }

\*let user = new User("Jack");\*alert(user.name); // Jack alert(user.isAdmin); // false\`

When a function is executed with `new`, it does the following steps:

1. A new empty object is created and assigned to `this`.
2. The function body executes. Usually it modifies `this`, adds new properties to it.
3. The value of `this` is returned.

In other words, `new User(...)` does something like:

\`function User(name) { _// this = {}; (implicitly)_// add properties to this this.name = name; this.isAdmin = false;

_// return this; (implicitly)_}\`

***

#### DataTypes and primitives

To write numbers with many zeroes:

* Append `"e"` with the zeroes count to the number. Like: `123e6` is the same as `123` with 6 zeroes `123000000`.
* A negative number after `"e"` causes the number to be divided by 1 with given zeroes. E.g. `123e-6` means `0.000123` (`123` millionths).

For different numeral systems:

* Can write numbers directly in hex (`0x`), octal (`0o`) and binary (`0b`) systems.
* `parseInt(str, base)` parses the string `str` into an integer in numeral system with given `base`, `2 ≤ base ≤ 36`.
* `num.toString(base)` converts a number to a string in the numeral system with the given `base`.

For regular number tests:

* `isNaN(value)` converts its argument to a number and then tests it for being `NaN`
* `isFinite(value)` converts its argument to a number and returns `true` if it’s a regular number, not `NaN/Infinity/-Infinity`

For converting values like `12pt` and `100px` to a number:

* Use `parseInt/parseFloat` for the “soft” conversion, which reads a number from a string and then returns the value they could read before the error.

For fractions:

* Round using `Math.floor`, `Math.ceil`, `Math.trunc`, `Math.round` or `num.toFixed(precision)`.
* Make sure to remember there’s a loss of precision when working with fractions.

#### Strings

As we can see, `~n` is zero only if `n == -1` (that’s for any 32-bit signed integer `n`).

So, the test `if ( ~str.indexOf("...") )` is truthy only if the result of `indexOf` is not `-1`. In other words, when there is a match.

* There are 3 types of quotes. Backticks allow a string to span multiple lines and embed expressions `${…}`.
* Strings in JavaScript are encoded using UTF-16.
* We can use special characters like  and insert letters by their Unicode using `\u...`.
* To get a character, use: `[]`.
* To get a substring, use: `slice` or `substring`.
* To lowercase/uppercase a string, use: `toLowerCase/toUpperCase`.
* To look for a substring, use: `indexOf`, or `includes/startsWith/endsWith` for simple checks.
* To compare strings according to the language, use: `localeCompare`, otherwise they are compared by character codes.

There are several other helpful methods in strings:

* `str.trim()` – removes (“trims”) spaces from the beginning and end of the string.
* `str.repeat(n)` – repeats the string `n` times.
* …and more to be found in the [manual](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String).

#### Array

Array is a special kind of object, suited to storing and managing ordered data items.

The declaration:

\`// square brackets (usual) let arr = \[item1, item2...];

// new Array (exceptionally rare) let arr = new Array(item1, item2...);\`

The call to `new Array(number)` creates an array with the given length, but without elements.

* The `length` property is the array length or, to be precise, its last numeric index plus one. It is auto-adjusted by array methods.
* If we shorten `length` manually, the array is truncated.

Getting the elements:

* we can get element by its index, like `arr[0]`
* also we can use `at(i)` method that allows negative indexes. For negative values of `i`, it steps back from the end of the array. If `i >= 0`, it works same as `arr[i]`.

We can use an array as a deque with the following operations:

* `push(...items)` adds `items` to the end.
* `pop()` removes the element from the end and returns it.
* `shift()` removes the element from the beginning and returns it.
* `unshift(...items)` adds `items` to the beginning.

To loop over the elements of the array:

* `for (let i=0; i<arr.length; i++)` – works fastest, old-browser-compatible.
* `for (let item of arr)` – the modern syntax for items only,
* `for (let i in arr)` – never use.

To compare arrays, don’t use the `==` operator (as well as `>`, `<` and others), as they have no special treatment for arrays. They handle them as any objects, and it’s not what we usually want.

Instead you can use `for..of` loop to compare arrays item-by-item.

#### Array Methods

A cheat sheet of array methods:

* To add/remove elements:
  * `push(...items)` – adds items to the end,
  * `pop()` – extracts an item from the end,
  * `shift()` – extracts an item from the beginning,
  * `unshift(...items)` – adds items to the beginning.
  * `splice(pos, deleteCount, ...items)` – at index `pos` deletes `deleteCount` elements and inserts `items`.
  * `slice(start, end)` – creates a new array, copies elements from index `start` till `end` (not inclusive) into it.
  * `concat(...items)` – returns a new array: copies all members of the current one and adds `items` to it. If any of `items` is an array, then its elements are taken.
* To search among elements:
  * `indexOf/lastIndexOf(item, pos)` – look for `item` starting from position `pos`, return the index or `1` if not found.
  * `includes(value)` – returns `true` if the array has `value`, otherwise `false`.
  * `find/filter(func)` – filter elements through the function, return first/all values that make it return `true`.
  * `findIndex` is like `find`, but returns the index instead of a value.
* To iterate over elements:
  * `forEach(func)` – calls `func` for every element, does not return anything.
* To transform the array:
  * `map(func)` – creates a new array from results of calling `func` for every element.
  * `sort(func)` – sorts the array in-place, then returns it.
  * `reverse()` – reverses the array in-place, then returns it.
  * `split/join` – convert a string to array and back.
  * `reduce/reduceRight(func, initial)` – calculate a single value over the array by calling `func` for each element and passing an intermediate result between the calls.
* Additionally:
  * `Array.isArray(value)` checks `value` for being an array, if so returns `true`, otherwise `false`.

Please note that methods `sort`, `reverse` and `splice` modify the array itself.

These methods are the most used ones, they cover 99% of use cases. But there are few others:

*   [arr.some(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/some)/[arr.every(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/every) check the array.

    The function `fn` is called on each element of the array similar to `map`. If any/all results are `true`, returns `true`, otherwise `false`.

    These methods behave sort of like `||` and `&&` operators: if `fn` returns a truthy value, `arr.some()` immediately returns `true` and stops iterating over the rest of items; if `fn` returns a falsy value, `arr.every()` immediately returns `false` and stops iterating over the rest of items as well.

    We can use `every` to compare arrays:

    \`function arraysEqual(arr1, arr2) { return arr1.length === arr2.length && arr1.every((value, index) => value === arr2\[index]); }

    alert( arraysEqual(\[1, 2], \[1, 2])); // true\`
* [arr.fill(value, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/fill) – fills the array with repeating `value` from index `start` to `end`.
* [arr.copyWithin(target, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/copyWithin) – copies its elements from position `start` till position `end` into _itself_, at position `target` (overwrites existing).
* [arr.flat(depth)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/flat)/[arr.flatMap(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/flatMap) create a new flat array from a multidimensional array.

For the full list, see the [manual](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array).

From the first sight it may seem that there are so many methods, quite difficult to remember. But actually that’s much easier.

Look through the cheat sheet just to be aware of them. Then solve the tasks of this chapter to practice, so that you have experience with array methods.

Afterwards whenever you need to do something with an array, and you don’t know how – come here, look at the cheat sheet and find the right method. Examples will help you to write it correctly. Soon you’ll automatically remember the methods, without specific efforts from your side.

#### Iterator

Objects that can be used in `for..of` are called _iterable_.

* Technically, iterables must implement the method named `Symbol.iterator`.
  * The result of `obj[Symbol.iterator]()` is called an _iterator_. It handles further iteration process.
  * An iterator must have the method named `next()` that returns an object `{done: Boolean, value: any}`, here `done:true` denotes the end of the iteration process, otherwise the `value` is the next value.
* The `Symbol.iterator` method is called automatically by `for..of`, but we also can do it directly.
* Built-in iterables like strings or arrays, also implement `Symbol.iterator`.
* String iterator knows about surrogate pairs.

Objects that have indexed properties and `length` are called _array-like_. Such objects may also have other properties and methods, but lack the built-in methods of arrays.

If we look inside the specification – we’ll see that most built-in methods assume that they work with iterables or array-likes instead of “real” arrays, because that’s more abstract.

`Array.from(obj[, mapFn, thisArg])` makes a real `Array` from an iterable or array-like `obj`, and we can then use array methods on it. The optional arguments `mapFn` and `thisArg` allow us to apply a function to each item.

#### Map and Set

`Map` – is a collection of keyed values.

Methods and properties:

* `new Map([iterable])` – creates the map, with optional `iterable` (e.g. array) of `[key,value]` pairs for initialization.
* `map.set(key, value)` – stores the value by the key, returns the map itself.
* `map.get(key)` – returns the value by the key, `undefined` if `key` doesn’t exist in map.
* `map.has(key)` – returns `true` if the `key` exists, `false` otherwise.
* `map.delete(key)` – removes the value by the key, returns `true` if `key` existed at the moment of the call, otherwise `false`.
* `map.clear()` – removes everything from the map.
* `map.size` – returns the current element count.

The differences from a regular `Object`:

* Any keys, objects can be keys.
* Additional convenient methods, the `size` property.

`Set` – is a collection of unique values.

Methods and properties:

* `new Set([iterable])` – creates the set, with optional `iterable` (e.g. array) of values for initialization.
* `set.add(value)` – adds a value (does nothing if `value` exists), returns the set itself.
* `set.delete(value)` – removes the value, returns `true` if `value` existed at the moment of the call, otherwise `false`.
* `set.has(value)` – returns `true` if the value exists in the set, otherwise `false`.
* `set.clear()` – removes everything from the set.
* `set.size` – is the elements count.

Iteration over `Map` and `Set` is always in the insertion order, so we can’t say that these collections are unordered, but we can’t reorder elements or directly get an element by its number.

#### WeakMap and WeakSet

`WeakMap` is `Map`-like collection that allows only objects as keys and removes them together with associated value once they become inaccessible by other means.

`WeakSet` is `Set`-like collection that stores only objects and removes them once they become inaccessible by other means.

Their main advantages are that they have weak reference to objects, so they can easily be removed by garbage collector.

That comes at the cost of not having support for `clear`, `size`, `keys`, `values`…

`WeakMap` and `WeakSet` are used as “secondary” data structures in addition to the “primary” object storage. Once the object is removed from the primary storage, if it is only found as the key of `WeakMap` or in a `WeakSet`, it will be cleaned up automatically.

#### Destructuring

* Destructuring assignment allows for instantly mapping an object or array onto many variables.
*   The full object syntax:

    `let {prop : varName = default, ...rest} = object`

    This means that property `prop` should go into the variable `varName` and, if no such property exists, then the `default` value should be used.

    Object properties that have no mapping are copied to the `rest` object.
*   The full array syntax:

    `let [item1 = default, item2, ...rest] = array`

    The first item goes to `item1`; the second goes into `item2`, all the rest makes the array `rest`.
* It’s possible to extract data from nested arrays/objects, for that the left side must have the same structure as the right one.

#### Date Time

* Date and time in JavaScript are represented with the [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Date) object. We can’t create “only date” or “only time”: `Date` objects always carry both.
* Months are counted from zero (yes, January is a zero month).
* Days of week in `getDay()` are also counted from zero (that’s Sunday).
* `Date` auto-corrects itself when out-of-range components are set. Good for adding/subtracting days/months/hours.
* Dates can be subtracted, giving their difference in milliseconds. That’s because a `Date` becomes the timestamp when converted to a number.
* Use `Date.now()` to get the current timestamp fast.

Note that unlike many other systems, timestamps in JavaScript are in milliseconds, not in seconds.

Sometimes we need more precise time measurements. JavaScript itself does not have a way to measure time in microseconds (1 millionth of a second), but most environments provide it. For instance, browser has [performance.now()](https://developer.mozilla.org/en-US/docs/Web/API/Performance/now) that gives the number of milliseconds from the start of page loading with microsecond precision (3 digits after the point):

`alert(`Loading started ${performance.now()}ms ago`); // Something like: "Loading started 34731.26000000001ms ago" // .26 is microseconds (260 microseconds) // more than 3 digits after the decimal point are precision errors, only the first 3 are correct`

Node.js has `microtime` module and other ways. Technically, almost any device and environment allows to get more precision, it’s just not in `Date`.

***

#### Decorators

_Decorator_ is a wrapper around a function that alters its behavior. The main job is still carried out by the function.

Decorators can be seen as “features” or “aspects” that can be added to a function. We can add one or add many. And all this without changing its code!

To implement `cachingDecorator`, we studied methods:

* [func.call(context, arg1, arg2…)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Function/call) – calls `func` with given context and arguments.
* [func.apply(context, args)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Function/apply) – calls `func` passing `context` as `this` and array-like `args` into a list of arguments.

The generic _call forwarding_ is usually done with `apply`:

`let wrapper = function() { return original.apply(this, arguments); };`

We also saw an example of _method borrowing_ when we take a method from an object and `call` it in the context of another object. It is quite common to take array methods and apply them to `arguments`. The alternative is to use rest parameters object that is a real array.

There are many decorators there in the wild. Check how well you got them by solving the tasks of this chapter.

***

#### Events

Mouse events have the following properties:

* Button: `button`.
* Modifier keys (`true` if pressed): `altKey`, `ctrlKey`, `shiftKey` and `metaKey` (Mac).
  *   If you want to handle , then don’t forget Mac users, they usually use , so it’s better to check `if (e.metaKey || e.ctrlKey)`.

      Ctrl

      Cmd
* Window-relative coordinates: `clientX/clientY`.
* Document-relative coordinates: `pageX/pageY`.

The default browser action of `mousedown` is text selection, if it’s not good for the interface, then it should be prevented.

In the next chapter we’ll see more details about events that follow pointer movement and how to track element changes under it.

use **contextMenu** for right click

We considered a basic Drag’n’Drop algorithm.

The key components:

1. Events flow: `ball.mousedown` → `document.mousemove` → `ball.mouseup` (don’t forget to cancel native `ondragstart`).
2. At the drag start – remember the initial shift of the pointer relative to the element: `shiftX/shiftY` and keep it during the dragging.
3. Detect droppable elements under the pointer using `document.elementFromPoint`.

We can lay a lot on this foundation.

* On `mouseup` we can intellectually finalize the drop: change data, move elements around.
* We can highlight the elements we’re flying over.
* We can limit dragging by a certain area or direction.
* We can use event delegation for `mousedown/up`. A large-area event handler that checks `event.target` can manage Drag’n’Drop for hundreds of elements.
* And so on.

There are frameworks that build architecture over it: `DragZone`, `Droppable`, `Draggable` and other classes. Most of them do the similar stuff to what’s described above, so it should be easy to understand them now. Or roll your own, as you can see that that’s easy enough to do, sometimes easier than adapting a third-party solution.

***

#### Forms

Form navigation:

\*\*`document.forms`**A form is available as `document.forms[name/index]`.**`form.elements`**Form elements are available as `form.elements[name/index]`, or can use just `form[name/index]`. The `elements` property also works for `<fieldset>`.**`element.form`\*\*Elements reference their form in the `form` property.

Value is available as `input.value`, `textarea.value`, `select.value`, etc. (For checkboxes and radio buttons, use `input.checked` to determine whether a value is selected.)

For `<select>`, one can also get the value by the index `select.selectedIndex` or through the options collection `select.options`.

These are the basics to start working with forms. We’ll meet many examples further in the tutorial.

In the next chapter we’ll cover `focus` and `blur` events that may occur on any element, but are mostly handled on forms.

• Most elements do not support focus by default. Use `tabindex` to make anything focusable.

Data change events:

| Event                                                                                                 | Description                      | Special                                              |
| ----------------------------------------------------------------------------------------------------- | -------------------------------- | ---------------------------------------------------- |
| change                                                                                                | A value was changed.             | For text inputs triggers on focus loss.              |
| input                                                                                                 | For text inputs on every change. | Triggers immediately unlike change                   |
| .                                                                                                     |                                  |                                                      |
| cut/copy/paste                                                                                        | Cut/copy/paste actions.          | The action can be prevented. The event.clipboardData |
|  property gives access to the clipboard. All browsers except Firefox also support navigator.clipboard |                                  |                                                      |
| .                                                                                                     |                                  |                                                      |

## [window.onunload](https://javascript.info/onload-ondomcontentloaded#window-onunload)

When a visitor leaves the page, the `unload` event triggers on `window`. We can do something there that doesn’t involve a delay, like closing related popup windows.

The notable exception is sending analytics.

Let’s say we gather data about how the page is used: mouse clicks, scrolls, viewed page areas, and so on.

Naturally, `unload` event is when the user leaves us, and we’d like to save the data on our server.

There exists a special `navigator.sendBeacon(url, data)` method for such needs, described in the specification [https://w3c.github.io/beacon/](https://w3c.github.io/beacon/).

It sends the data in background. The transition to another page is not delayed: the browser leaves the page, but still performs `sendBeacon`.

#### Very important dom events

Page load events:

* The `DOMContentLoaded` event triggers on `document` when the DOM is ready. We can apply JavaScript to elements at this stage.
  * Script such as `<script>...</script>` or `<script src="..."></script>` block DOMContentLoaded, the browser waits for them to execute.
  * Images and other resources may also still continue loading.
* The `load` event on `window` triggers when the page and all resources are loaded. We rarely use it, because there’s usually no need to wait for so long.
* The `beforeunload` event on `window` triggers when the user wants to leave the page. If we cancel the event, browser asks whether the user really wants to leave (e.g we have unsaved changes).
* The `unload` event on `window` triggers when the user is finally leaving, in the handler we can only do simple things that do not involve delays or asking a user. Because of that limitation, it’s rarely used. We can send out a network request with `navigator.sendBeacon`.
* `document.readyState` is the current state of the document, changes can be tracked in the `readystatechange` event:
  * `loading` – the document is loading.
  * `interactive` – the document is parsed, happens at about the same time as `DOMContentLoaded`, but before it.
  * `complete` – the document and resources are loaded, happens at about the same time as `window.onload`, but before it.

***

### Mutation observer

`MutationObserver` is a built-in object that observes a DOM element and fires a callback when it detects a change.

We’ll first take a look at the syntax, and then explore a real-world use case, to see where such thing may be useful.

## [Syntax](https://javascript.info/mutation-observer#syntax)

`MutationObserver` is easy to use.

First, we create an observer with a callback-function:

`let observer = new MutationObserver(callback);`

And then attach it to a DOM node:

`observer.observe(node, config);`

`config` is an object with boolean options “what kind of changes to react on”:

* `childList` – changes in the direct children of `node`,
* `subtree` – in all descendants of `node`,
* `attributes` – attributes of `node`,
* `attributeFilter` – an array of attribute names, to observe only selected ones.
* `characterData` – whether to observe `node.data` (text content),

Few other options:

* `attributeOldValue` – if `true`, pass both the old and the new value of attribute to callback (see below), otherwise only the new one (needs `attributes` option),
* `characterDataOldValue` – if `true`, pass both the old and the new value of `node.data` to callback (see below), otherwise only the new one (needs `characterData` option).

Then after any changes, the `callback` is executed: changes are passed in the first argument as a list of [MutationRecord](https://dom.spec.whatwg.org/#mutationrecord) objects, and the observer itself as the second argument.

[MutationRecord](https://dom.spec.whatwg.org/#mutationrecord) objects have properties:

* `type` – mutation type, one of
  * `"attributes"`: attribute modified
  * `"characterData"`: data modified, used for text nodes,
  * `"childList"`: child elements added/removed,
* `target` – where the change occurred: an element for `"attributes"`, or text node for `"characterData"`, or an element for a `"childList"` mutation,
* `addedNodes/removedNodes` – nodes that were added/removed,
* `previousSibling/nextSibling` – the previous and next sibling to added/removed nodes,
* `attributeName/attributeNamespace` – the name/namespace (for XML) of the changed attribute,
* `oldValue` – the previous value, only for attribute or text changes, if the corresponding option is set `attributeOldValue`/`characterDataOldValue`.

***

## Advance concepts

#### Popups and window

Popup windows are used rarely, as there are alternatives: loading and displaying information in-page, or in iframe.

If we’re going to open a popup, a good practice is to inform the user about it. An “opening window” icon near a link or button would allow the visitor to survive the focus shift and keep both windows in mind.

* A popup can be opened by the `open(url, name, params)` call. It returns the reference to the newly opened window.
* Browsers block `open` calls from the code outside of user actions. Usually a notification appears, so that a user may allow them.
* Browsers open a new tab by default, but if sizes are provided, then it’ll be a popup window.
* The popup may access the opener window using the `window.opener` property.
* The main window and the popup can freely read and modify each other if they have the same origin. Otherwise, they can change location of each other and [exchange messages](https://javascript.info/cross-window-communication).

To close the popup: use `close()` call. Also the user may close them (just like any other windows). The `window.closed` is `true` after that.

* Methods `focus()` and `blur()` allow to focus/unfocus a window. But they don’t work all the time.
* Events `focus` and `blur` allow to track switching in and out of the window. But please note that a window may still be visible even in the background state, after `blur`.

To call methods and access the content of another window, we should first have a reference to it.

For popups we have these references:

* From the opener window: `window.open` – opens a new window and returns a reference to it,
* From the popup: `window.opener` – is a reference to the opener window from a popup.

For iframes, we can access parent/children windows using:

* `window.frames` – a collection of nested window objects,
* `window.parent`, `window.top` are the references to parent and top windows,
* `iframe.contentWindow` is the window inside an `<iframe>` tag.

If windows share the same origin (host, port, protocol), then windows can do whatever they want with each other.

Otherwise, only possible actions are:

* Change the `location` of another window (write-only access).
* Post a message to it.

Exceptions are:

* Windows that share the same second-level domain: `a.site.com` and `b.site.com`. Then setting `document.domain='site.com'` in both of them puts them into the “same origin” state.
* If an iframe has a `sandbox` attribute, it is forcefully put into the “different origin” state, unless the `allow-same-origin` is specified in the attribute value. That can be used to run untrusted code in iframes from the same site.

The `postMessage` interface allows two windows with any origins to talk:

1. The sender calls `targetWin.postMessage(data, targetOrigin)`.
2. If `targetOrigin` is not `'*'`, then the browser checks if window `targetWin` has the origin `targetOrigin`.
3.  If it is so, then `targetWin` triggers the `message` event with special properties:

    * `origin` – the origin of the sender window (like `http://my.site.com`)
    * `source` – the reference to the sender window.
    * `data` – the data, any object in everywhere except IE that supports only strings.

    We should use `addEventListener` to set the handler for this event inside the target window.

***

### Network Request

💡 Remember response has a property called ok it’s a bool to check whether the status is between 200-299 or not.

Response properties:

* `response.status` – HTTP code of the response,
* `response.ok` – `true` if the status is 200-299.
* `response.headers` – Map-like object with HTTP headers.

Methods to get response body:

* **`response.text()`** – return the response as text,
* **`response.json()`** – parse the response as JSON object,
* **`response.formData()`** – return the response as `FormData` object (`multipart/form-data` encoding, see the next chapter),
* **`response.blob()`** – return the response as [Blob](https://javascript.info/blob) (binary data with type),
* **`response.arrayBuffer()`** – return the response as [ArrayBuffer](https://javascript.info/arraybuffer-binary-arrays) (low-level binary data),

Fetch options so far:

* `method` – HTTP-method,
* `headers` – an object with request headers (not any header is allowed),
* `body` – the data to send (request body) as `string`, `FormData`, `BufferSource`, `Blob` or `UrlSearchParams` object.

[FormData](https://xhr.spec.whatwg.org/#interface-formdata) objects are used to capture HTML form and submit it using `fetch` or another network method.

We can either create `new FormData(form)` from an HTML form, or create an object without a form at all, and then append fields with methods:

* `formData.append(name, value)`
* `formData.append(name, blob, fileName)`
* `formData.set(name, value)`
* `formData.set(name, blob, fileName)`

Let’s note two peculiarities here:

1. The `set` method removes fields with the same name, `append` doesn’t. That’s the only difference between them.
2. To send a file, 3-argument syntax is needed, the last argument is a file name, that normally is taken from user filesystem for `<input type="file">`.

Other methods are:

* `formData.delete(name)`
* `formData.get(name)`
* `formData.has(name)`

#### Abort controller for network request

* `AbortController` is a simple object that generates an `abort` event on its `signal` property when the `abort()` method is called (and also sets `signal.aborted` to `true`).
* `fetch` integrates with it: we pass the `signal` property as the option, and then `fetch` listens to it, so it’s possible to abort the `fetch`.
* We can use `AbortController` in our code. The "call `abort()`" → “listen to `abort` event” interaction is simple and universal. We can use it even without `fetch`.

#### Cors

From the browser point of view, there are two kinds of cross-origin requests: “safe” and all the others.

“Safe” requests must satisfy the following conditions:

* Method: GET, POST or HEAD.
* Headers – we can set only:
  * `Accept`
  * `Accept-Language`
  * `Content-Language`
  * `Content-Type` to the value `application/x-www-form-urlencoded`, `multipart/form-data` or `text/plain`.

The essential difference is that safe requests were doable since ancient times using `<form>` or `<script>` tags, while unsafe were impossible for browsers for a long time.

So, the practical difference is that safe requests are sent right away, with the `Origin` header, while for the other ones the browser makes a preliminary “preflight” request, asking for permission.

**For safe requests:**

* → The browser sends the `Origin` header with the origin.
* ← For requests without credentials (not sent by default), the server should set:
  * `Access-Control-Allow-Origin` to \`\` or same value as `Origin`
* ← For requests with credentials, the server should set:
  * `Access-Control-Allow-Origin` to same value as `Origin`
  * `Access-Control-Allow-Credentials` to `true`

Additionally, to grant JavaScript access to any response headers except `Cache-Control`, `Content-Language`, `Content-Type`, `Expires`, `Last-Modified` or `Pragma`, the server should list the allowed ones in `Access-Control-Expose-Headers` header.

**For unsafe requests, a preliminary “preflight” request is issued before the requested one:**

* → The browser sends an `OPTIONS` request to the same URL, with the headers:
  * `Access-Control-Request-Method` has requested method.
  * `Access-Control-Request-Headers` lists unsafe requested headers.
* ← The server should respond with status 200 and the headers:
  * `Access-Control-Allow-Methods` with a list of allowed methods,
  * `Access-Control-Allow-Headers` with a list of allowed headers,
  * `Access-Control-Max-Age` with a number of seconds to cache the permissions.
* Then the actual request is sent, and the previous “safe” scheme is applied.

Typical code of the GET-request with `XMLHttpRequest`

```jsx
**let xhr = new XMLHttpRequest();

xhr.open('GET', '/my/url');

xhr.send();

xhr.onload = function() {
  if (xhr.status != 200) { // HTTP error?
    // handle error
    alert( 'Error: ' + xhr.status);
    return;
  }

  // get the response from xhr.response
};

xhr.onprogress = function(event) {
  // report progress
  alert(`Loaded ${event.loaded} of ${event.total}`);
};

xhr.onerror = function() {
  // handle non-HTTP error (e.g. network down)
};**
```

There are actually more events, the [modern specification](https://xhr.spec.whatwg.org/#events) lists them (in the lifecycle order):

* `loadstart` – the request has started.
* `progress` – a data packet of the response has arrived, the whole response body at the moment is in `response`.
* `abort` – the request was canceled by the call `xhr.abort()`.
* `error` – connection error has occurred, e.g. wrong domain name. Doesn’t happen for HTTP-errors like 404.
* `load` – the request has finished successfully.
* `timeout` – the request was canceled due to timeout (only happens if it was set).
* `loadend` – triggers after `load`, `error`, `timeout` or `abort`.

The `error`, `abort`, `timeout`, and `load` events are mutually exclusive. Only one of them may happen.

The most used events are load completion (`load`), load failure (`error`), or we can use a single `loadend` handler and check the properties of the request object `xhr` to see what happened.

We’ve already seen another event: `readystatechange`. Historically, it appeared long ago, before the specification settled. Nowadays, there’s no need to use it, we can replace it with newer events, but it can often be found in older scripts.

If we need to track uploading specifically, then we should listen to same events on `xhr.upload` object.

***

### Custom HTML Element

Custom elements can be of two types:

1.  “Autonomous” – new tags, extending `HTMLElement`.

    Definition scheme:

    ```jsx
    class MyElement extends HTMLElement {
      constructor() { super(); /* ... */ }
      connectedCallback() { /* ... */ }
      disconnectedCallback() { /* ... */  }
      static get observedAttributes() { return [/* ... */]; }
      attributeChangedCallback(name, oldValue, newValue) { /* ... */ }
      adoptedCallback() { /* ... */ }
     }
    customElements.define('my-element', MyElement);
    /* <my-element> */
    ```
2.  “Customized built-in elements” – extensions of existing elements.

    Requires one more `.define` argument, and `is="..."` in HTML:

    ```jsx
    class MyButton extends HTMLButtonElement { /*...*/ }
    customElements.define('my-button', MyElement, {extends: 'button'});
    /* <button is="my-button"> */
    ```

    Custom elements are well-supported among browsers. There’s a polyfill [https://github.com/webcomponents/polyfills/tree/master/packages/webcomponentsjs](https://github.com/webcomponents/polyfills/tree/master/packages/webcomponentsjs) .

    ***

    ### RegEx

    ## [Flags](https://javascript.info/regexp-introduction#flags)

    Regular expressions may have flags that affect the search.

    There are only 6 of them in JavaScript:

    \*\*`i`\*\*With this flag the search is case-insensitive: no difference between `A` and `a`&#x20;

    **`g`** With this flag the search looks for all matches, without it – only the first match is returned.

    \*\*`m`\*\*Multiline mode

    \*\*`s`\*\*Enables “dotall” mode, that allows a dot `.` to match newline character&#x20;

    \*\*`u`\*\*Enables full Unicode support. The flag enables correct processing of surrogate pairs.

    **`y`**“Sticky” mode: searching at the exact position in the text

    ```jsx
    // wrong way
    let matches = "JavaScript".match(/HTML/); // = null

    if (!matches.length) { // Error: Cannot read property 'length' of null
      alert("Error in the line above");
    }
    // right way
    let matches = "JavaScript".match(/HTML/) || [];

    if (!matches.length) {
      alert("No matches"); // now it works
    }
    ```

    * A regular expression consists of a pattern and optional flags: `g`, `i`, `m`, `u`, `s`, `y`.
    * Without flags and special symbols (that we’ll study later), the search by a regexp is the same as a substring search.
    * The method `str.match(regexp)` looks for matches: all of them if there’s `g` flag, otherwise, only the first one.
    * The method `str.replace(regexp, replacement)` replaces matches found using `regexp` with `replacement`: all of them if there’s `g` flag, otherwise only the first one.
    * The method `regexp.test(str)` returns `true` if there’s at least one match, otherwise, it returns `false`.

    #### Classes in RegEx

    Most used are:

    \*\*`\d` (“d” is from “digit”)**A digit: a character from `0` to `9`.**`\s` (“s” is from “space”)**A space symbol: includes spaces, tabs , newlines  and few other rare characters, such as `\v`, `\f` and .**`\w` (“w” is from “word”)\*\*A “wordly” character: either a letter of Latin alphabet or a digit or an underscore `_`. Non-Latin letters (like cyrillic or hindi) do not belong to `\w`.

    For every character class there exists an “inverse class”, denoted with the same letter, but uppercased.

    The “inverse” means that it matches all other characters, for instance:

    \*\*`\D`**Non-digit: any character except `\d`, for instance a letter.**`\S`**Non-space: any character except `\s`, for instance a letter.**`\W`\*\*Non-wordly character: anything but `\w`, e.g a non-latin letter or a space.

    There exist following character classes:

    * `\d` – digits.
    * `\D` – non-digits.
    * `\s` – space symbols, tabs, newlines.
    * `\S` – all but `\s`.
    * `\w` – Latin letters, digits, underscore `'_'`.
    * `\W` – all but `\w`.
    * `.` – any character if with the regexp `'s'` flag, otherwise any except a newline .

    …But that’s not all!

    Unicode encoding, used by JavaScript for strings, provides many properties for characters, like: which language the letter belongs to (if it’s a letter), is it a punctuation sign, etc.

    We can search by these properties as well. That requires flag `u`, covered in the next article.

    Here’s the main character categories and their subcategories:

    * Letter `L`:
      * lowercase `Ll`
      * modifier `Lm`,
      * titlecase `Lt`,
      * uppercase `Lu`,
      * other `Lo`.
    * Number `N`:
      * decimal digit `Nd`,
      * letter number `Nl`,
      * other `No`.
    * Punctuation `P`:
      * connector `Pc`,
      * dash `Pd`,
      * initial quote `Pi`,
      * final quote `Pf`,
      * open `Ps`,
      * close `Pe`,
      * other `Po`.
    * Mark `M` (accents etc):
      * spacing combining `Mc`,
      * enclosing `Me`,
      * non-spacing `Mn`.
    * Symbol `S`:
      * currency `Sc`,
      * modifier `Sk`,
      * math `Sm`,
      * other `So`.
    * Separator `Z`:
      * line `Zl`,
      * paragraph `Zp`,
      * space `Zs`.
    * Other `C`:
      * control `Cc`,
      * format `Cf`,
      * not assigned `Cn`,
      * private use `Co`,
      * surrogate `Cs`.

    So, e.g. if we need letters in lower case, we can write `\p{Ll}`, punctuation signs: `\p{P}` and so on.

    Flag `u` enables the support of Unicode in regular expressions.

    That means two things:

    1. Characters of 4 bytes are handled correctly: as a single character, not two 2-byte characters.
    2. Unicode properties can be used in the search: `\p{…}`.

    With Unicode pr

    #### **Anchors: string start ^ and end $**

    The caret `^` and dollar `$` characters have special meaning in a regexp. They are called “anchors”.

    The caret `^` matches at the beginning of the text, and the dollar `$` – at the end.

    #### **Word boundary: \b**

    A word boundary `\b` is a test, just like `^` and `$`.

    When the regexp engine (program module that implements searching for regexps) comes across `\b`, it checks that the position in the string is a word boundary.

    There are three different positions that qualify as word boundaries:

    * At string start, if the first string character is a word character `\w`.
    * Between two characters in the string, where one is a word character `\w` and the other is not.
    * At string end, if the last string character is a word character `\w`.

    #### **Escaping, special characters**

    As we’ve seen, a backslash `\` is used to denote character classes, e.g. `\d`. So it’s a special character in regexps (just like in regular strings).

    There are other special characters as well, that have special meaning in a regexp, such as `[ ] { } ( ) \ ^ $ . | ? * +`. They are used to do more powerful searches.

    Don’t try to remember the list – soon we’ll deal with each of them, and you’ll know them by heart automatically.

    * To search for special characters `[ \ ^ $ . | ? * + ( )` literally, we need to prepend them with a backslash `\` (“escape them”).
    * We also need to escape `/` if we’re inside `/.../` (but not inside `new RegExp`).
    * When passing a string to `new RegExp`, we need to double backslashes `\\`, cause string quotes consume one of them.

    #### Sets

    For instance:

    * **\d** – is the same as `[0-9]`,
    * **\w** – is the same as `[a-zA-Z0-9_]`,
    * **\s** – is the same as `[\t\n\v\f\r ]`, plus few other rare Unicode space characters.

    ```jsx
    // find [t or m], and then "op"
    alert( "Mop top".match(/[tm]op/gi) ); // "Mop", "top"
    ```

    #### \*_**Quantifiers +, , ? and {n}**_

    ## [Quantity {n}](https://javascript.info/regexp-quantifiers#quantity-n)

    The simplest quantifier is a number in curly braces: `{n}`.

    A quantifier is appended to a character (or a character class, or a `[...]` set etc) and specifies how many we need.

    It has a few advanced forms, let’s see examples:

    \*\*The exact count: `{5}**\d{5}` denotes exactly 5 digits, the same as `\d\d\d\d\d`.

    **The range: `{3,5}`, match 3-5 times**

    To find numbers from 3 to 5 digits we can put the limits into curly braces: `\d{3,5}`

    We can omit the upper limit.

    Then a regexp `\d{3,}` looks for sequences of digits of length `3` or more:

    Let’s return to the string `+7(903)-123-45-67`.

    A number is a sequence of one or more digits in a row. So the regexp is `\d{1,}`:

    There are shorthands for most used quantifiers:

    \*\*`+`\*\*Means “one or more”, the same as `{1,}`. For instance, `\d+` looks for numbers:

    **`?`**

    Means “zero or one”, the same as `{0,1}`. In other words, it makes the symbol optional. For instance, the pattern `ou?r` looks for `o` followed by zero or one `u`, and then `r`. So, `colou?r` finds both `color` and `colour`:

    * **\`\`**

    Means “zero or more”, the same as `{0,}`. That is, the character may repeat any times or be absent. For example, `\d0*` looks for a digit followed by any number of zeroes (may be many or none):

    `alert( "100 10 1".match(/\d0*/g) ); // 100, 10, 1`

    Compare it with `+` (one or more):

    `alert( "100 10 1".match(/\d0+/g) ); // 100, 10 // 1 not matched, as 0+ requires at least one zero`

    #### Greedy and Lazy search

    **Greedy**

    By default the regular expression engine tries to repeat the quantified character as many times as possible. For instance, `\d+` consumes all possible digits. When it becomes impossible to consume more (no more digits or string end), then it continues to match the rest of the pattern. If there’s no match then it decreases the number of repetitions (backtracks) and tries again.

    **Lazy**

    Enabled by the question mark `?` after the quantifier. The regexp engine tries to match the rest of the pattern before each repetition of the quantified character.

    As we’ve seen, the lazy mode is not a “panacea” from the greedy search. An alternative is a “fine-tuned” greedy search, with exclusions, as in the pattern `"[^"]+"`.

    #### Capturing

    Parentheses group together a part of the regular expression, so that the quantifier applies to it as a whole.

    Parentheses groups are numbered left-to-right, and can optionally be named with `(?<name>...)`.

    The content, matched by a group, can be obtained in the results:

    * The method `str.match` returns capturing groups only without flag `g`.
    * The method `str.matchAll` always returns capturing groups.

    If the parentheses have no name, then their contents is available in the match array by its number. Named parentheses are also available in the property `groups`.

    We can also use parentheses contents in the replacement string in `str.replace`: by the number `$n` or the name `$<name>`.

    A group may be excluded from numbering by adding `?:` in its start. That’s used when we need to apply a quantifier to the whole group, but don’t want it as a separate item in the results array. We also can’t reference such parentheses in the replacement string.

    #### OR

    Alternation is the term in regular expression that is actually a simple “OR”.

    In a regular expression it is denoted with a vertical line character `|`.

    For instance, we need to find programming languages: HTML, PHP, Java or JavaScript.

    The corresponding regexp: `html|php|java(script)?`.

    ```jsx
    let regexp = /html|php|css|java(script)?/gi;

    let str = "First HTML appeared, then CSS, then JavaScript";

    alert( str.match(regexp) ); // 'HTML', 'CSS', 'JavaScript'
    ```

    #### Lookahead and Lookbehind(Non-V8 doesn’t support)

    The syntax is: `X(?=Y)`, it means "look for `X`, but match only if followed by `Y`". There may be any pattern instead of `X` and `Y`.

    For an integer number followed by `€`, the regexp will be `\d+(?=€)`:

    \`let str = "1 turkey costs 30€";

    alert( str.match(/\d+(?=€)/) ); // 30, the number 1 is ignored, as it's not followed by €\`

    Lookahead and lookbehind (commonly referred to as “lookaround”) are useful when we’d like to match something depending on the context before/after it.

    For simple regexps we can do the similar thing manually. That is: match everything, in any context, and then filter by context in the loop.

    Remember, `str.match` (without flag `g`) and `str.matchAll` (always) return matches as arrays with `index` property, so we know where exactly in the text it is, and can check the context.

    But generally lookaround is more convenient.

    | Patternt | Type                | Matches                |
    | -------- | ------------------- | ---------------------- |
    | X(?=Y)   | Positive lookahead  | X if followed by Y     |
    | X(?!Y)   | Negative lookahead  | X if not followed by Y |
    | (?<=Y)X  | Positive lookbehind | X if after Y           |
    | (?\<!Y)X | Negative lookbehind | X if not after Y       |

    * Some Of Things for yours

    1- \w == \[a-z A-Z 0-9 \_]

    2- \W == \[^a-z A-Z 0-9 \_]

    3- \d == \[0-9]

    4- \D == \[^0-9]

    5- \s == Space==\[]

    6- \S == everything unless Space

    7- \b == Word Bounding => \bor Ragab loves an orange

    8- \[^] == Negate Set \[^ABC] Not Matches A Or B Or C

    9- ^ == Starts with ^R => Ragab

    10- $ == Ends With $b =>Ragab

    11- \A == Starts with From All Text

    12- \Z == Ends with From All Text

    13- A | B == Matches A Or B

    14- \[ABC] == Matches ABC

    15- \[A-Z] == Matches From A To Z

    16- \w{10} == 10 characters

    17- \d{10} == 10 digits

    18- \w{10,} == 10 More Than

    19- \d{10,} == 10 more Than

    20- \* == Matches Zero Or More

    21- + == Matches One Or More

    22- ? == Question Mark

    23- \ == Skip
