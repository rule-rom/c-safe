# Pointer Guards

**Intent ID:** `:pointer-arithmetic`

## Example

```c
/* [[garden:intent(C-SAFE-03)]] */
if (ptr + offset < segment_end) {
    result = *(ptr + offset);
}
/* [[/garden:intent]] */
```
