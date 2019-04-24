---
title: Hidden Benefits of Unit Tests
theme: beige
highlightTheme: rainbow
revealOptions:
    slideNumber: 'c/t'

---
# Hidden Benefits 
# of Unit Tests 

#### @rachelcdavies @tes_engineering
![Tes Logo](../images/tes_logo.jpg)

Notes:  
Unit tests provide a quick way for us to confirm our code is working as we expect,
many developers remain unconvinced whether it's worth investing time writing unit tests, 
especially in front-end projects. 
Once we have implemented a working solution, there's often pressure to move on to adding more crowd-pleasing features rather than trying to wrap our code 
with tests. 
The benefit of writing unit tests is not limited to automated checking our code still works. 
I'll share some less obvious benefits for investing time writing unit tests with some 
examples drawn from a recent project using GraphQL.

---

## A bit about me

* Full-stack software engineer
* Work remotely from home in Bath
* XP/TDD fan since 2000

Notes: 
I started coding 30 years ago before the web and Javascript existed.
I spent time coding in Ada, C, C++, Java and Ruby. 
Relatively new to JavaScript.
20 years ago I was an early adopter of eXtreme Programming an Agile software development approach.
After some years consulting, I made a shift back to coding.
so I could stop commuting to London.
Moved to Bath before Xmas and work from home for Tes.

---

## A bit about Tes

* Digital education company
* 200+ Javascript micro-services Node/React 
* 50+ full-stack engineers in 12 product squads
* Remote-first culture

Notes: We support and connect teachers and schools worldwide, 
helping them to improve children's lives through education
       
---

## Your Background?

![Hands](../images/hands.jpg)

Notes: 
Who is new to unit-testing?
Who regularly writes unit-tests?
Who prefers not to write unit-tests?

---

# Introduction to Tests

----

## What is a Test?

> _"A test is some code that checks some other code works as expected."_

Notes: 
We often check code works by running the application and clicking through as a user would.
The subject of the test is the code being tested.
There are lots of frameworks to help you write tests.

----

## What is a Unit Test?

![Units](../images/units.png)

https://www.martinfowler.com/bliki/UnitTest.html

Notes: 
Unit tests call some small chunk of code that is part of a larger application. 
Typically in JS this would be a component or a function.
Unit tests are organised into suites and can be run for a whole application.

----

## Test Frameworks

![Many](../images/many.jpg)


Notes: 
There are lots of frameworks to help you write tests, such as Tape, Mocha, Ava, etc
Some test frameworks test the whole application from the outside.
Others help us write tests for smaller parts of an application

----

##### Simple Example using Mocha

``` javascript

describe('Array object', () =>{
  // add a describe block for function under test

  describe('indexOf', () => {

    // a test case
    it('should return negative index when not present', () =>  {

      const arrayUnderTest = ['banana, apricot'];

      const result = arrayUnderTest.indexOf('apple');

      assert.equal(result, -1);
    });

    // another test case
    it(' should return index when present', () =>  {
    
      const arrayUnderTest = [1,2,3];
  
      const result = arrayUnderTest.indexOf(3);

      assert.equal(result, 2);
    });
    
  });
});
```

Notes: 
There are lots of frameworks to help you write tests, such as Tape, Mocha, Ava, etc
Some test frameworks test the whole application from the outside.
Others help us write tests for smaller parts of an application

----
## Anatomy of a Test 3As

* Arrange: 
    * setup preconditions and inputs
* Act: 
    * on component or function under test
* Assert: 
    * expected results have occurred

---

##### Example

``` javascript

describe('indexOf', () => {
    // a test case
    it('should return negative index when not present', () =>  {
      // Arrange
      const arrayUnderTest = ['banana, apricot'];
      const expectedResult = -1;
      // Act
      const result = arrayUnderTest.indexOf('apple');
      // Assert
      assert.equal(result, expectedResult);
    });
});
```

Notes: 
There are lots of frameworks to help you write tests, such as Tape, Mocha, Ava, etc
Some test frameworks test the whole application from the outside.
Others help us write tests for smaller parts of an application

---

## Tests as Documentation

* Tests illustrate what your code does
* Examples show what data it handles
* Test cases so how it handles error cases

Notes: 
Tests can be used as a way to document your code.

----

##### Example

``` javascript
describe('email', () => {
    const validEmail = 'a@b.com';
    const invalidEmailEmail = 'a@b.';

    it('returns a validation error message when the value is not a string', () =>
      [0, false, [], {}, true].forEach(notStringVal =>
        expect(email()(notStringVal)).to.be.a('string')));

    it('returns a validation error message when the string value is NOT a valid email address', () =>
      expect(email()(invalidEmailEmail)).to.be.a('string'));

    it('returns undefined when the string value is a valid email address', () =>
      expect(email()(validEmail)).to.equal(undefined));

    it('returns undefined when the value is empty', () =>
      [undefined, null, ''].forEach(emptyVal => expect(email()(emptyVal)).to.equal(undefined)));

  });
  
  ```
  
  Notes: 

----

## Test Doubles

* Stubs
* Mocks
* Spies

Notes: 
Test-doubles stand in for code that the subject of the test relies on.

----

## Solitary or Sociable?

![Isolate](../images/isolate.png)

https://www.martinfowler.com/bliki/UnitTest.html

Notes: 


---

# Trade-Off?

----

# Obvious Benefits :-)

* Quick automatic checking code works
* Write once, run many times
* Documentation for future developers

----

# Obvious Cost :-(

* Takes time to write
* Take more time to maintain as code changes
* May be a barrier to refactoring code

----

## When to write unit tests?

* Concurrent with developing code
    * helps you shape your code
    * make progress when end-to-end is not ready
* When you have non-trivial logic
    * helps you document your code
    * helps you uncover edge cases

Notes: 
Test first?

----

## When not to write unit tests?

* Time consuming and fiddly to setup
* Area of code that likely change
* When intention is obvious

Notes: 

---

# More Examples

----

## React Component

https://www.robinwieruch.de/react-testing-tutorial

----

## GraphQL Component

https://www.apollographql.com/docs/react/recipes/testing

---

## Unit tests help you to ..

* Shape the design of your code
* Work on components independently
* Figure out API to backend services
* Save time checking you didn't break functionality!

Notes: Summing up ^^

---

## Thank You
#### @tes_engineering
![Tes Logo](../images/tes-career-hero.png)

Notes: We're hiring :-)
