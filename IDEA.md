# Personal Site — laksarkhip.ru

## Концепция

Минималистичный личный сайт-блог. Посты пишутся в Markdown в репозитории, публикуются на сайте. При деплое Telegram-бот автоматически отправляет превью + UTM-ссылку в канал "Laks" (~50 подписчиков).

## Решения

| Вопрос | Ответ |
|--------|-------|
| Домен | laksarkhip.ru |
| Язык контента | Русский |
| Стиль | Минимализм (референс: borischerny.com) |
| Формат постов | Markdown в репозитории |
| Фокус контента | Текст + фото/скрины из VCPay |
| Telegram-синхро | Автоматически: превью + UTM-ссылка при деплое |

## Tech Stack

- **Astro** — статический генератор сайта (нативный MD, быстрый, минимализм)
- **GitHub Pages** — бесплатный хостинг, домен laksarkhip.ru
- **GitHub Actions** — CI/CD: сборка + отправка превью в Telegram-бот

## Темы контента

- VCPay — продукт, бизнес, скриншоты, инсайты
- Личная жизнь — путешествия, события, еда
- Любые темы кроме политики

## Структура сайта

### Страницы
- **Главная** — хронологический список постов (дата + заголовок + теги)
- **About** — краткое био, ссылки
- **Пост** — текст + изображения, теги

### Навигация
- Лого/имя → главная
- About
- Telegram-канал (ссылка)

## Telegram-интеграция

При пуше нового поста в main:
1. GitHub Actions собирает сайт
2. Деплоит на GitHub Pages
3. Telegram-бот отправляет в канал:
   - Заголовок поста
   - Первые 2-3 предложения (превью)
   - UTM-ссылка: `https://laksarkhip.ru/post-slug?utm_source=telegram&utm_medium=channel&utm_campaign=new_post`

## Структура репозитория (план)

```
personal-site/
├── src/
│   ├── content/
│   │   └── posts/          # MD-файлы постов
│   ├── layouts/
│   ├── pages/
│   └── styles/
├── public/
│   └── images/             # Фото и скрины
├── .github/
│   └── workflows/
│       └── deploy.yml      # Build + deploy + telegram notify
├── astro.config.mjs
└── package.json
```

## Формат поста (frontmatter)

```markdown
---
title: "Заголовок поста"
date: 2026-03-05
tags: [vcpay, product]
image: /images/post-slug/cover.png
description: "Краткое описание для превью и Telegram"
---

Текст поста...
```

## TODO

- [ ] Инициализировать Astro-проект
- [ ] Настроить минимальную тему (референс borischerny.com)
- [ ] Настроить GitHub Pages + домен laksarkhip.ru
- [ ] Создать GitHub Action (build + deploy + telegram bot)
- [ ] Создать Telegram-бота для публикаций
- [ ] Написать первый пост
