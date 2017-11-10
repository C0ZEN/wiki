# Notify and subscribe

### About ?

This part is a pure custom way to manage listener in my services and factories.

The controller will execute callback when the data change.  
The listener life cycle will be managed by the service.

### Example

Let's take for example the current language of your application.

When you want to get or update the current language, you should do it by calling a dedicated service.  
The service will have a `get` and `set` methods.

The current language value will be stored in an `angular.constant` file.

The MVP question here is how could I execute multiple functions from multiple controllers when this value change ?  
The obvious solution is to listen for an event.

### So how does it works ?

Each controller where you want to receive this event should call a method `subscribe`.  
This methods as the `$scope` as first parameter and the `callback` function as second parameter.

The `$scope` is useful to automatically take care of the litener destruction directly from the service.  
The `callback` function is the function executed when the current language change.

Instead of using a watcher in the service, we will execute a function to `notify` that the current language value from the `angular.constant` file has changed.

This function should be called on each location of the code where you edit the current language.

This `notify` function will send an event which is listened by the `broadcast` function.

### Code example

````
function get() {
    return angular.copy(currentLanguageConstant.currentLanguage);
}

function set($newCurrentLanguage) {
    currentLanguageConstant.currentLanguage = $newCurrentLanguage;
    notify();
}

function subscribe(scope, callback) {
    var handler = $rootScope.$on('currentLanguageService:currentLanguageChanged', function() {
        callback({
            newCurrentLanguage: currentLanguageConstant.currentLanguage
        });
    });
    scope.$on('$destroy', handler);
}

function notify() {
    $rootScope.$emit('currentLanguageService:currentLanguageChanged');
}
````
