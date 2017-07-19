# angular.element

### When ?

Everytime you want to access to a DOM element, you should wrap your selector into `angular.element`.

The syntax is better and it will avoid problems with JQuery or jqLite.

### Example

```
angular.element(document.getElementById('myElement'));
```

### Want more ?

[See the official documentation](https://docs.angularjs.org/api/ng/function/angular.element)
