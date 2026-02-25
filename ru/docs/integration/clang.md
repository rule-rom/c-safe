# Clang AST Интеграция

## Генерация AST

```bash
clang -Xclang -ast-dump=json -fsyntax-only code.c > ast.json
```

## Валидация

```bash
bb -m garden.enforcer ast.json
```
