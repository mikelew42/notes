When I learned Angular about a year ago, the documentation was terrible.  You need to understand an overview of all the building blocks of an Angular app, before trying to wrap your head around the syntax.

Table of Contents
- The building blocks:  *modules*, *directives*, *controllers*, *services*, *views*, and *filters*.
- Demystifying *Dependency Injection*
- Controllers have *$scope*

# Dependency Injection

Some building blocks can depend on, and inject, other building blocks.  This concept is known as *dependency injection*, and is found frequently in Angular code.  This is really just "including something else", and I'll go over that a bit too.

You've already seen one 

Controllers provide a *$scope* variable which is a critical concept to understand.

Views are just html, and they allow some Angular magic (called directives).



# Directives

This is simply a selector (element, attribute, or class) that is paired with some JavaScript, very similar to how you would `$('select.something')` with jQuery, and then do something with it.  The Angular framework itself is largely composed of directives, for example, the `ng-app` directive (which is just an html attribute that looks like this:  `<div ng-app="MyModule">`) is your starting point that kicks off the whole Angular system.

> Note, Angular likes to create a bunch of different names for the same concept.  For example, ng-app must reference a module.  It would make more sense if this directive was ng-module.  You'll find this a lot with Angular...

Some other very handy html attribute directives that ship with Angular:
- `ng-class` lets you easily bind html class names to javascript variables and expressions
- `ng-show` and `ng-if` let you easily show/hide and render/remove from DOM, based on JS expression
- `ng-click` lets you execute a JS expression (such as calling a function) when this element is clicked

See [this page](https://docs.angularjs.org/api) to find a list of directives and some examples.

# Modules

Modules are containers for the other building blocks (directives, controllers, services, etc).  As I mentioned, the entry point for Angular into your webpage is the usage of the `ng-app` directive to access a module you have defined using the `angular.module` function. 

You can package sets of functionality (often directives work with controllers and services) into modules for reuse, and then include any number of modules in your new module. 

For example:

```
// Create a new module
var myModule = angular.module('myModule', ['myOtherModule', 'ChatRoomModule']);
```

In this example, you would have previously defined myOtherModule and ChatRoomModule (which each can have any number of directives, controllers, services, etc defined in them), and now you're basically just adding these building blocks to your new app.  This is called `dependency injection`, and is a frequent pattern in Angular.  When injecting services into your controllers, however, there's an added step.

