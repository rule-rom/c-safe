# Garden-Core Enforcer

**The Clang AST Validation Engine**

## What It Does

Garden-Core parses your C code through Clang AST and validates against EDN contracts from the Registry.

## Integration

### 1. Install

```bash
# Via cargo
cargo install garden-core-enforcer

# Or via bb (Babashka)
bb -m garden.enforcer your_code.c
```

### 2. Tag Your Code

```c
/* [[garden:intent(C-SAFE-01)]] */
if (input_size < BUFFER_MAX) {
    memcpy(target_buffer, input_stream, input_size);
}
/* [[/garden:intent]] */
```

### 3. Run Validation

```bash
clang -Xclang -ast-dump=json -fsyntax-only your_code.c > ast.json
bb -m garden.enforcer ast.json
```

## Result

- ✅ **VALIDATED** — Code passes AST vs EDN check
- ❌ **REJECTED** — Mismatch detected (prune)

---

[← Back to Home](index.md)
