# Strict DI Mode

### What is it ?

This option will ensure that all of you angular stuff is annoted to avoid error.  
You really should enable it when planning to use minification.

You just have to put this attribute on the `ng-app` of your application.

**Note:** do not use it in production, you could save some time on first load. 

### Example

```
<div ng-app="myApp" 
     ng-strict-di>

  <!-- your app here -->
  
</div>
```

### Coverage

You need to inject your dependencies everywhere.  
It is very important to do it from the start of the project.

For example, you must include the depencencies in:

- Controllers
- Services and Factories
- Directives
- Filters
- ...

The syntax with `$inject` is exactly the same.

**Note:** you must also include the dependencies into the resolve of the ui-states (array like).

### Controller injection

```
(function (angular) {
    'use strict';

    angular
        .module('myApp')
        .controller('exampleCtrl', exampleCtrl);

    exampleCtrl.$inject = [
        'example' 
    ];

    function exampleCtrl(example) {
    
       // Code...
       
    }
    
}(window.angular));
```

### Resolve state injection

```
.state('example', {
     url         : '/example',
     templateUrl : 'example.html',
     controller  : 'exampleCtrl',
     controllerAs: 'vm',
     resolve     : {
         example: [
             'exampleService',
             function (exampleService) {
                 return exampleService.getExample();
             }
         ]
     }
})
```

### Substitute solution

You didn't use the correct syntax, you are at the end of the project, and you need to minify your code ?

That could be a long and not funny way to refacto your code to avoid the mess.  

So, take a look at this [substitute solution](../../grunt/uglify.md#fix-injection-error).

### Want more ?

[See the official documentation](https://docs.angularjs.org/guide/di#using-strict-dependency-injection)
