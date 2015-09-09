---
layout: post
title:  "Bind, call and Apply in JavaScript"
date:   2015-09-08 
categories: javascript
---
[Extrct form JavaScriptissexy](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals/)

JavaScript’s Bind Allows Us to Set the this Value on Methods 
**bind ()** allows us to easily set which specific object will be bound to this when a function or method is invoked.

    //            <button>Get Random Person</button>​
    ​//        <input type="text">​
    ​
    ​
    ​var user = {
        data        :[
            {name:"T. Woods", age:37},
            {name:"P. Mickelson", age:43}
        ],
        clickHandler:function (event) {
            var randomNum = ((Math.random () * 2 | 0) + 1) - 1; // random number between 0 and 1​
    ​
            // This line is adding a random person from the data array to the text field​
            $ ("input").val (this.data[randomNum].name + " " + this.data[randomNum].age);
        }
    ​
    }
    ​
    ​// Assign an eventHandler to the button's click event​
    $ ("button").click (user.clickHandler);
When you click the button, you get an error because this in the clickHandler () method is bound to the button HTML element, since that is the object that the clickHandler method is executed on. To fix this problem, we could bind 

    $ ("button").click (user.clickHandler.bind (user));
use this

      // This data variable is a global variable​
                var data = [
                    {name:"Samantha", age:12},
                    {name:"Alexis", age:14}
                ]
    ​
                var user = {
                    // local data variable​
                    data    :[
                        {name:"T. Woods", age:37},
                        {name:"P. Mickelson", age:43}
                    ],
                    showData:function (event) {
                        var randomNum = ((Math.random () * 2 | 0) + 1) - 1; // random number between 0 and 1​
    ​
                        console.log (this.data[randomNum].name + " " + this.data[randomNum].age);
                    }
    ​
                }
    ​
                // Assign the showData method of the user object to a variable​
                var showDataVar = user.showData;
    ​
                showDataVar (); // Samantha 12 (from the global data array, not from the local data array)​
we can fix this problem by specifically setting the “this” value with the bind method:

                // Bind the showData method to the user object​
                var showDataVar = user.showData.bind (user);
    ​
                // Now the we get the value from the user object because the this keyword is bound to the user object​
                showDataVar (); // P. Mickelson 43​

**Bind () Allows us to Borrow Methods**

           // Here we have a cars object that does not have a method to print its data to the console​
                var cars = {
                    data:[
                        {name:"Honda Accord", age:14},
                        {name:"Tesla Model S", age:2}
                    ]
    ​
                }
    ​
                // We can borrow the showData () method from the user object we defined in the last example.​
                // Here we bind the user.showData method to the cars object we just created.​
                cars.showData = user.showData.bind (cars);
                cars.showData (); // Honda Accord 14​
it is best to borrow a method using either the Apply or Call method.

**JavaScript’s Bind Allows Us to Curry a Function** 

**Function Currying**, also known as partial function application, is the use of a function (that accept one or more arguments) that returns a new function with some of the arguments already set. The function that is returned has access to the stored arguments and variables of the outer function. 
Let’s use the bind () method for currying. 

    function greet (gender, age, name) {
        // if a male, use Mr., else use Ms.​
        var salutation = gender === "male" ? "Mr. " : "Ms. ";
    
        if (age > 25) {
            return "Hello, " + salutation + name + ".";
        }
        else {
            return "Hey, " + name + ".";
        }
    }
    // So we are passing null because we are not using the "this" keyword in our greet function.​
    var greetAnAdultMale = greet.bind (null, "male", 45);

    greetAnAdultMale ("John Hartlove"); // "Hello, Mr. John Hartlove."​

    var greetAYoungster = greet.bind (null, "", 16);
    greetAYoungster ("Alex"); // "Hey, Alex."​
    greetAYoungster ("Emma Waterloo"); // "Hey, Emma Waterloo."​
        
So, with the bind () method, we can explicitly set the this value for invoking methods on objects, we can borrow and copy methods, and assign methods to variable to be executed as functions.

####JavaScript’s Apply and Call Methods
The **Apply and Call** methods are two of the most often used Function methods in JavaScript, and for good reason: they allow us to borrow functions and set the this value in function invocation. In addition, the apply function in particular allows us to execute a function with an array of parameters, such that each parameter is passed to the function individually when the function executes—great for variadic functions; a variadic function takes varying number of arguments, not a set number of arguments as most functions do.

**Set the this value with Apply or Call**

    // global variable for demonstration​
    var avgScore = "global avgScore";
    ​
    //global function​
    function avg (arrayOfScores) {
        // Add all the scores and return the total​
        var sumOfScores = arrayOfScores.reduce (function (prev, cur, index, array) {
            return prev + cur;
        });
    ​
        // The "this" keyword here will be bound to the global object, unless we set the "this" with Call or Apply​
        this.avgScore = sumOfScores / arrayOfScores.length;
    }
    ​
    var gameController = {
        scores  :[20, 34, 55, 46, 77],
        avgScore:null​
    }
    ​
    // If we execute the avg function thus, "this" inside the function is bound to the global window object:​
    avg (gameController.scores);
    // Proof that the avgScore was set on the global window object​
    console.log (window.avgScore); // 46.4​
    console.log (gameController.avgScore); // null​
    ​
    // reset the global avgScore​
    avgScore = "global avgScore";
    ​
    // To set the "this" value explicitly, so that "this" is bound to the gameController,​
    // We use the call () method:​
    avg.call (gameController, gameController.scores);
    ​
    console.log (window.avgScore); //global avgScore​
    console.log (gameController.avgScore); // 46.4​
The apply and call methods are almost identical when setting the this value except that you pass the function parameters to apply () as an array, while you have to list the parameters individually to pass them to the call () method. More on this follows. Meanwhile, the apply () method also has another feature that the call () method doesn’t have, as we will soon see.

**Use Call or Apply To Set this in Callback Functions**

    // Define an object with some properties and a method​
    // We will later pass the method as a callback function to another function​
    var clientData = {
    id: 094545,
    fullName: "Not Set",
    // setUserName is a method on the clientData object​
    setUserName: function (firstName, lastName)  {
    // this refers to the fullName property in this object​
    this.fullName = firstName + " " + lastName;
    }
    }
    
    function getUserInput (firstName, lastName, callback, callbackObj) {
    // The use of the Apply method below will set the "this" value to callbackObj​
    callback.apply (callbackObj, [firstName, lastName]);
    }
The Apply method sets the this value to callbackObj. This allows us to execute the callback function with the this value set explicitly, so the parameters passed to the callback function will be set on the clientData object:

    // The clientData object will be used by the Apply method to set the "this" value​
    getUserInput ("Barack", "Obama", clientData.setUserName, clientData);
    // the fullName property on the clientData was correctly set​
    console.log (clientData.fullName); // Barack Obama​
    
[Examples](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals/) of **Borrowing Functions with Apply and Call (A Must Know)**