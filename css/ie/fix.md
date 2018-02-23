# IE Fix

You can find a bunch of solutions for Flex error on [Flexbugs](https://github.com/philipwalton/flexbugs).

## All versions

### Background-color inherit

Always use `transparent` instead of `inherit` for the `background-color` property.

```css
element {
  background-color: transparent;
}
```

## IE 11

### Min-height on flex-container with aligns center

When a container is flexible, align items on center and has a min-height, IE will not vertically center the children.  
To fix this behavior, instead of setting a min-height, set a height and a min-height with max-content value.

```css
.container {
  display        : flex;
  flex-direction : row;
  justify-content: flex-start;
  align-items    : center;
  height         : 4rem;
  min-height     : max-content;
}
```

## IE 10

## IE 9
