# angular.copy

When you have some data binded to a view (scope), you can change it from everywhere.  
That's all the beauty, right ?

But, sometimes, you need to edit this data and later get the original one.

**First approach:**

The first approach is to save a copy of it into a new variable.

`vm.myUserCopy = vm.myUser;`

But the binding is always present !  
If you edit `myUserCopy`, it will update `myUser` and vice-versa.

**Solution:**

The easier solution is to use `angular.copy()`.

This will create a deep copy of the source to make sure that no data binding is active.

**Note:** use it for arrays or objects only.

### Example

```
vm.myUser = {
  fname: 'Geoffrey',
  lname: 'Testelin',
  nickname: 'C0ZEN'
};

// First syntax
vm.myUserCopy = angular.copy(vm.myUser);

// Second syntax
angular.copy(vm.myUser, vm.myUserCopy);
```

### Want more ?

[See the official documentation](https://docs.angularjs.org/api/ng/function/angular.copy)
