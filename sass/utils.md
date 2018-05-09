# Utils

## Class interpolation

Use the `#{$...}` syntax to escape the SASS variables.

```sass
$name: 'wonderful';

.prefix-#{$name}-sufix {
  // ...
}
```

## Loop

```sass
@for $i from 0 through 1 {
  // ...
}
```

## Dynamic loop on map

```sass
$my-map: (0: 'hello', 1: 'you');

@for $i from 0 through length($my-map) {
  content: map_get($my-map, $i);
}
```
