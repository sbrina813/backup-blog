---
layout: post
title:  "Object Oriented Programming (OOP)"
date:   2015-09-07 
categories: javascript
---
[Extract form JavaScriptissexy](http://javascriptissexy.com/oop-in-javascript-what-you-need-to-know/)

**Object Oriented Programming (OOP)** refers to using self-contained pieces of code to develop applications. We call these self-contained pieces of code objects, better known as Classes in most OOP programming languages and Functions in JavaScript.
Building applications with objects allows us to adopt some valuable techniques, namely, **Inheritance** (objects can inherit features from other objects), **Polymorphism** (objects can share the same interface—how they are accessed and used—while their underlying implementation of the interface may differ), and **Encapsulation** (each object is responsible for specific tasks).
In this article, we are concerned with only **Inheritance and Encapsulation** **since only these two concepts apply to OOP in JavaScript**, particularly because, in JavaScript, objects can encapsulate functionalities and inherit methods and properties from other objects.These two techniques: the best technique for creating objects with specialized functionalities (aka Encapsulation) and the best technique for reusing code (aka Inheritance).

###Encapsulation and Inheritance Overview
**Objects** can be thought of as the main actors in an application, or simply the main “things” or building blocks that do all the work. As you know by now, objects are everywhere in JavaScript since every component in JavaScript is an Object, including Functions, Strings, and Numbers. We normally use object literals or constructor functions to create objects.

**Encapsulation** refers to enclosing all the functionalities of an object within that object so that the object’s internal workings (its methods and properties) are hidden from the rest of the application. This allows us to abstract or localize specific set of functionalities on objects.

**Inheritance** refers to an object being able to inherit methods and properties from a parent object (a Class in other OOP languages, or a Function in JavaScript).

**Both of these concepts, encapsulation and inheritance, are important because they allow us to build applications with reusable code, scalable architecture, and abstracted functionalities. Maintainable, scalable, efficient.**

###OOP in JavaScript
The two important principles with OOP in JavaScript are **Object Creation patterns (Encapsulation) and Code Reuse patterns (Inheritance)**. When building applications, you create many objects, and there exist many ways for creating these objects: you can use the ubiquitous object literal pattern,

    var myObj = {name: "Richard", profession: "Developer"}; 
    
You can use the prototype pattern, adding each method and property directly on the object’s prototype.

    function Employee () {}
    ​
    Employee.prototype.firstName = "Abhijit";
    Employee.prototype.lastName = "Patel";
    Employee.prototype.startDate = new Date();
    Employee.prototype.signedNDA = true;
    Employee.prototype.fullName = function () {
    console.log (this.firstName + " " + this.lastName); 
    };
    ​
    ​var abhijit = new Employee () //​
    console.log(abhijit.fullName()); // Abhijit Patel​
    console.log(abhijit.signedNDA); // true

You can also use the constructor pattern, a constructor function (Classes in other languages, but Functions in JavaScript).

    function Employee (name, profession) {
    ​this.name = name;
    ​this.profession = profession;
    } // Employee () is the constructor function because we use the <em>new</em> keyword below to invoke it.​
    ​
    ​var richard = new Employee (“Richard”, “Developer”) // richard is a new object we create from the Employee () constructor function.​
    ​
    console.log(richard.name); //richard​
    console.log(richard.profession); // Developer
    
These two universal principles—**creating objects** (especially from constructor Functions) and **allowing objects to inherit properties and methods**—are the main focus of this article and, indeed, **the main concepts with OOP in JavaScript.** We first discuss the object creation pattern.

###Encapsulation in JavaScript
#####(The Best Object Creation Pattern: Combination Constructor/Prototype Pattern)

As discussed above, one of the main principles **with OOP is encapsulation**: put all the inner workings of an object inside that object. 

**Why Encapsulation?**
whenever you want to create objects with similar functionalities (to use the same methods and properties), you encapsulate the main functionalities in a Function and you use that Function’s constructor to create the objects. This is the `essence` of encapsulation.
**Implementation of Combination Constructor/Prototype Pattern**

    function User (theName, theEmail) {
        this.name = theName;
        this.email = theEmail;
        this.quizScores = [];
        this.currentScore = 0;
    }
    ​
    User.prototype = {
        constructor: User, //have to set manually,since constructor property changes 
        saveScore:function (theScoreToAdd)  {
            this.quizScores.push(theScoreToAdd)
        },
        showNameAndScores:function ()  {
            var scores = this.quizScores.length > 0 ? this.quizScores.join(",") : "No Scores Yet";
            return this.name + " Scores: " + scores;
        },
        changeEmail:function (newEmail)  {
            this.email = newEmail;
            return "New Email Saved: " + this.email;
        }
    }
    
    // A User ​
    firstUser = new User("Richard", "Richard@examnple.com"); 
    firstUser.changeEmail("RichardB@examnple.com");
    firstUser.saveScore(15);
    firstUser.saveScore(10); 
    ​
    firstUser.showNameAndScores(); //Richard Scores: 15,10​
    ​
    ​// Another User​
    secondUser = new User("Peter", "Peter@examnple.com");
    secondUser.saveScore(18);
    secondUser.showNameAndScores(); //Peter Scores: 18

*The one **disadvantage** of overwriting the prototype is that the constructor property no longer points to the prototype, so we have to set it manually. Hence this line:*
With this pattern, you can use the standard operators and methods on the instances, including the instanceOf operator, the for-in loop (even hasOwnProperty), and the constructor property.

###Inheritance in JavaScript
#####(The Best Pattern: Parasitic Combination Inheritance)

**Object.create method**

    Object.create = function (o) {
    ​//It creates a temporary constructor F()​
            function F() {
            }
    ​//And set the prototype of the this constructor to the parametric (passed-in) o object​
    ​//so that the F() constructor now inherits all the properties and methods of o​
            F.prototype = o;
    ​
    ​//Then it returns a new, empty object (an instance of F())​
    ​//Note that this instance of F inherits from the passed-in (parametric object) o object. ​
    ​//Or you can say it copied all of the o object's properties and methods​
            return new F();
        }

The crux of the matter with this Object.create method is that you pass into it an object that you want to inherit from, and it returns a new object that inherits from the object you passed into it. For example:

    // We have a simple cars object​
    ​var cars = {
        type:"sedan",
        wheels:4​
    };
    ​
    ​// We want to inherit from the cars object, so we do:​
    ​var toyota = Object.create (cars); // now toyota inherits the properties from cars​
    console.log(toyota.type); // sedan

The next function we will use for inheritance is the **inheritPrototype** function. **This function succinctly implements the parasitic combination inheritance for us.** We pass in the parent object (or Super Class) and the child object (or Sub Class), and the function does the parasitic combination inheritance: makes the child object inherits from the parent object.

     function inheritPrototype(childObject, parentObject) {
        // As discussed above, we use the Crockford’s method to copy the properties and methods from the parentObject onto the childObject​
    ​// So the copyOfParent object now has everything the parentObject has ​
        var copyOfParent = Object.create(parentObject.prototype);
    ​
        //Then we set the constructor of this new object to point to the childObject.​
    ​// Why do we manually set the copyOfParent constructor here, see the explanation immediately following this code block.​
        copyOfParent.constructor = childObject;
    ​
        // Then we set the childObject prototype to copyOfParent, so that the childObject can in turn inherit everything from copyOfParent (from parentObject)​
       childObject.prototype = copyOfParent;
    }
    
######Why did we manually set the copyOfParent.constructor?
We explicitly set the copyOfParent.constructor property to point to the childObject constructor because in the preceding step, var copyOfParent = Object.create(parentObject.prototype), this is what we actually did:

    // We made a new object and overwrote its prototype with the parentObject prototype:​
    ​function F() {
            }
    F.prototype = parentObject.prototype;
    ​// Then it was this new F object we assigned to copyOfParent.​
    ​// All of this was done inside the Object.create () method.
    
So, this new F object, which we assigned to copyOfParent, doesn’t have a constructor property anymore because we overwrote its entire prototype. **Whenever you overwrite an object’s prototype (object.prototype = someVal), you also overwrite the object’s constructor property.**
To make sure we have the correct value for copyOfParent constructor, we set it manually with this: `copyOfParent.constructor = childObject;`

> Essentially, we are copying all the properties and methods from the
> parentObject to the childObject, but we are **using the copyOfParent as
> an intermediary** for the copy. And because the childObject prototype
> was overwritten during the copy, we manually set the copyOfParent
> constructor to the childObject. Then we set the childObject prototype
> to the copyOfParent so that the childObject inherits from the
> parentObject.
