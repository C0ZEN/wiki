# $compileProvider

### What is it ?

This provider is used to configure the behavior of somes directives and debug stuff.

### debugInfoEnabled

You should always enable it on development and disable it on production.

**Description:**

It can helps to debug the DOM by adding some stuff in it like:

- `ng-binding`, `ng-scope` and `ng-isolated-scope` CSS class
- `$binding` data property containing an array of the binding expressions
- `ngBind` and `ngBindHtml` attributes
- `ng-if` comments

Obviously, this option will slow down the application and it is useless in production.  
So, **disable** it !

### Example

```
$compileProvider.debugInfoEnabled(false);
```

### Bonus

If you want to debug easily a production which have this option disable,  
You can enter `angular.reloadWithDebugInfo();` in your browser console to enable the debug.

### Want more ?

[See the official documentation](https://docs.angularjs.org/api/ng/provider/$compileProvider)
