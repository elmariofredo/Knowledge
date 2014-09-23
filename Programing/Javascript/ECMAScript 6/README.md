# ECMAScript 6 (ES6)

  New implementation of Javascript with new awesome features, code name Harmony.

  References:
    http://wiki.ecmascript.org/doku.php?id=harmony:specification_drafts&s=harmony#draft_specification_for_es.next_ecma-262_edition_6
    https://github.com/lukehoban/es6features
    https://kangax.github.io/compat-table/es6/

##❯ Generator

References:
http://wiki.ecmascript.org/doku.php?id=harmony:generators
http://strongloop.com/strongblog/how-to-generators-node-js-yield-use-cases/
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*

##❯ Yield

The yield keyword is used to pause and resume a generator.

##❯ Reflect

##❯ Proxy

##❯ Thunk

Is a subroutine that is created, often automatically, to assist a call to another subroutine
This approach is going to be deprecated as JS is going to be more Promised enabled, see https://github.com/visionmedia/co/issues/143

## Modules

Way to import other sources using native API. Currently we have two standarts
* CommonJS Modules - Node.js server
* Asynchronous Module Definition (AMD) - RequireJS browser
New implementation is trying to get best out of these two options.

References: http://www.2ality.com/2014/09/es6-modules-final.html
