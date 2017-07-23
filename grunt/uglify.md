# uglify task

### Fix injection error

Sometimes, you are just fucked up by your own code.  
That kind of problems could and will happen.

If you need to uglify your code, the default behavior is to rename all the variables and function names.

That could be a huge mess if you didn't use the array or $inject syntax to avoid re-writing.

Please, next time make sure to read [Strict DI Mode](../angular/config/strictDiMode.md).

Anyway, I have a substitute solution for you.

In the options of the uglify task, you could use the option `mangle` to `false` to avoid rewriting names.

**Example:**

- Find all the JavaScript files in the *app* folder 
- Exclude the template files *.tpl.js*
- Minify them into a files named *main.min.js*
- Put the file into the *release* folder

```
uglify: {
   example: {
       options: {
           mangle: false
       },
       files: {
           '<%= release %>/main.min.js': [
               '<%= app %>/**/*.js',
               '!<%= app %>/**/*.tpl.js'
           ]
       }
   }
}
```
