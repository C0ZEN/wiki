# New scope in a directive

It's difficult to give you a theorical example with benefits.

I just figure it out that you can create a new scope in a scope.

It helps me only one time, so I will give you the example.

### Example

I wanted to create a feed of alerts (like notifications and toasts).  
These elements should be added directly in the DOM to increase the performances (instead of using an `ng-repeat` for example).

The first step is obvious, create a new directive to create an alert.

The second step is to create a factroy with an `add` method.  
This methods will create a new alert directive and then append it in the DOM.

The third step is to create a new directive used like a container for the alerts.  
This directive will be called in the index (root) and only one time.  

If we look deeper in the code of this directive, it will create a template of the alert directive, compile the scope with the attributes and finally append the alert in the DOM.  
The template is a simple HTML file with alert directive creation in it.

And that my friends, was the hard part.  
If you understand what I made, the data-binbind is still active.  
So, when I add a first alert, it's perfect, but when I add a second one, the first one's scope is updated by the second one's scope.

We need at this moment, a new scope.  
That's simple the best way (unbind and :: annotation is not always working).

```
function add($event, alert) {

  // Create a new instance of the template
  $templateRequest('Alert.template.html').then(function (html) {
  
    // Create a new scope with the alert data
    var newScope = scope.$new(true);
    newScope.alert = angular.copy(alert);

    // Compile the scope in the template
    var newAlert = $compile(html)(newScope);
    
    // Add the directive in the DOM
    angular.element(document.getElementById("rs-alert-container")).append(newAlert).unbind();
  });
}
```
