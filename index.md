# Mario Vejlupek - Dictionary

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

    During the planning or execution of a software project, decisions are made to defer necessary work

    References:
      http://c2.com/cgi/wiki?TechnicalDebt

### [ Patterns ]

    References:
      http://addyosmani.com/resources/essentialjsdesignpatterns/book/

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
      http://restful-api-design.readthedocs.org/
      https://github.com/interagent/http-api-design

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

#### [ Buffer ]

#### [ Promises ]

#### [ ES6 ]

    References:

##### [ Closure ]

    The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.

    References:
      https://stackoverflow.com/questions/111102/how-do-javascript-closures-work?page=1&tab=votes#tab-top
      http://web.archive.org/web/20080209105120/http://blog.morrisjohns.com/javascript_closures_for_dummies

##### [ Prototype ]

    Object.getPrototypeOf()

    References:
      https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf

##### [ Generator ]

      References:
        http://strongloop.com/strongblog/how-to-generators-node-js-yield-use-cases/

###### [ Yield ]

      The yield keyword is used to pause and resume a generator.

###### [ Reflect ]

###### [ Proxy ]

###### [ Thunk ]
      Is a subroutine that is created, often automatically, to assist a call to another subroutine

#### [ Strict Mode ]


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

### [ Password ]

    References:
      http://www.sitepoint.com/good-users-bad-password-ux/

### [ SemVer ]

    References:
      http://www.sitepoint.com/semantic-versioning-why-you-should-using
