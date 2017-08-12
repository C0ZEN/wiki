# Limit lines

Most of the time, you just don't care about how many line your text is.  
Nevertheless, modern apps with i18n require to make sure that your text fit in one line or a limit of max line.

# Solution

To do that, add these properties to your element.

```
overflow: hidden;
text-overflow: ellipsis;
-webkit-line-clamp: 2;
display: -webkit-box;
-webkit-box-orient: vertical;
word-break: break-all;
```

**Note:** `-webkit-line-clamp` is the limit of line you want.
