# Variable Life-Cycle Tracking (Пастух)

**Intent ID:** `:variable-lifecycle-tracking`
**Статус:** 🚧 Draft
**Версия:** 0.1

## Описание

Контракт для отслеживания полного жизненного цикла переменных: рождение, активность и смерть. Каждая переменная должна быть «помечена» от объявления до освобождения/выхода из области видимости.

## EDN Спецификация (Draft)

```edn
{:intent :variable-lifecycle-tracking
 :entities {:var {:type "T" :role :tracked-variable}}
 :lifecycle [
   ;; Фаза 1: Рождение переменной
   {:phase :birth
    :op :declare :target :var
    :tag "garden:birth"}

   ;; Фаза 2: Активное использование
   {:phase :active
    :op :access :target :var :mode [:read :write]
    :tag "garden:active"}

   ;; Фаза 3: Смерть переменной
   {:phase :death
    :op [:free :scope-exit] :target :var
    :tag "garden:death"}
 ]
 :invariants [
   ;; Правило: каждая переменная должна иметь birth
   {:require :birth :for-each :var}

   ;; Правило: death следует после всех active
   {:order [:birth :active* :death]}

   ;; Правило: переменная без tracked lifecycle — бесхозная
   {:forbid :untracked-variable}]
 :tags {:birth "garden:birth"
        :active "garden:active"
        :death "garden:death"}}
```

## Пример использования

### ✅ Валидный код

```c
/* [[garden:intent(variable-lifecycle-tracking)]] */
void process_data() {
    /* [[garden:birth(buffer)]] */
    char *buffer = malloc(64);
    
    if (buffer != NULL) {
        /* [[garden:active(buffer, MEM-WRITE)]] */
        memset(buffer, 0, 64);
        
        /* [[garden:active(buffer, MEM-READ)]] */
        size_t len = strlen(buffer);
        
        // ... logic ...

        /* [[garden:death(buffer)]] */
        free(buffer);
        buffer = NULL;
    }
}
/* [[/garden:intent]] */
```

### ❌ Нарушение: нет birth

```c
/* [[garden:intent(variable-lifecycle-tracking)]] */
void missing_birth() {
    // ОШИБКА: переменная объявлена без garden:birth
    char *buffer = malloc(64);
    free(buffer);
}
/* [[/garden:intent]] */
```

### ❌ Нарушение: нет death

```c
/* [[garden:intent(variable-lifecycle-tracking)]] */
void missing_death() {
    /* [[garden:birth(buffer)]] */
    char *buffer = malloc(64);
    // ОШИБКА: нет garden:death перед выходом
}
/* [[/garden:intent]] */
```

### ❌ Нарушение: бесхозная переменная

```c
/* [[garden:intent(variable-lifecycle-tracking)]] */
void untracked_variable() {
    // ОШИБКА: переменная без тегов жизненного цикла
    int x = 42;
    use(x);
}
/* [[/garden:intent]] */
```

## Правило Пастуха

> **Каждая переменная должна быть «помечена» от рождения до смерти.**
>
> Переменная без отслеживаемого жизненного цикла считается **бесхозной** (orphan) и будет удалена (prune) на этапе валидации.

## Теги жизненного цикла

| Тег | Описание | Когда использовать |
|-----|----------|-------------------|
| `[[garden:birth(VAR_NAME)]]` | Точка объявления/инициализации | Сразу после объявления переменной |
| `[[garden:active(VAR_NAME, INTENT_ID)]]` | Операция чтения/записи | Каждое использование переменной |
| `[[garden:death(VAR_NAME)]]` | Освобождение/выход из области | `free()`, `delete`, выход из scope |

## Статус разработки

Этот интент находится в разработке. Протокол требует глубокой интеграции с Clang AST для трассировки переменных.

## Ссылки

- [Garden-Core Enforcer](../tools/enforcer.md)
- [Безопасность памяти](memory_safety.md)
- [Агентский Контракт](../spec/agent_contract.md)

---

**Bake the Future. Build the Substrate.** 🛠️⚡️
