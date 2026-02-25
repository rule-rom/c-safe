# Memory Safety (C-SAFE)

**Intent ID:** `:safe-pointer-lifecycle`

## EDN Contract

```edn
{:intent :safe-pointer-lifecycle
 :rules [{:match :call :name "free"}
         {:ensure-next :assignment :value "NULL"}]}
```

## Example

```c
/* [[garden:intent(C-SAFE-01)]] */
free(ptr);
ptr = NULL;
/* [[/garden:intent]] */
```
