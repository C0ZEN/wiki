# angular.forEach

### Why ?

This methods is **better** than the classic Javascript forEach method.

**Reminder:**

```
myArray.forEach(function(element, index, array) {

   // ...
   
});
```

**How's that better ?**

Because it can loop through objects, too !  
By this simple fact, it makes it **better**.

Moreover, because it filters object's keys with `hasOwnProperty` automatically !

It feels safe and sounds great.

### Example

```
angular.forEach(elements, function(element, key) {

  // ...
  
}, context);
```

### Want more ?

[See the official documentation](https://docs.angularjs.org/api/ng/function/angular.forEach)
