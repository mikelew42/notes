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

## Directives

This is simply a selector (element, attribute, or class) that is paired with some JavaScript, very similar to how you would `$('select.something')` with jQuery, and then do something with it.  Most of the Angular framework's functionality is created using directives, so you'll hear about them a lot.  Just remember, a directive is usually just a custom attribute that does something special.  For example, the `ng-app` directive (which looks like:  `<div ng-app="MyModule">`) is your starting point that kicks off the whole Angular system.

> It would make more sense if this directive was called ng-module, because it must reference a module (there is no App building block)

Some other very handy html attribute directives that ship with Angular:
- `ng-class` lets you toggle classes based on javascript expressions
- `ng-show` and `ng-if` let you easily show/hide and render/remove from DOM, based on JS expression
- `ng-click` lets you execute a JS expression (such as calling a function) when this element is clicked

See [this page](https://docs.angularjs.org/api) to find a list of directives and examples.

# Modules

Modules are containers for the other building blocks.  As I mentioned, the entry point for Angular into your webpage is the usage of the `ng-app` directive to access a module you have defined using the `angular.module` function. 

You can package related building blocks into modules for reuse, and then include modules in other modules. 

For example:

```
// Create a new module
var myModule = angular.module('myModule', ['myOtherModule', 'ChatRoomModule']);
```

This essentially just adds the building blocks from those modules onto your new module.  This is called `dependency injection`, and is a frequent pattern in Angular.  When injecting services into your controllers, however, there's an added step.

### Dependency Injection

The example from [the guide](https://docs.angularjs.org/guide/di):

```
someModule.controller('MyController', ['$scope', 'dep1', 'dep2', function($scope, dep1, dep2) {
  ...
  $scope.aMethod = function() {
    ...
  }
  ...
}]);
```

You're defining a new controller and specifying several dependencies that are "injected" into the function that defines the controller.  Now let's talk about

## Controllers and $scope

Controllers contain the functionality 
