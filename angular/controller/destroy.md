# Destroy

You should always be careful about the speed of a digest in Angular.

That notion is too much left for dead in Angular app.

### Listeners

There is not much to discuss. 
You should always destroy the listeners you had instancied.

Below the list of elements you should destroy manually:

- $rootScope.$on(...)
- $scope.$watch(...)
- $scope.$interval(...)
- $window.addEventListener(...)

### Syntax

I recommand you to centralize all the stuff you want to destroy in a method.

For both controllers and directives, you should call a method when the scope is destroy.  
This method will destroy all the listeners.

### $on and $watch

To make it easier to maintain, I use the array way to manage the listeners.  
Each time I call `$rootScope.$on(...)` and `$scope.$watch(...)`, I push the promise in an array.

It's a beautiful thing to do because you just don't care about the quantity on listeners you use, you just push them and that's all.

**Example:**

```
// Array of listeners
var listeners = [];

// Push every listener in the array
listeners.push($rootScope.$on('aRandomEvent', angular.noop));
listeners.push($scope.$watch('aRandomValue', angular.noop));

// Watch for scope destruction event
scope.$on('$destroy', destroy);

// Function to loop throught the listeners array
// Destroy all of them
function destroy() {
  angular.forEach(listeners, function (listener) {
	  listener();
	});
}
```

### $interval

You could use the same way as **$on** and **$watch** to manage these.

**Example:**

```
// Array of intervals
var intervals = [];

// Push every interval in the array
intervals.push($scope.$interval(angular.noop));
intervals.push($scope.$interval(angular.noop));

// Watch for scope destruction event
scope.$on('$destroy', destroy);

// Function to loop throught the listeners array
// Destroy all of them
function destroy() {
  angular.forEach(intervals, function (interval) {
	  interval();
	});
}
```

### $window.addEventListener

I don't have a shortcut for that, sadly.  
Just never forget to remove the listeners after an add.

**Example:**

```
// Add the listeners
$window.addEventListener('myEvent, angular.noop);

// Watch for scope destruction event
scope.$on('$destroy', destroy);

// Function to loop throught the listeners array
// Destroy all of them
function destroy() {
  $window.removeEventListener('myEvent, angular.noop);
}
```
