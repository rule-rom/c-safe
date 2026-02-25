# Защита Указателей

**Intent ID:** `:pointer-arithmetic`

## Пример

```c
/* [[garden:intent(C-SAFE-03)]] */
if (ptr + offset < segment_end) {
    result = *(ptr + offset);
}
/* [[/garden:intent]] */
```
