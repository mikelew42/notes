When I learned Angular about a year ago, the documentation was terrible.  You need to understand an overview of all the building blocks of an Angular app, before trying to wrap your head around the syntax.

### The Building Blocks
- *module*s are containers for the rest:
  - *directive*s
  - *controller*s
  - *service*s, *provider*s, and *factory*s
  - *views*
  - *filters*

### and some important concepts
- Demystifying *Dependency Injection*
- Controllers have *$scope*

While modules are the largest building block, and serve as containers for the rest, I'll start with directives 

### Directives


# Dependency Injection



You've already seen one 

Controllers provide a *$scope* variable which is a critical concept to understand.

Views are just html, and they allow some Angular magic (called directives).



# Directives

This is simply a selector (element, attribute, or class) that is paired with some JavaScript, very similar to how you would `$('select.something')` with jQuery, and then do something with it.  Most of the Angular framework's functionality is created using directives, so you'll hear about them a lot.  Just remember, a directive is usually just a custom attribute that does something special.  For example, the `ng-app` directive (which looks like:  `<div ng-app="MyModule">`) is your starting point that kicks off the whole Angular system.

> It would make more sense if this directive was called ng-module

Some other very handy html attribute directives that ship with Angular:
- `ng-class` lets you toggle classes based on javascript expressions
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

