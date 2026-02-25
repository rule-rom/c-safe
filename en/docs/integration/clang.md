# Clang AST Integration

## Generate AST

```bash
clang -Xclang -ast-dump=json -fsyntax-only code.c > ast.json
```

## Validate

```bash
bb -m garden.enforcer ast.json
```
