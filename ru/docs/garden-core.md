# Garden-Core Enforcer

**Движок Валидации через Clang AST**

## Что Он Делает

Garden-Core парсит ваш C код через Clang AST и валидирует против EDN контрактов из Реестра.

## Интеграция

### 1. Установка

```bash
# Via cargo
cargo install garden-core-enforcer

# Or via bb (Babashka)
bb -m garden.enforcer your_code.c
```

### 2. Тегирование Кода

```c
/* [[garden:intent(C-SAFE-01)]] */
if (input_size < BUFFER_MAX) {
    memcpy(target_buffer, input_stream, input_size);
}
/* [[/garden:intent]] */
```

### 3. Запуск Валидации

```bash
clang -Xclang -ast-dump=json -fsyntax-only your_code.c > ast.json
bb -m garden.enforcer ast.json
```

## Результат

- ✅ **VALIDATED** — Код проходит проверку AST vs EDN
- ❌ **REJECTED** — Обнаружено несоответствие (prune)

---

[← Назад на Главную](index.md)
