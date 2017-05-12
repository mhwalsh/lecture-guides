# Angular Routing

_These notes originally from [antauth](https://github.com/antauth)_

In single page applications (SPAs), we often want to load new content without reloading the page.

Angular utilizes hash urls (e.g. http://localhost:3000/#/home.html) to allow us to handle our routes on the client. This works because browsers ignore everything after the #. With Angular routing, we can use what the browser ignores to show our users the content they requested.

## Using ngRoute

1. Include the source for angular-route in `index.html` under the source for angular.
2. Include the `ngRoute` module as a dependency for our angular app module.
3. Use `ng-view` to mark the section of the `index.html` page where content will change based on route.
4. Define your routes  in a `config` function using `$routeProvider`.

## More detail/what's new

### ngRoute
An [Angular module](https://www.npmjs.com/package/angular-route) that we use to perform *client-side routing*.

```JS
var app = angular.module('someApp', ['ngRoute']);
```

### ng-view
Marks which section of the page should change when the route changes

```HTML
<ng-view></ng-view>
```

### $routeProvider
An angular service provided by `ngRoute` module, allows us to setup our client-side routes and their behavior.

**app.config** allows us to set configurations for our application, like our routes.

```JS
app.config(function($routeProvider) {
  $routeProvider.when('/', {
    templateUrl: 'views/pages/default.html',
    controller: 'defaultController as defCtrl'
  })
  .otherwise({ redirectTo: '/'});
});
```

### $locationProvider
We use this service to allow us to use non-hash URLs.

```JS
app.config(function($routeProvider, $locationProvider) {
  $routeProvider.when('/', {
    templateUrl: 'views/pages/default.html',
    controller: 'defaultController as defCtrl'
  })
  .otherwise({ redirectTo: '/'});

  $locationProvider.html5Mode(true);
});
```

Additionally you will need to have a `<base>` tag in your `index.html`. This can go in the header after the `src` tags.

```
<base href="/">
```

If you don't have it, you might get an error like this: [https://docs.angularjs.org/error/$location/nobase](https://docs.angularjs.org/error/$location/nobase)