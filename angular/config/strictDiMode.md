# Strict DI Mode

### What is it ?

This option will ensure that all of you angular stuff is annoted to avoid error.  
You really should enable it when planning to use minification.

**Description:**

You just have to put this attribute on the `ng-app` of your application.

### Example

```
<div ng-app="myApp" 
     ng-strict-di>

  <!-- your app here -->
  
</div>
```

### Want more ?

[See the official documentation](https://docs.angularjs.org/guide/di#using-strict-dependency-injection)
