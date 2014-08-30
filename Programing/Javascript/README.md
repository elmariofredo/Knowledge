# [ Javascript ]

## [ Node.js ]

  References:
    https://github.com/sindresorhus/awesome-nodejs

## [ Callbacks ]

  Is function passed to another function as argument and executed when needed, usually when we finish some IO processing.

## [ Event Emitters ]

  Many objects in Node emit events: a net.Server emits an event each time a peer connects to it, a fs.readStream emits an event when the file is opened. All objects which emit events are instances of events.EventEmitter. You can access this module by doing: require("events");

## [ Auto-boxing ]

  Whenever you access or assign to a property of a number, string or boolean, a temporary object value (of the Number, String or Boolean class, respectively) is created with the same naked value as the primitive value, but that temporary object is only available to that property access, and does not replace the primitive value that your variable references.

  References:
      http://princepthomas.blogspot.cz/2011/07/auto-boxing-javascript-primitive-types.html

## [ Streams ]

  References:
    http://nodejs.org/docs/latest/api/stream.html
    http://streamjs.org/
    https://github.com/substack/stream-handbook

## setTimeout

  something about bind

## [ Object ]

  References:
    http://helephant.com/2008/08/17/how-javascript-objects-work/

## [ this ]

  In any function, this is a reserved keyword that refers to the owner of the function. `this` is also used in event handler functions, where it refers to the element(s) that triggered the event

## [ bind ]

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

## [ Buffer ]

## [ Promises ]

## [ ES6 ]

  ECMAScript 6 new implementation of Javascript with new awesome features, code name Harmony.

  References:
    http://wiki.ecmascript.org/doku.php?id=harmony:specification_drafts&s=harmony#draft_specification_for_es.next_ecma-262_edition_6
    https://github.com/lukehoban/es6features
    https://kangax.github.io/compat-table/es6/

### [ Closure ]

  The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.

  References:
    https://stackoverflow.com/questions/111102/how-do-javascript-closures-work?page=1&tab=votes#tab-top
    http://web.archive.org/web/20080209105120/http://blog.morrisjohns.com/javascript_closures_for_dummies

### [ Prototype ]

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

### [ Generator ]

  References:
    http://wiki.ecmascript.org/doku.php?id=harmony:generators
    http://strongloop.com/strongblog/how-to-generators-node-js-yield-use-cases/
    https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*

#### [ Yield ]

  The yield keyword is used to pause and resume a generator.

#### [ Reflect ]

#### [ Proxy ]

#### [ Thunk ]

  Is a subroutine that is created, often automatically, to assist a call to another subroutine

## [ Strict Mode ]

  Is a way to opt in to a restricted variant of JavaScript. Prevent global variable leak. `this` will be the global object or undefined

  References:
    https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/Strict_mode
