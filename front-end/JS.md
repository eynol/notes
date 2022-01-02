[Return to content](../index.md)

# Detect text overflow
```javascript
// Determines if the passed element is overflowing its bounds,
// either vertically or horizontally.
// Will temporarily modify the "overflow" style to detect this
// if necessary.
function checkOverflow(el)
{
   var curOverflow = el.style.overflow;

   if ( !curOverflow || curOverflow === "visible" )
      el.style.overflow = "hidden";

   var isOverflowing = el.clientWidth < el.scrollWidth 
      || el.clientHeight < el.scrollHeight;

   el.style.overflow = curOverflow;

   return isOverflowing;
}
```

## [].every(anyFunction) === true

```javascript
 [].every(x=>x===2)  # true
 [].every(String)   #true

```

[Ref:ecma-262-Array.prototype.every](https://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.16)

### reference:
[Ref:determine-if-an-html-elements-content-overflows](https://stackoverflow.com/questions/143815/determine-if-an-html-elements-content-overflows)


[Return to content](../index.md)
