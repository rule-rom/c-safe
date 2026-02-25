# C-SAFE 🌿 — Иммунная Система для Кода

> **«Останови стохастический шум в своём C-стеке.»**

## 🏛️ Миссия

**C-SAFE** — это ретроактивный слой иммунизации для C легаси кода. Мы не переписываем — мы **тегируем и валидируем** через Garden-Core Enforcer.

## 🎯 Целевая Аудитория

- **C-Разработчики** уставшие от багов памяти
- **@cursor_ai** пользователи желающие детерминированный код
- **GNU maintainers** сохраняющие наследие C

## 🔗 Крючок

> Современные «безопасные» языки хотят похоронить C. Мы хотим **освободить** его от стохастического шума.

---

## 🛡️ Как Это Работает

```
┌─────────────────────────────────────────────────────────┐
│  C-Legacy Code + Garden-Tags                            │
│                                                         │
│  /* [[garden:intent(C-SAFE-01)]] */                    │
│  if (size < BUFFER_MAX) {                              │
│      memcpy(dest, src, size);                          │
│  }                                                      │
│  /* [[/garden:intent]] */                              │
│                                                         │
│         ↓ Garden-Core Enforcer                          │
│         ↓ (Clang AST + EDN Contract)                    │
│                                                         │
│  ✅ VALIDATED → Production Ready                       │
│  ❌ REJECTED → Pruned (No Tag = No Code)               │
└─────────────────────────────────────────────────────────┘
```

---

## 📚 Документация

### 📖 Манифест
- [Главная](index.md)
- [Garden-Core](garden-core.md)

### 📜 Реестр EDN
- [Обзор](registry/index.md)
- [Безопасность памяти](registry/memory_safety.md)
- [Контроль границ](registry/bounds_check.md)
- [Защита указателей](registry/pointer_guards.md)
- [Валидация типов](registry/type_validation.md)

### 🛠️ Инструменты
- [AST Integration](tools/ast_integration.md)
- [Enforcer](tools/enforcer.md)
- [Lisp Setup](tools/lisp_setup.md)

### 🔌 Интеграция
- [Cursor AI](integration/cursor.md)
- [Clang AST](integration/clang.md)

### 📋 Спецификация
- [Agent Contract](spec/agent_contract.md)
- [System Prompt](spec/system_prompt.md)

### 💎 Экосистема
- [Обзор экосистемы](ecosystem.md)

---

**Bake the Future. Build the Substrate.** 🛠️⚡️
