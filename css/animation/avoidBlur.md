# Avoir blur after animation

Sometimes, when you show something after an animation, the element is blur.

### Solution

The easy solution is to add these 3 properties to your element.

```
backface-visibility: hidden;
transform: translateZ(0);
-webkit-font-smoothing: subpixel-antialiased;
```

**Note:** the transform could be ignore, sometimes it doesn't change anything and worst, it could break your element position.
