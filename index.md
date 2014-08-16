# Mario Vejlupek - Dictionary

## [ User Experience ]

  User experience (UX) involves a person's behaviors, attitudes, and emotions about using a particular product, system or service.

  References:
    https://en.wikipedia.org/wiki/User_experience
    http://www.guidebookgallery.org/guis
    http://www.webdesignerdepot.com/2009/03/operating-system-interface-design-between-1981-2009/

### [ HEART ]

  Framework for UX metrics it means:

    Happiness: measures of user attitudes, often collected via survey. For example: satisfaction, perceived ease of use, and net-promoter score.
    Engagement: level of user involvement, typically measured via behavioral proxies such as frequency, intensity, or depth of interaction over some time period. Examples might include the number of visits per user per week or the number of photos uploaded per user per day.
    Adoption: new users of a product or feature. For example: the number of accounts created in the last seven days or the percentage of Gmail users who use labels.
    Retention: the rate at which existing users are returning. For example: how many of the active users from a given time period are still present in some later time period? You may be more interested in failure to retain, commonly known as “churn.”
    Task success: this includes traditional behavioral metrics of user experience, such as efficiency (e.g. time to complete a task), effectiveness (e.g. percent of tasks completed), and error rate. This category is most applicable to areas of your product that are very task-focused, such as search or an upload flow.

  References:
    http://www.gv.com/lib/how-to-choose-the-right-ux-metrics-for-your-product

## [ Development ]

    References:
      http://mitpress.mit.edu/sicp/full-text/book/book.html

### [ Primitives ]

    basic type is a data type provided by a programming language as a basic building block.

    References:
      http://en.wikipedia.org/wiki/Primitive_data_type

### [ Objects ]

    particular instance of a class where the object can be a combination of variables, functions, and data structures.

    References:
      http://en.wikipedia.org/wiki/Object_(computer_science)

### [ Testing ]


    References:


#### [ Test Harness ]

    Think of a Test Harness as an 'enabler' that actually does all the work of (1)executing tests using a (2)test library and (3)generating reports. It would require that your test scripts are designed to handle different (4)test data and (5)test scenarios.

    References:
      https://stackoverflow.com/questions/11625351/what-is-test-harness

#### [ Domain Driven Design ]

    Domain Driven Design (DDD) is about mapping business domain concepts into software artifacts.

    References:
      http://www.infoq.com/articles/ddd-in-practice

#### [ Test-driven development - TDD ]

    # Write unit/functional/acceptance test
    # Check that unit/functional/acceptance test is failing
    # Write code
    # Run all tests
    # Cleanup code
    # Write unit/functional/acceptance test...

    References:
      http://en.wikipedia.org/wiki/Test-driven_development

#### [ Behavior Driven Development - BDD ]

    Superset of TDD with "natural" language which can be written by anyone, a.k.a. TDD done right.

    References:
      http://en.wikipedia.org/wiki/Behavior-driven_development
      http://dannorth.net/introducing-bdd/

#### [ e2e test ]

    The entire application is tested in a real-world scenario such as communicating with the database, network, hardware and other applications.



#### [ Unit test ]

    Checking smallest testable unit of particular program

    References:
      http://en.wikipedia.org/wiki/Unit_testing
      http://andyshora.com/unit-testing-best-practices-angularjs.html

#### [ Functional test ]

    Functional tests are written from a user's perspective. These tests confirm that the system does what users are expecting it to.

    References:
      http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html
      http://en.wikipedia.org/wiki/Functional_testing

#### [ Acceptance Test ]

    It's test for single user story, written by customer

    A [named user role] can [select/operate] [feature/function] so that [output] is [visible/complete/etc.] and leads to a Yes/No decision for user and developer

    References:
      http://c2.com/cgi/wiki?AcceptanceTest

### [ Technical Debt ]

    During the planning or execution of a software project, decisions are made to defer necessary work.

    Note:
      There should be always visible list of technical debts with possible outcomes.

    References:
      http://c2.com/cgi/wiki?TechnicalDebt

