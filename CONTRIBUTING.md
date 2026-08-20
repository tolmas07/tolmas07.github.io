# Contributing / Как внести вклад

## Архитектура веток

Репозиторий использует **двухветочную систему**:

| Ветка | Назначение | URL |
|---|---|---|
| `main` | Продакшен сайт | https://tolmas07.github.io/ |
| `test-improvements` | Тестовая среда для проверки изменений | https://tolmas07.github.io/test/ |

Деплой обеих веток происходит автоматически через GitHub Actions (`.github/workflows/static.yml`).

## Рабочий процесс (для AI-ассистентов)

**ВАЖНО: Все изменения СПЕРВА попадают в `test-improvements`, и только после подтверждения пользователя — в `main`.**

### Шаг 1: Переключение на тестовую ветку
```bash
git checkout test-improvements
```

### Шаг 2: Внесение изменений
Все правки делаются в ветке `test-improvements`.

### Шаг 3: Коммит и пуш в тестовую ветку
```bash
git add -A
git commit -m "описание изменений"
git push origin test-improvements
```

### Шаг 4: Проверка пользователем
Изменения доступны по адресу: https://tolmas07.github.io/test/

### Шаг 5: Мерж в main (только после подтверждения)
```bash
git checkout main
git merge test-improvements --no-edit
git push origin main
```

После мержа продакшен-сайт обновляется автоматически.

## Рабочий процесс (для людей)

### 1. Форкните репозиторий (для внешних участников)
Нажмите **Fork** на странице репозитория на GitHub.

### 2. Клонируйте репозиторий
```bash
git clone https://github.com/<ваш-username>/tolmas07.github.io.git
cd tolmas07.github.io
```

### 3. Создайте новую ветку
```bash
git checkout -b feature/описание-изменений
```

Используйте префиксы:
- `feature/` — новая функциональность
- `fix/` — исправление бага
- `docs/` — изменения в документации
- `style/` — изменения стилей

### 4. Внесите изменения и закоммитьте
```bash
git add .
git commit -m "Описание изменений"
```

### 5. Отправьте ветку на GitHub
```bash
git push origin feature/описание-изменений
```

### 6. Создайте Pull Request
- Перейдите на GitHub и нажмите **"Compare & pull request"**
- Заполните описание изменений
- Дождитесь одобрения от владельца репозитория

## Правила

- **Не пушите напрямую в `main`** — все изменения через ветку `test-improvements` или Pull Request
- **AI-ассистенты: ВСЕГДА пушите в `test-improvements` первыми**, ждите подтверждения, затем мержите в `main`
- Один PR — одна задача
- Пишите понятные описания коммитов
- Проверяйте тестовую версию перед мержем в main

## Структура проекта

```
├── index.html          # Главная страница
├── style.css           # Стили
├── translations.js     # Переводы (ru/en)
├── config.js           # Конфигурация (генерируется из GitHub Secrets)
├── CV.html             # Резюме (можно скачать с сайта)
├── images/             # Изображения
├── robots.txt          # SEO
├── sitemap.xml         # SEO
└── .github/
    └── workflows/
        └── static.yml  # GitHub Actions деплой
```
