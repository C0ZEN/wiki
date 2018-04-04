# Scaffolding for a library

## Changelog

**Version        :** 1.0.0  
**Angular version:** 5.*  
**Last update    :** 04/04/2018

## Summary

- Seed
- Linters

### Seed

You should use a seed like [Angular Seed](https://github.com/angular/angular-seed) or at least the [Angular CLI](https://github.com/angular/angular-cli) to create the scaffolding of the application.  

**Example**

Install the Angular CLI:

```
npm install -g @angular/cli`
```

Then create your new project:

```
ng new PROJECT-NAME
cd PROJECT-NAME
ng serve
```

## Linters

### TSLint

Use **TSLinter** to help you maintain a good syntax for TypeScript.  
Create a `tslint.json` file on the root folder (which is already generated when creating a new project with Angular CLI).  
Copy this [sample](tslint.json) if you want a prebuild linter.

Then install the package if it is not installed yet:

```
npm install tslint --save-dev
```

**Using WebStorm**

You should enable the live TSLinter from WebStorm settings to ensure that the linter is always working and help you coding safer and faster.  
To do so, `CTRL + ALT + S` and search `TSLint`.  
Then check `Enable`.  
WebStorm will automatically search the corresponding configuration file.

### StyleLint

Use **StyleLint** to help you maintain a good syntax for your CSS.  
Create a `.stylelintrc` file on the root folder.  
Copy this [sample](.stylelintrc) if you want a prebuild linter.

Then install the package:

`npm install stylelint --save-dev`

**Using WebStorm**

You should enable the live StyleLint from WebStorm settings to ensure that the linter is always working and help you coding safer and faster.  
To do so, `CTRL + ALT + S` and search `StyleLint`.  
Then check `Enable`.  
WebStorm will automatically search the corresponding configuration file.
