# Object-Oriented Programing (OOP)

References:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript
http://javascriptissexy.com/oop-in-javascript-what-you-need-to-know/

##❯ Namespace

A container which allows developers to bundle all functionality under a unique, application-specific name.

##❯ Class

Defines the characteristics of the object. It is a template definition of variables and methods of an object.

##❯ Object

An Instance of a class.

##❯ Property

An object characteristic, such as color.

##❯ Method

An object capability, such as walk. It is a subroutine or function associated with a class.

##❯ Constructor

A method called at the moment of instantiation of an object. It usually has the same name as that of the class containing it.

##❯ Inheritance

A class can inherit characteristics from another class.

Example:

```javascript
// Inehrit Person prototype from Person prototype
Student.prototype = Object.create(Person.prototype);
// Then you have to set proper constructor
Student.prototype.constructor = Student;
```

##❯ Encapsulation

When class inherits the methods of its parent and only needs to define things it wishes to change.

##❯ Abstraction

The conjunction of complex inheritance, methods, properties of an object must be able to simulate a reality model.

##❯ Polymorphism

Poly means "many"  and morphism means "forms". Different classes might define the same method or property.
