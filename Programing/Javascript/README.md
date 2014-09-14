# Javascript

##❯ OOP

References:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript
http://javascriptissexy.com/oop-in-javascript-what-you-need-to-know/

###❯ Namespace

A container which allows developers to bundle all functionality under a unique, application-specific name.

###❯ Class

Defines the characteristics of the object. It is a template definition of variables and methods of an object.

###❯ Object

An Instance of a class.

###❯ Property

An object characteristic, such as color.

###❯ Method

An object capability, such as walk. It is a subroutine or function associated with a class.

###❯ Constructor

A method called at the moment of instantiation of an object. It usually has the same name as that of the class containing it.

###❯ Inheritance

A class can inherit characteristics from another class.

Example:

```javascript
// Inehrit Person prototype from Person prototype
Student.prototype = Object.create(Person.prototype);
// Then you have to set proper constructor
Student.prototype.constructor = Student;
```

###❯ Encapsulation

When class inherits the methods of its parent and only needs to define things it wishes to change.

###❯ Abstraction

The conjunction of complex inheritance, methods, properties of an object must be able to simulate a reality model.

###❯ Polymorphism

Poly means "many"  and morphism means "forms". Different classes might define the same method or property.


##❯ Node.js

  References:
    https://github.com/sindresorhus/awesome-nodejs

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
```  

References: http://princepthomas.blogspot.cz/2011/07/auto-boxing-javascript-primitive-types.html

##❯ Streams

  References:
    http://nodejs.org/docs/latest/api/stream.html
    http://streamjs.org/
    https://github.com/substack/stream-handbook

## setTimeout

  something about bind

##❯ Object

  References:
    http://helephant.com/2008/08/17/how-javascript-objects-work/

##❯ this

  In any function, this is a reserved keyword that refers to the owner of the function. `this` is also used in event handler functions, where it refers to the element(s) that triggered the event

##❯ bind

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

##❯ ES6

  ECMAScript 6 new implementation of Javascript with new awesome features, code name Harmony.

  References:
    http://wiki.ecmascript.org/doku.php?id=harmony:specification_drafts&s=harmony#draft_specification_for_es.next_ecma-262_edition_6
    https://github.com/lukehoban/es6features
    https://kangax.github.io/compat-table/es6/

###❯❯ Closure

  The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.

  References:
    https://stackoverflow.com/questions/111102/how-do-javascript-closures-work?page=1&tab=votes#tab-top
    http://web.archive.org/web/20080209105120/http://blog.morrisjohns.com/javascript_closures_for_dummies

###❯❯ Prototype

  Object that provides shared properties for other objects.

  Example:

```javascript
var a = function(){};
a.prototype.yay = 'yay';
var x = new a();
x.__proto__
> Object {yay: "yay"}
Object.getPrototypeOf(x);
> Object {yay: "yay"}
Object.getPrototypeOf(x) === a.prototype
> true
```

  References:
    http://mathieularose.com/javascript-prototype/
    https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf

###❯❯ Generator

  References:
    http://wiki.ecmascript.org/doku.php?id=harmony:generators
    http://strongloop.com/strongblog/how-to-generators-node-js-yield-use-cases/
    https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*

####❯❯❯ Yield

  The yield keyword is used to pause and resume a generator.

####❯❯❯ Reflect

####❯❯❯ Proxy

####❯❯❯ Thunk

  Is a subroutine that is created, often automatically, to assist a call to another subroutine

##❯ Strict Mode

  Is a way to opt in to a restricted variant of JavaScript. Prevent global variable leak. `this` will be the global object or undefined

  References:
    https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/Strict_mode

##❯ Flux

New architectural approach to replace traditional MVC like pattern. Broght to public by Facebook with their react framework. It's trying to solve development issues on large projects. Includes JSX bit different javascript impementation and Virtual DOM to use diffs when updating DOM.

References:
  https://docs.google.com/a/vejlupek.cz/presentation/d/1afMLTCpRxhJpurQ97VBHCZkLbR1TEsRnd3yyxuSQ5YY/edit#slide=id.g380053cce_1703

## Currying

It's special kind of function construct. If you give a curried function, less arguments, then it expects, it will give you back, a function, which has been fed the arguments you gave it, and will accept the remaining ones. In the example above, we first gave it 4 (myFunc(4)), and it was waiting for another number, and we gave it 9.

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