### [ Patterns ]

    References:
      http://addyosmani.com/resources/essentialjsdesignpatterns/book/

#### [ Duck Typing ]

#### [ Singleton ]
#### [ Factory ]
#### [ Module ]
#### [ Observer ]

#### [ Parent References ]

    Tree structure pattern where each record has parent refenrence like this:

    ```
    db.categories.insert( { _id: "MongoDB", parent: "Databases" } )
    db.categories.insert( { _id: "dbm", parent: "Databases" } )
    db.categories.insert( { _id: "Databases", parent: "Programming" } )
    ```

    The Parent Links pattern provides a simple solution to tree storage but requires multiple queries to retrieve subtrees.

    References:
      http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-parent-references/

#### [ Child References ]

    Tree structure pattern where each record store array of node child id's like this:

    ```
    db.categories.insert( { _id: "MongoDB", children: [] } )
    db.categories.insert( { _id: "dbm", children: [] } )
    db.categories.insert( { _id: "Databases", children: [ "MongoDB", "dbm" ] } )
    ```

    The Child References pattern provides a suitable solution to tree storage as long as no operations on subtrees are necessary. This pattern may also provide a suitable solution for storing graphs where a node may have multiple parents.

    References:
      http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-child-references/

#### [ Array of Ancestors ]

    Tree structure pattern where we store array of ancestors along with parent node like this:

    ```
    db.categories.insert( { _id: "MongoDB", ancestors: [ "Books", "Programming", "Databases" ], parent: "Databases" } )
    db.categories.insert( { _id: "dbm", ancestors: [ "Books", "Programming", "Databases" ], parent: "Databases" } )
    db.categories.insert( { _id: "Databases", ancestors: [ "Books", "Programming" ], parent: "Programming" } )
    ```

    The Array of Ancestors pattern is slightly slower than the Materialized Paths pattern but is more straightforward to use.

    References:
      http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-ancestors-array/

#### [ Materialized Paths ]

    Tree structure pattern where as in **Array of Ancestors** are stored ancestor but as comma delimited string without parent node like this

    ```
    db.categories.insert( { _id: "Books", path: null } )
    db.categories.insert( { _id: "Programming", path: ",Books," } )
    db.categories.insert( { _id: "Databases", path: ",Books,Programming," } )
    ```

    References:
      http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-materialized-paths/

#### [ Nested Sets ]

    The Nested Sets pattern identifies each node in the tree as stops in a round-trip traversal of the tree. The application visits each node in the tree twice; first during the initial trip, and second during the return trip. The Nested Sets pattern stores each tree node in a document; in addition to the tree node, document stores the id of node’s parent, the node’s initial stop in the left field, and its return stop in the right field.

    ```
    db.categories.insert( { _id: "Books", parent: 0, left: 1, right: 12 } )
    db.categories.insert( { _id: "Programming", parent: "Books", left: 2, right: 11 } )
    db.categories.insert( { _id: "Languages", parent: "Programming", left: 3, right: 4 } )
    ```

    The Nested Sets pattern provides a fast and efficient solution for finding subtrees but is inefficient for modifying the tree structure. As such, this pattern is best for static trees that do not change.

    Reference:
      http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-nested-sets/




### [ API ]

#### [ REST ]

    References:
      http://restful-api-design.readthedocs.org
      https://github.com/interagent/http-api-design
      http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html

#### [ Collection ]

    Resources can be grouped into collections. Each collection is homogeneous so that it contains only one type of resource, and unordered.

    Example:

    /api/:coll	    A top-level collection named “coll”
    /api/:coll/:id	The resource “id” inside collection “coll”

    References:
      http://restful-api-design.readthedocs.org/en/latest/resources.html#resources

#### [ Resource ]
    A resource is an object with a type, associated data, relationships to other resources, and a set of methods that operate on it. It is similar to an object instance in an object-oriented programming language, with the important difference that only a few standard methods are defined for the resource (corresponding to the standard HTTP GET, POST, PUT and DELETE methods), while an object instance typically has many methods.

    References:
      http://restful-api-design.readthedocs.org/en/latest/resources.html



