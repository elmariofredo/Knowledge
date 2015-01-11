# Javascript

##❯ Unobtrusive JavaScript

General approach to the use of JavaScript in web pages.

* Separation of functionality structure/content and presentation.
* Best practices to avoid the problems of traditional JavaScript programming (such as browser inconsistencies and lack of scalability)
* Support old browsers and offer additional functionality to new browsers(progressive enhancement)

Resources: https://en.wikipedia.org/wiki/Unobtrusive_JavaScript

##❯ Callbacks

  Is function passed to another function as argument and executed when needed, usually when we finish some IO processing.

##❯ Event Emitters

  Many objects in Node emit events: a net.Server emits an event each time a peer connects to it, a fs.readStream emits an event when the file is opened. All objects which emit events are instances of events.EventEmitter. You can access this module by doing: require("events");

##❯ Auto-boxing

  Whenever you access or assign to a property of a number, string or boolean, a temporary object value (of the Number, String or Boolean class, respectively) is created with the same naked value as the primitive value, but that temporary object is only available to that property access, and does not replace the primitive value that your variable references.

Example:
```javascript
// You can't manipulate object which your primitive value reference
// This value is Auto-boxed to object it repesent but it's not full object
var str = 'primitive-valued string literal';
str.split = function(){ return 'overridden!'; };
console.log( str.split(' ') ); //=> ["primitive-valued", "string", "literal"]

// You can when using proper object
var str = new String( 'primitive-valued string literal' );
str.split = function(){ return 'overridden!'; };
console.log( str.split(' ') ); //=> "overridden!" that's more like it

// Note that
String('koko') === 'koko'
```

References:
  http://princepthomas.blogspot.cz/2011/07/auto-boxing-javascript-primitive-types.html
  http://www.acnenomor.com/3801378p1/javascript-string-literal-vs-string-object

##❯ Streams

  References:
    http://nodejs.org/docs/latest/api/stream.html
    http://streamjs.org/
    https://github.com/substack/stream-handbook

## setTimeout

Timing out of function execution

Resources: https://stackoverflow.com/questions/1728563/changing-the-scope-of-an-anonymous-function-on-a-settimeout-causes-a-weird-warni

##❯ Object

  References:
    http://helephant.com/2008/08/17/how-javascript-objects-work/

##❯ This

In any function, this is a reserved keyword that refers to the owner of the function. `this` is also used in event handler functions, where it refers to the element(s) that triggered the event

##❯ Call

Call function with selected context(first argument) and pass arguments to function itself

##❯ Apply

Same as call but accepts array as second argument and pass it to function

##❯ Bind

  Calling f.bind(someObject) creates a new function with the same body and scope as f, but where this occurs in the original function, in the new function it is permanently bound to the first argument of bind, regardless of how the function is being used.

  Example:
```javascript
var bind = function(context, func) {
  return func.apply(context);
}

bind({name: "Something"}, function() {
  return this.name;
});

"Something"
```

##❯ Buffer

##❯ Promises

Promise represents a value that is not yet known a deferred represents work that is not yet finished.


References:
  http://blog.mediumequalsmessage.com/promise-deferred-objects-in-javascript-pt1-theory-and-semantics

##❯ Closure

The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.

References:
https://stackoverflow.com/questions/111102/how-do-javascript-closures-work?page=1&tab=votes#tab-top
http://web.archive.org/web/20080209105120/http://blog.morrisjohns.com/javascript_closures_for_dummies

##❯ Prototype

Object that provides shared properties for other objects.

`cat.__proto__` is internal reference to prototype object and `Animal.prototype` is reference to object from which is `__proto__` builded. `__proto__` is not standart JS implementation and thus should be never used.

By default `Animal.prototype` is set to `Object.prototype` as all objects inherit from `Object`

Example:

```javascript
var Animal = function(){};
Animal.prototype.yay = 'yay';
var cat = new Animal();
cat.__proto__
> Object {yay: "yay"}
Object.getPrototypeOf( cat );
> Object {yay: "yay"}
Object.getPrototypeOf( cat ) === Animal.prototype
> true
```

References:
http://mathieularose.com/javascript-prototype/
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf
http://stackoverflow.com/questions/650764/how-does-proto-differ-from-constructor-prototype
http://stackoverflow.com/questions/2344493/what-is-the-default-prototype-for-custom-function-in-javascript

##❯ Strict Mode

Is a way to opt in to a restricted variant of JavaScript. Prevent global variable leak. `this` will be the global object or undefined

References:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/Strict_mode

##❯ Flux

New architectural approach to replace traditional MVC like pattern. Brought to public by Facebook with their react framework. It's trying to solve development issues on large projects. Includes JSX bit different javascript implementation and Virtual DOM to use diffs when updating DOM.

References:
https://docs.google.com/a/vejlupek.cz/presentation/d/1afMLTCpRxhJpurQ97VBHCZkLbR1TEsRnd3yyxuSQ5YY/edit#slide=id.g380053cce_1703
http://scotch.io/tutorials/javascript/getting-to-know-flux-the-react-js-architecture

##❯ Currying

It's special kind of function construct. If you give a curried function less arguments then it expects, it will give you back a function, which has been fed the arguments you gave it and will accept the remaining ones. In the example above, we first gave it 4 (myFunc(4)), and it was waiting for another number, and we gave it 9.

Example:

```javascript
alert(myFunc(2,2));      // alerts 4
var adds4 = myFunc(4);   // adds4, is now a function,
                         // which adds 4, to it's argument.
alert(adds4(5));         // alerts 9.
```

References:
https://medium.com/@kbrainwave/currying-in-javascript-ce6da2d324fe
http://www.crockford.com/javascript/www_svendtofte_com/code/curried_javascript/index.html

##❯ Immediately-Invoked Function Expression - IIFE

Creating function which purpose is to create own execution context

Example:
```javascript
(function(){
  x = 1;
})
console.log(x);
> ReferenceError: x is not defined

// Ignore output
!function(){ /* code */ }();
~function(){ /* code */ }();
-function(){ /* code */ }();
+function(){ /* code */ }();

// Another approach
new function(){ /* code */ }
```

References: http://benalman.com/news/2010/11/immediately-invoked-function-expression/

##❯ requestAnimationFrame (rAF)

Browser api to controll animation execution to get it sync with redraw process and on highest speed possible(60fps).

Resources:
  http://creativejs.com/resources/requestanimationframe/

Example:
```javascript
var body = document.querySelector('body');
body.style.fontSize = 0
var draw = function(){
  requestAnimationFrame(draw);
  body.style.fontSize=parseInt(body.style.fontSize)+1+'px';
}
draw();
```
