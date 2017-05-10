# Angular scope

## tl;dr
We will use `controller as` because it is newer and has better ability to nest controllers. We are showing you `scope` because there will be a lot of examples on the internet that use it and you will want to know how to translate between scope and controller as.

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
```
<div ng-controller="mySecondController">
  {{oneThing}}
</div>
```

### controller as
```
myApp.controller('mySecondController', function($scope) {
  $scope.oneThing = 'This is my first thing';
});
```

## Nesting Controller As

## Resources

[http://stackoverflow.com/questions/16619740/angular-should-i-use-this-or-scope](http://stackoverflow.com/questions/16619740/angular-should-i-use-this-or-scope)

[http://codetunnel.io/angularjs-controller-as-or-scope/](http://codetunnel.io/angularjs-controller-as-or-scope/)

[https://johnpapa.net/angularjss-controller-as-and-the-vm-variable/](https://johnpapa.net/angularjss-controller-as-and-the-vm-variable/)



