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

## 📚 Быстрые Ссылки

- [Garden-Core Интеграция](garden-core.md)
- [EDN Реестр](registry/memory_safety.md)
- [Cursor AI Настройка](integration/cursor.md)

---

**Bake the Future. Build the Substrate.** 🛠️⚡️
