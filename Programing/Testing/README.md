# Testing

##❯ Test Harness

  Think of a Test Harness as an 'enabler' that actually does all the work of (1)executing tests using a (2)test library and (3)generating reports. It would require that your test scripts are designed to handle different (4)test data and (5)test scenarios.

  References:
    https://stackoverflow.com/questions/11625351/what-is-test-harness

##❯ Domain Driven Design

  Domain Driven Design (DDD) is about mapping business domain concepts into software artifacts.

  References:
    http://www.infoq.com/articles/ddd-in-practice

##❯ Test-driven development (TDD)

  1. Write unit/functional/acceptance test
  2. Check that unit/functional/acceptance test is failing
  3. Write code
  4. Run all tests
  5. Cleanup code
  6. Write unit/functional/acceptance test...

  Example:
```javascript
suite('Array', function(){
  setup(function(){
    // ...
  });

  suite('#indexOf()', function(){
    test('should return -1 when not present', function(){
      assert.equal(-1, [1,2,3].indexOf(4));
    });
  });
});
```

  References:
    http://en.wikipedia.org/wiki/Test-driven_development

##❯ Behavior Driven Development - BDD

  Superset of TDD with "natural" language which can be written by anyone, a.k.a. TDD done right.

  Example:
```javascript
describe('Array', function(){
  before(function(){
    // ...
  });

  describe('#indexOf()', function(){
    it('should return -1 when not present', function(){
      [1,2,3].indexOf(4).should.equal(-1);
    });
  });
});
```

  References:
    http://en.wikipedia.org/wiki/Behavior-driven_development
    http://dannorth.net/introducing-bdd/

##❯ e2e test

  The entire application is tested in a real-world scenario such as communicating with the database, network, hardware and other applications.

##❯ Unit test

  Checking smallest testable unit of particular program

  References:
    http://en.wikipedia.org/wiki/Unit_testing
    http://andyshora.com/unit-testing-best-practices-angularjs.html

###❯❯ Stub

  For replacing a method with code that returns a specified result.

  References:
    https://stackoverflow.com/questions/3459287/whats-the-difference-between-a-mock-stub

###❯❯ Mock

  A stub with an assertion that the method gets called.

  References:
    https://stackoverflow.com/questions/3459287/whats-the-difference-between-a-mock-stub

##❯ Functional test

  Functional tests are written from a user's perspective. These tests confirm that the system does what users are expecting it to.

  References:
    http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html
    http://en.wikipedia.org/wiki/Functional_testing

##❯ Acceptance Test

  It's test for single user story, written by customer

  A [named user role] can [select/operate] [feature/function] so that [output] is [visible/complete/etc.] and leads to a Yes/No decision for user and developer

  References:
    http://c2.com/cgi/wiki?AcceptanceTest

##❯ CI

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
