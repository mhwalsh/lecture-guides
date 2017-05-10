# Angular $scope

## tl;dr
We will use `controller as` because it is newer and has ability to nest controllers more cleanly. We are showing you `$scope` because there will be a lot of examples on the internet that use it and you will want to know how to translate between scope and controller as.

## Controller As

### index.html
```
<div ng-controller="myFirstController as first">
  {{first.oneThing}}
</div>
```

### controller as
```
myApp.controller('myFirstController', function() {
  // view model
  var vm = this;
  vm.oneThing = 'This is my first thing';
});
```

## scope 

### index.html
You don't need to name your controller as anything. Less typing here, but things get messy when you want to nest controllers later.

```
<div ng-controller="mySecondController">
  {{oneThing}}
</div>
```

### controller as
You need to inject `$scope` into the controller.

```
myApp.controller('mySecondController', function($scope) {
  $scope.oneThing = 'This is my first thing';
});
```

## Nesting Controller As

### index.html
With controller as we can refer to our controllers by name. This allows us to nest controllers if we need and refer to the specifically even if they have the same name.
```
<div ng-controller="myFirstController as first">
  {{first.oneThing}}
  <div ng-controller="myNestedController as nested">
    {{nested.nestedThing}}
    {{nested.oneThing}}
    {{first.oneThing}}
  </div>
</div>
```

### controller as
```
myApp.controller('myNestedController', function() {
  var vm = this;
  vm.nestedThing = 'Here is a nested thing!'
  vm.oneThing = 'This is our first thing inside nested'
});
```

## Resources

[http://stackoverflow.com/questions/16619740/angular-should-i-use-this-or-scope](http://stackoverflow.com/questions/16619740/angular-should-i-use-this-or-scope)

[https://johnpapa.net/do-you-like-your-angular-controllers-with-or-without-sugar/](https://johnpapa.net/do-you-like-your-angular-controllers-with-or-without-sugar/)

[http://codetunnel.io/angularjs-controller-as-or-scope/](http://codetunnel.io/angularjs-controller-as-or-scope/)

[https://johnpapa.net/angularjss-controller-as-and-the-vm-variable/](https://johnpapa.net/angularjss-controller-as-and-the-vm-variable/)



