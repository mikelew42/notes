When I learned Angular about a year ago, the documentation was terrible.  You need to understand an overview of all the building blocks of an Angular app, before trying to wrap your head around the syntax.

#### The Building Blocks
- *modules* are containers for the rest:
  - *directives*
  - *controllers*
  - *services*, *providers*, and *factories*
  - *views*
  - *filters*

#### and some important concepts
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

This essentially just adds the building blocks from those modules onto your new module.  This is called `dependency injection`, and is a frequent pattern in Angular.  

### Dependency Injection

To include building blocks in other building blocks, you use "dependency injection".  You'll see this pattern (from [the guide](https://docs.angularjs.org/guide/di)) frequently:

```
someModule.controller('MyController', ['$scope', 'dep1', 'dep2', function($scope, dep1, dep2) {
  ...
  $scope.aMethod = function() {
    ...
  }
  ...
}]);
```

You're defining a new controller and specifying several dependencies that are "injected" into the function that defines the controller.  Usually you'll inject dependencies that are defined by Angular, but you can also find third party plugins (modules) that provide dependencies you can inject, or create your own.  Now let's talk about

## Controllers and $scope

Controllers are basically just JavaScript objects that are attached to certain DOM elements.  The way this works is a little tricky, because its largely dependent on views.  And, the view system kinda sucks, because you can only have 1 view container, and you can't nest them.
