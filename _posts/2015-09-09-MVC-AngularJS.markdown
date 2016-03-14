---
layout: post
title:  "SPA and MVC in AngularJS"
date:   2015-09-09
categories: javascript
---
Extract from the book of Pro AngularJS---Adam Freeman

#### Round-Trip App vs Single Page App

**Round-trip App**:The browser requests an initial HTML document from the server. User interactions-such as clicking a link or submitting a form-led the browser to request and receive a completely new HTML document. In this kind of application, the browser is essentially a rending engine for HTML content, and all of the applicaation logic and data resides on the server. The browser makes a series of stateless HTTP requests that the server handles by generating HTML documents danamically.

**Serious drawbacks to round-trip apps** : They make the user wait while the next HTML document is requested and roaded, they require a large server-side infrastructure to process all of the requests and manage all of the application state, and they require a lot of bandwidth because each HTML document has to be self-contained(a lot of same content-like header, footer- being included in each response from the server)

**Single page application(SPA)**: An initial HTML document is sent to the browser, but user interactions lead to Ajax requests for small fragments of HTML or data inserted into the existing set of elements being displayed to the user. The initial HTML document is never be reloaded or replaced, and the user can continue to interact with the existing HTML while the Ajax requests are being performed asychronously, even if that just means seeing a "data loading" message.
Ther is gradual tendency for current web app projects to move toward the single page application model, because the benefits of using the MVC pattern really start to manifest themselves in larger and more complex projects.

####Understanding the MVC Pattern
The key to applying the MVC pattern is to implement the key premise of a *separation of concerns*, in which the data model in the application is decoupled from the business and presentation logic. In the client-side web development, **this means separating the data, the logic that oprates on that data, and the HTML elements used to display the data.** The result is a client-side application that is easier to develop,maintain and test.

**Models**---the M in MVC,contains the data that users work with. There are two broad types of model. **view models**, which represent just data passed from the controller to the view, and **domian models**, which contain the data in a business domain, along with the operations, transformation, and rules for creating, storing and manipulating that data, collectively referred to as the model logic.

> **A model should:**
> 
>  - Contain domain data
>  - Contain the logic for creating,managing and modifying the domain data 
>  - Provide a clean API that exposes the model data and operations on it  

> **should not:**
> 
>  - Expose details of how the model data is obtained or managed( in other words, details of the data storage mechanism or the remote web
> service should not be exposed to controllers and views)
>  - Contain logic that transforms the model based on user interaction( because this is the controller's job)
>  - Contain logic for displaying to the user( this is the view's job)

 
**Controllers** are the connective tissue in an AngularJS web application, acting as conduits between the data model and views. Controllers add business logic(known as behavior) to scopes, which are subsets of the model.

> **A controller should:**
> 
>  - Contain the logic required to initialize the scope
>  - Contain the logic/behaviors required by the view to present data from the scope
>  - Contain the logic/behaviors required to update the scope based on the user interaction      
> 
> **Should not:**
>   
>  - Contain logic that manipulates the DOM (that is the job of the view)
>  - Contain logic that manages the persistence of data (that is the job of the model)
>  - Manipulate data outside of the scope

**Views** are defined using HTML elements that are enhanced and that generate HTML by the use of data bindings and directives. It is the AngularJS directives that make views so flexible, and they transform HTML elements into the foundation for dynamic web apps.

> **Virws should:**
> 
>  - Contain the logic and markup required to present data to the user  
> **Should not:**
> 
>  - Contain complex logic （this is better placed in a controller)
>  - Contain logic that creates, stores or manipulates the domain model