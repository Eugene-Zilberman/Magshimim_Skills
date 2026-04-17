# ai-skills

> A curated collection of reusable prompts and instruction sets for AI models; focused on coding, writing, and autonomous agents.

![open to contributions](https://img.shields.io/badge/open%20to-contributions-7F77DD) ![LLM agnostic](https://img.shields.io/badge/LLM-agnostic-EF4444) ![MIT license](https://img.shields.io/badge/license-MIT-0F6E56)

---

## Что это такое

**Скилл** - это структурированный, переиспользуемый набор инструкций, который задаёт AI-модели чёткий способ решения конкретной задачи.

### Категории

| Папка | Содержимое |
|---|---|
| `coding/` | Ревью кода, рефакторинг, генерация тестов, отладка, commit-сообщения |
| `writing/` | Сделать AI-текст более естественным, подбор тона, перевод, суммаризация |
| `agents/` | Исследование, планирование, анализ данных, автономное выполнение задач |
| `templates/` | Шаблоны скиллов и руководство по добавлению |

---

## Как использовать

1. **Найдите** - откройте нужную категорию и выберите скилл
2. **Скопируйте** - возьмите промпт из блока `## Prompt`
3. **Используйте** - вставьте как системный промпт или инлайн-инструкцию
4. **Улучшите** - доработали? Открывайте merge request с обновлённой версией

---

## Формат скилла

Каждый файл скилла имеет следующую структуру:

```markdown
# Название скилла
**Category:** coding / writing / agents
**Works with:** Claude / GPT / any LLM
**Author:** github handle
**Last tested:** YYYY-MM

## Purpose
Одно предложение - что делает этот скилл.

## Prompt
[ сам промпт ]

## Notes
Нюансы, ограничения, особенности конкретных моделей.
```

---

## Избранные скиллы

### `writing` → humanize-text
Переписывает AI-сгенерированный текст так, чтобы он звучал естественно: корректирует ритм, словарный запас и разнообразие предложений.

### `coding` → code-review
Структурированное ревью кода: конвенции, оптимизация, документация, производительность и стиль.

### `coding` → write-tests
Генерирует полноценные юнит-тесты с учётом граничных случаев для любой функции или модуля.

### `agent` → researcher
Агент для глубокого исследования: разбивает тему на подвопросы, анализирует источники и возвращает структурированный результат с цитатами.

---

## Структура репозитория

```
ai-skills/
├── README.md
├── CONTRIBUTING.md
│
├── coding/
│   ├── code-review.md
│   ├── refactoring.md
│   ├── debug-assistant.md
│   ├── write-tests.md
│   └── git-commit-messages.md
│
├── writing/
│   ├── humanize-text.md
│   ├── tone-casual.md
│   ├── translate-ru-en.md
│   └── summarize.md
│
├── agents/
│   ├── researcher.md
│   ├── planner.md
│   └── data-analyst.md
│
├── templates/
│   └── SKILL_TEMPLATE.md
│
└── meta/
    ├── sources.md
    └── tools.md
```

---

## Как участвовать

**Добавить новый скилл** - скопируйте `templates/SKILL_TEMPLATE.md`, заполните и откройте Pull Request в нужную папку.

**Улучшить существующий** - нашли более удачную версию? Обновите промпт, пример и дату в поле *Last tested*.

**Добавить внешние источники** - нашли полезный скилл в интернете? Добавьте ссылку в `meta/sources.md` с кратким описанием.

**Сообщить о сломанном скилле** - откройте issue с указанием модели и даты. Промпты могут устаревать по мере обновления моделей.

---

Скиллы протестированы на Claude Sonnet и GPT-4o, если не указано иное. Результаты могут отличаться в зависимости от версии модели. Любые контрибьюции приветствуются. Цель репозитория - общая библиотека, которая экономит время всем.

## Инструкция по работе через partial clone и sparse-checkout

Этот режим удобен, если репозиторий большой, а разработчику нужна только конкретная часть проекта.

### 1. Клонировать репозиторий без полной загрузки всех файлов

```bash
git clone --filter=blob:none --sparse <repo_url>
cd <repo_name>
```

Что делает эта команда:
- `--filter=blob:none` не загружает содержимое всех файлов сразу
- `--sparse` включает sparse checkout

### 2. Указать, с какими папками нужно работать

```bash
git sparse-checkout set skills docs examples
```

После этого в рабочем дереве будут доступны в основном только указанные директории.

### 3. Создать отдельную ветку под задачу

```bash
git checkout -b feature/update-skill
```

### 4. Внести изменения и сохранить их

```bash
git add .
git commit -m "Update skill documentation"
git push -u origin feature/update-skill
```

### 5. Создать Pull Request в `main`

После push ветки нужно открыть Pull Request и влить изменения в `main` только через review.

---

## Полный пример

```bash
git clone --filter=blob:none --sparse <repo_url>
cd <repo_name>
git sparse-checkout set skills docs examples
git checkout -b feature/update-skill
# вносим изменения
git add .
git commit -m "Update skill documentation"
git push -u origin feature/update-skill
```

---

## Полезные команды для sparse-checkout

### Добавить еще одну папку

```bash
git sparse-checkout add templates
```

### Посмотреть текущий список путей

```bash
git sparse-checkout list
```

### Вернуться к полному рабочему дереву

```bash
git sparse-checkout disable
```

---

## Когда использовать partial clone и sparse-checkout

Используй этот подход, если:
- репозиторий большой
- разработчик работает только с одной частью проекта
- не нужно держать весь проект локально

Если проект маленький, обычно достаточно обычного `git clone` и работы через отдельную ветку.

---

## Рекомендуемые правила команды

- не работать напрямую в `main`
- всегда создавать отдельную ветку под задачу
- отправлять изменения только через Pull Request
- использовать `partial clone` и `sparse-checkout`, если нужен только кусок большого репозитория
- писать понятные commit message
- держать skills короткими, точными и хорошо структурированными