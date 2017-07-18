# angular.noop

### Why ?

A function could have a required parameter which is type of function.

Sometimes, you just don't give a shit about the callback of this function.

**Bad solution:**

The bad solution in those cases is to give an empty parameter (like null or sort of).

Because the code could evolve or because it can cause a bug if the function is called without safety.

**Better solution:**

A better solution is to use an anonymous function like `function () {}`.

**Best solution:**

angular.noop

### Example

**Declaration:**

```
/**
 * @param {function} callback > callback function [required]
 */
function aSimpleFunction (callback) {
   callback();
}
```

**Usage:**

```
aSimpleFunction(angular.noop);
```

### Bonus

Check below a safety solution to avoid error.

**Declaration:**

```
/**
 * @param {function} callback > callback function [required]
 */
function aSimpleFunction (callback) {
   angular.isFunction(callback) ? callback() : null;
}
```

**Note:** [check out](isFunction.md) to know more about it.

### Want more ?

[See the official documentation](https://docs.angularjs.org/api/ng/function/angular.noop)
