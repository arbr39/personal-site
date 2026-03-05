# Personal Site — laksarkhip.ru

Минималистичный личный блог на Astro. Посты в Markdown, хостинг на GitHub Pages, автопубликация превью в Telegram-канал.

## Tech Stack

- **Astro 5** — статический генератор
- **MDX** — расширенный Markdown (опционально)
- **TypeScript** (strictest)
- **GitHub Pages** — хостинг
- **GitHub Actions** — CI/CD + Telegram-уведомления

## Команды

```bash
npm run dev        # Dev-сервер (localhost:4321)
npm run build      # Сборка в ./dist
npm run preview    # Превью билда
```

## Архитектура проекта

```
src/
├── content/
│   └── blog/              # MD/MDX посты (frontmatter: title, description, pubDate, heroImage)
├── components/            # Astro-компоненты (Header, Footer, BaseHead, FormattedDate)
├── layouts/
│   └── BlogPost.astro     # Layout для постов
├── pages/
│   ├── index.astro        # Главная — список постов
│   ├── about.astro        # Страница About
│   ├── blog/
│   │   ├── index.astro    # Список постов
│   │   └── [...slug].astro # Динамический роут поста
│   └── rss.xml.js         # RSS-лента
├── styles/
│   └── global.css         # Глобальные стили
├── assets/                # Изображения (обрабатываются Astro image)
├── consts.ts              # SITE_TITLE, SITE_DESCRIPTION
└── content.config.ts      # Схема контента (Zod)
public/                    # Статические файлы (favicon, шрифты)
```

## Конфигурация

- `astro.config.mjs` — site URL, интеграции (mdx, sitemap)
- `src/consts.ts` — название сайта и описание
- `src/content.config.ts` — Zod-схема frontmatter для постов

## Формат поста

Файл: `src/content/blog/post-slug.md`

```markdown
---
title: "Заголовок"
description: "Краткое описание (используется для превью и Telegram)"
pubDate: 2026-03-05
updatedDate: 2026-03-06        # опционально
heroImage: "../../assets/img.jpg"  # опционально
---

Текст поста...
```

## Контент

- **Язык**: русский
- **Темы**: VCPay (продукт, бизнес), личная жизнь, путешествия — всё кроме политики
- **Стиль**: минимализм, текст + фото/скрины
- **Референс дизайна**: borischerny.com

## Telegram-интеграция

Канал "Laks" (ID: 2246102249, ~50 подписчиков).
При деплое GitHub Action отправляет в канал:
- Заголовок + описание (из frontmatter)
- UTM-ссылка: `https://laksarkhip.ru/blog/{slug}?utm_source=telegram&utm_medium=channel&utm_campaign=new_post`

## Домен

- **laksarkhip.ru** → GitHub Pages
- DNS: CNAME запись на `<username>.github.io`

## Git Workflow

- `main` — продакшен, автодеплой через GitHub Actions
- Conventional Commits
