# ES6

## Learning Objectives

- **Explain** the history of ES and JS
- **Compare/contrast** features of ES5 and ES6
- **Explain** when to use `var` vs `let` vs `const`
- **Use** deconstruction to extract values from objects and arrays
- **Use** default parameters

<!-- Timing is tight here. Basically all questions need to go to parking lot. -->

<!--Actually 9:06 -->
<!-- 9:05 10 minutes -->

## Framing

Today, we are going to be looking at a new way to write Javascript by playing with some of the new features released in ES6.

#### JS vs ES

The JavaScript standard is officially referred to as [ECMAScript](https://en.wikipedia.org/wiki/ECMAScript).

As JS is so widely used that any changes would affect the whole web, there is a body known as TC39 or Ecma International, which formally approves official versions for release.

Each version contains features / changes to be added to the language.

In short, I like to think of ECMAScript as the language, and JavaScript an implementation of that language.

#### Evolution of JS

> Check out [this awesome visualization](http://shaunlebron.github.io/solar-system-of-js/#0) of the current state of the JS universe

Condensed timeline:

- 1999 - ES3 released, the first widespread use of the language.
- ES4 never released, largely due to  political reasons
- 2009 - ES5 released, what we've been writing so far in class.
- 2015 - ES6 published releasing a wide set of new features and syntax
- June, 2016 - ES7 published with features inclusing the `**` exponent operator

#### Why now?

Many plugins, frameworks and modules still use ES5, as browser support for
the new version of the language is [still not universal](http://caniuse.com/#search=es6), but the new syntax and features
of ES6 are increasingly becoming more and more popular among many open-source projects and in the developer world at large. Also, you are very likely to see it pop up in the documentation of some of the technologies we will be using in this course.

Today is all about exploring some of the [new features](https://github.com/lukehoban/es6features) and getting comfortable with the new syntax.

> For more backstory, we recommend checking out [this talk](https://www.youtube.com/watch?v=PlmsweSNhTw) from Brendan Eich on what he views as the future of JS.

## New Features

<!--9:17-->
<!--9:15 <10 minutes -->

### Block Scope

<details>
<summary>What does the concept of scope refer to in JS?</summary>

In short, the notion of which variables are available where.

</details>

---

<details>
<summary>So far in class, what is the primary way to control scope in JS?</summary>

Through the use of functions to create new local scopes.

</details>

#### `let`

So far, the primary way to control scope in an application has been through the use
of functions:

```js
// es5
var a = 1;
(function(){
  var a = 2
  console.log(a);
})();
console.log(a);
```

ES6 introduces the concept of block scoping, which allows us to limit the scope
of a variable declared with `let` to a given block `{ ... }`

```js
// es6
var a = 1;
{
  let a = 2;
  console.log(a);
}
console.log(a);
```

You're more likely to see `let` declarations inside an `if` or `for` block:

```js
//es5
for(var i = 0; i < 10; i++){
  console.log(i)
}
console.log("outside loop:", i)

// versus

//es6
for(let j = 0; j < 10; j++){
  console.log(j)
}
console.log("outside loop:", j)
```
#### `const`

ES6 introduces another keyword for declaring variables: `const`

`const` is an identifier for variables that won't be reassigned:

```js
const a = 1;
a = 2;
// Throws an error in chrome
const a = 2;
// throws an error
var a = 2;
// throws an error
```

<!--Actually 9:22 -->
<!--9:25 >10 minutes -->
### You do: Block Scope Exercises

1. https://github.com/ga-wdi-exercises/es6-exercises/blob/master/01-var-let-const.js
2. https://github.com/ga-wdi-exercises/es6-exercises/blob/master/02-const-complex.js

<!--9:36 -->
<!--9:35 <5 minutes -->

### Default parameters

With ES6, we now have the option to set a default value for any of our functions' parameters.

```js
function hello( name = "stranger"){
  console.log("Hello, " + name)
}

hello() // Hello, stranger
hello("Jesse") // Hello, Jesse
```

<!--Actually 9:40 (while explaining), 9:41 when exercise started-->
<!--9:40 >10 minutes -->

#### You do: Default Parameters Practice

1. https://github.com/ga-wdi-exercises/es6-exercises/blob/master/04-default-parameters.js
2. https://github.com/ga-wdi-exercises/es6-exercises/blob/master/05-default-parameters.js

<!--9:51 -->
<!--9:50 10 minutes -->

### Destructuring

Destructuring assignment makes it possible to extract data from complex data
types (arrays and objects) into distinct variables:

```js
let [a,b] = [1,2]
a //= 1
b //= 2
let nums = [1,2,3,4,5]
let [first, second, third] = nums
first //= 1
second //= 2
third //= 3
```

This also applies to objects:

```js
var user = {
   id: 1,
   name: "Bob",
   age: 43 ,
   profile_url:  "http://api.co/users/1",
   location: "DC",
}

// ES5
function greetUser (user) {
  console.log("Hello " + user.name + ", how's the weather in " + user.location)
}

// In ES6 becomes

function greetUser ({ name, location })  {
  console.log("Hello " + name + ", how's the weather in " + location)
}

//You would call both by using: greetUser(user)
```

<!--Woah questions!!! We were almost on time, then got bombarded with confusions -->
<!--Actually 10:06 -->

## Keep Going

There are lots more features of ES6 that we have not covered:

- [Symbols](http://es6-features.org/#SymbolType)
- [Iterator & for..of operator](http://es6-features.org/#IteratorForOfOperator)
- [Generators](https://davidwalsh.name/es6-generators)
- [Proxies](https://ponyfoo.com/articles/es6-proxies-in-depth)
- [Reflection and meta-programming](http://www.2ality.com/2011/01/reflection-and-meta-programming-in.html)

## Resources

- [You Don't Know ES6](https://github.com/getify/You-Dont-Know-JS/tree/master/es6%20%26%20beyond)
- [Block Scope](https://www.sitepoint.com/joys-block-scoping-es6/)
- [Destructuring](http://www.2ality.com/2015/01/es6-destructuring.html)
- [Template Literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals)