### [ Javascript ]

#### [ Callbacks ]

    Is function passed to another function as argument and executed when needed, usually when we finish some IO processing.

#### [ Event Emitters ]

    Many objects in Node emit events: a net.Server emits an event each time a peer connects to it, a fs.readStream emits an event when the file is opened. All objects which emit events are instances of events.EventEmitter. You can access this module by doing: require("events");

#### [ Auto-boxing ]

    Whenever you access or assign to a property of a number, string or boolean, a temporary object value (of the Number, String or Boolean class, respectively) is created with the same naked value as the primitive value, but that temporary object is only available to that property access, and does not replace the primitive value that your variable references.

    References:
      http://princepthomas.blogspot.cz/2011/07/auto-boxing-javascript-primitive-types.html

#### [ Streams ]

    References:
      http://nodejs.org/docs/latest/api/stream.html
      http://streamjs.org/
      https://github.com/substack/stream-handbook

#### setTimeout

  something about bind

#### [ Strict Mode ]

#### [ Object ]

    References:
      http://helephant.com/2008/08/17/how-javascript-objects-work/

#### [ this ]

#### [ bind ]

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

#### [ Buffer ]

#### [ Promises ]

#### [ ES6 ]

    ECMAScript 6 new implementation of Javascript with new awesome features, code name Harmony.

    References:
      http://wiki.ecmascript.org/doku.php?id=harmony:specification_drafts&s=harmony#draft_specification_for_es.next_ecma-262_edition_6
      https://github.com/lukehoban/es6features
      https://kangax.github.io/compat-table/es6/

##### [ Closure ]

    The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.

    References:
      https://stackoverflow.com/questions/111102/how-do-javascript-closures-work?page=1&tab=votes#tab-top
      http://web.archive.org/web/20080209105120/http://blog.morrisjohns.com/javascript_closures_for_dummies

##### [ Prototype ]

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

##### [ Generator ]

      References:
        http://wiki.ecmascript.org/doku.php?id=harmony:generators
        http://strongloop.com/strongblog/how-to-generators-node-js-yield-use-cases/
        https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*

###### [ Yield ]

      The yield keyword is used to pause and resume a generator.

###### [ Reflect ]

###### [ Proxy ]

###### [ Thunk ]
      Is a subroutine that is created, often automatically, to assist a call to another subroutine

#### [ Strict Mode ]

    Is a way to opt in to a restricted variant of JavaScript

    References:
      https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/Strict_mode

### [ HTML ]

#### [ Flexbox ]

    References:
      http://www.sitepoint.com/are-we-ready-to-use-flexbox/

### [ Agile Software Development ]

#### [ Scrum ]

    References:
      http://scrummethodology.com/

##### [ Sprint ]

      References:
        http://scrummethodology.com/scrum-sprint/

# [ CI ]

    Continuous Integration

      References:
        https://drone.io/
        http://stridercd.com/
        https://www.atlassian.com/software/bamboo/pricing#ondemand-subscription-details
        http://buildbot.net/
        https://travis-ci.org/
        https://circleci.com/
        https://www.codeship.io/
        https://semaphoreapp.com/
        http://jenkins-ci.org/

# [ FizBuzz ]

    Really stupid interview test!

    Example:
      ```javascript
      var i;

      for (i = 1; i < 101; i = i + 1) {

          if ((i % 3 === 0) && (i % 5 === 0)) {
              listItem = "fizzbuzz";
          }
          else if (i % 3 === 0) {
              listItem = "fizz";
          }
          else if (i % 5 === 0) {
              listItem = "buzz";
          }
          else {
              listItem = i;
          }

          console.log(listItem);
      }
      ```

### [ Password ]

    References:
      http://www.sitepoint.com/good-users-bad-password-ux/

### [ SemVer ]

    References:
      http://www.sitepoint.com/semantic-versioning-why-you-should-using
