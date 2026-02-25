# Bounds Check

**Intent ID:** `:bounds-checked-access`

## Example

```c
/* [[garden:intent(C-SAFE-02)]] */
if (index < array_size) {
    value = array[index];
}
/* [[/garden:intent]] */
```
