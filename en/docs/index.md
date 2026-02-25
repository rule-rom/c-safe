# C-SAFE 🌿 — The Software Immune System

> **"Stop the stochastic noise in your C-stack."**

## 🏛️ The Mission

**C-SAFE** is the retroactive immunization layer for C legacy code. We don't rewrite — we **tag and validate** through Garden-Core Enforcer.

## 🎯 Target Audience

- **C-Developers** tired of memory bugs
- **@cursor_ai** users who want deterministic code
- **GNU maintainers** preserving the C heritage

## 🔗 The Hook

> Modern "safe" languages want to bury C. We want to **liberate** it from stochastic noise.

---

## 🛡️ How It Works

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

## 📚 Documentation

### 📖 Manifesto
- [Home](index.md)
- [Garden-Core](garden-core.md)

### 📜 EDN Registry
- [Overview](registry/index.md)
- [Memory Safety](registry/memory_safety.md)
- [Bounds Check](registry/bounds_check.md)
- [Pointer Guards](registry/pointer_guards.md)
- [Type Validation](registry/type_validation.md)

### 🛠️ Tools
- [AST Integration](tools/ast_integration.md)
- [Enforcer](tools/enforcer.md)
- [Lisp Setup](tools/lisp_setup.md)

### 🔌 Integration
- [Cursor AI](integration/cursor.md)
- [Clang AST](integration/clang.md)

### 📋 Specification
- [Agent Contract](spec/agent_contract.md)
- [System Prompt](spec/system_prompt.md)

### 💎 Ecosystem
- [Ecosystem Overview](ecosystem.md)

---

**Bake the Future. Build the Substrate.** 🛠️⚡️
