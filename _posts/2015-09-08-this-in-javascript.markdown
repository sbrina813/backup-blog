---
layout: post
title:  "this in JavaScript"
date:   2015-09-08 
categories: javascript
---
[Extrct form JavaScriptissexy](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)

Note that when we use `strict mode`, this holds the value of undefined in global functions and in anonymous functions that are not bound to any object.

> Even though it appears *this* refers to the object where it is
> defined, it is not until an object invokes the this Function that
> *this* is actually assigned a value. And the value it is assigned is based exclusively on the object that invokes the this Function. *this*
> has the value of the invoking object in most circumstances. However,
> there are a few scenarios where *this* does not have the value of the
> invoking object.

**The use of *this* in the global scope**
when we use *this* in a global function, it refers to (and has the value of) the global window object (not in strict mode though, as noted earlier) that is the main container of the entire JavaScript application or web page.

**When *this* is most misunderstood and becomes tricky**
The this keyword is most misunderstood when we borrow a method that uses *this*, when we assign a method that uses this to a variable, when a function that uses *this* is `passed as a callback function`, and when this is used inside a closure—an inner function. 

[**4 Examples need to digest for future use**](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)

**Always remember that *this* is assigned the value of the object that invoked the this Function.**