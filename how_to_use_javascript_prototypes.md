### How to use JavaScript Prototypes

#### What is the prototype chain? How do we define objects in JavaScript?

Part of being a good developer is modularization. Splitting code apart and reusing functionality is key to writing solid maintainable code. One of the tools developers use to split code apart is Classes. In fact Classes are the main way programmers are taught to segment their code. This practice is so popular that many modern programming languages adhere to what’s called the Object Oriented Paradigm. When a language is Object Oriented it means that a majority of the features in the language center around the utilization of and the creation of classes/objects. Classes can inherit properties of other Classes, or even extend their functionality. Classes also get to keep bits of data private and “encapsulated” away from outside code. In the world of programming Object Oriented programming can be incredibly useful.

This is all well and good, but it’s important at this point to acknowledge JavaScript doesn’t utilize traditional Classes. While many of the features of Classes are present within JavaScript, they aren’t the exactly the same. JavaScript is what’s called a dynamic language. There are no classes. In JavaScript there are only objects. In fact everything is an Object, even functions. Objects in JavaScript are Prototype based. Every Object in JavaScript has a “Prototype Chain” associated with it. When you call a method associated with an object, or reference a value the interpreter looks through the Prototype Chain until it finds what it needs.

> Everything is an Object with a prototype chain in JavaScript

So how does all of this actually work in practice? First let’s start with constructors. Constructors are used to define the initial state of an object. In normal Object Oriented languages constructors are a special feature of classes, but in JavaScript they are a plain function objects.

### Constructors

Let’s say we want to define a Person Object Prototype.

![img](https://cdn-images-1.medium.com/max/800/1*TVGWjQk_Bsp9KdPr3Iv8Gw.png)Person Constructor

As you can see the constructor is a regular JavaScript Function, which in turn is a JavaScript Object. All Objects in JavaScript have the special “this” keyword. A constructor in JavaScript is simply a function that sets its own attributes through the “this” keyword. This constructor will define an object with attributes name, age, job, and hobby.

You might be wondering why the underscore before the attributes? In JavaScript there isn’t a way to protect data. The underscore is a convention to communicate to other programmers not to directly access those data fields, and that they are meant to be “private”.

If those attributes are meant to be private how do we access and mutate them?

### Getters and Setters

Implementing get and set methods goes as follows.

![img](https://cdn-images-1.medium.com/max/800/1*sJgAvdsnrPDCJbHFyEEpHg.png)Implementation of get and set methods

These methods can be easily implemented with the new ES6 arrow functions. Using Get and Set methods is a best practice because it forces the programmer to think about how data is accessed from outside of an Object.

### Adding Methods to a Prototype

What if we would like to add functionality for our Person object to have a birthday? In our birthday function we could have the Person announce their age, increment age by one year, and then announce their new age.

![img](https://cdn-images-1.medium.com/max/800/1*ivZOs_0o2IGT7fbabh8Kjg.png)Adding functions to the prototype

To add a method onto a prototype we define a new attribute of the prototype and assign it a function. Now all Objects of the Person prototype will have access to this function.

### The Prototype Chain

So we’ve seen how to create a prototype and add attributes to it, but in practice how is this Prototype actually used? To utilize this Prototype we need to create an instance of an object adhering to it.

![img](https://cdn-images-1.medium.com/max/800/1*F49ZBBrVkdIRXeKgUEVsHA.png)Creating an instance of type Person

That’s it. That’s really all there is to it. We now have an Object named Todd, of the Prototype Person. Todd now has access to all of the methods and attributes associated with the person Prototype.

![img](https://cdn-images-1.medium.com/max/800/1*Ix9LYHGhUGc5fLr1H3V7Kw.png)Accessing attributes from the prototype

This is all made possible via the Prototype Chain. The JavaScript interpreter will create a hierarchy of Prototypes associated with an Object. Whenever an attribute is accessed the interpreter climbs through the hierarchy starting at the bottom and going from parent to parent until it finds the attribute it’s searching for.

![img](https://cdn-images-1.medium.com/max/800/1*3ijoVxDlNUsXgZ0bTR6nLA.png)The Prototype chain

We can access the haveBirthdayParty function because it exists on the Prototype Chain for Todd.

> Objects can access any attribute on their prototype chain

Prototypes are different than classes because they simply define how an Object is created and what attributes the Object will immediately have access to. There isn’t traditional class inheritance in JavaScript. When an Object “inherits” methods or attributes from a Prototype it simply means that the Prototype exists somewhere on the object’s Prototype Chain.

Many developers are confused by the difference between Prototypical inheritance and Classes, or believe there is no difference. Part of becoming a good JavaScript developer is knowing the difference and knowing how the language is working under the hood.

Hopefully this helps!