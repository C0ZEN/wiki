# angular.forEach VS for

### Why ?

If you ask yourself which one is the best, this *battle* is for you.

First of all, check out [forEach](../methods/forEach.md).  
Make sure to understand why I recommand to use `angular.forEach` instead of `myArray.forEach`.

**Note:** this *battle* is only in case of arrays, use [forEach](../methods/forEach.md) for objects !

**Reminder:**

```
angular.forEach(elements, function(element, key) {

  // ...
  
}, context);

for (var i = 0, length = 10; i < length; i++) {

   // ...

}
```

### forEach: advantages

You can loop through arrays and objects.  
**for loop** is only for arrays.

You can access easily to the `key` and `value`.

The code syntax is more appropriate to read it.

### for: advantages

The **for loop** is the fastest way to loop through an array.  
Far better than **forEach**.

You can `break` it to increase the speed.  
Moreover, you can add alias to break a specific layer in case of multiple nested loops.

If the loop is in a function with a return statement, you can use `return` to stop the loop and return directly the data.  
It's the equivalent to use `break` then `return`.

**Note:** the **forEach** can't do such a thing because the return is in the anonymous function context.

You can use at your advantage the reverse loop (from end to start, usually when you need to remove elements and continue the loop).

### Bonus

You should never recalculate the condition in the **for loop**.

**Bad:**

```
var myArray = [0, 0, 0];
for (var i = 0; i < myArray.length; i++) {

   // ...

}
```

**Good:**

```
var myArray = [0, 0, 0];
for (var i = 0, length = myArray.length; i < length; i++) {

   // ...

}
```
