---
tags:
  - frontend
  - тема/html
  - тема/a11y
type: тема
---

# HTML и доступность

[[Frontend Roadmap|← карта]] · смежное: [[CSS и вёрстка]]

> [!info] Зачем
> HTML — фундамент. Семантичная разметка = доступность, SEO и поддерживаемость «бесплатно». Это недооценивают, а спрашивают на собесах.

## 🟢 Intern → [[Frontend · Intern]]
- Структура документа: `<!DOCTYPE>`, `html`, `head`, `body`, мета-теги.
- Блочные и строчные элементы.
- Семантические теги: `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`.
- Текст: заголовки `h1–h6`, `p`, списки `ul/ol/li`.
- Ссылки `a`, изображения `img` (и зачем нужен `alt`).
- Таблицы: `table`, `thead`, `tbody`, `tr`, `th`, `td`.

## 🟡 Junior → [[Frontend · Junior]]
- **Формы**: `form`, `input` (типы), `textarea`, `select`, `button`, `label`.
- Атрибуты: `name`, `value`, `placeholder`, `required`, `disabled`.
- Валидация формы средствами HTML.
- `data-*` атрибуты.
- Метатеги для адаптива (`viewport`) и SEO (`description`).

## 🟠 Junior+ / Middle → [[Frontend · Junior+]] · [[Frontend · Middle]]
- **Доступность (a11y)**:
  - ARIA-роли и атрибуты (`aria-label`, `aria-hidden`, `role`).
  - Навигация с клавиатуры, `tabindex`, фокус.
  - Контраст, размеры зон клика.
  - Семантика как основа a11y (правильные теги вместо `div` на всё).
- Скринридеры — как ими проверять.
- Микроразметка (Schema.org) для SEO.
- Оптимизация изображений: `srcset`, `picture`, lazy-loading, форматы (WebP/AVIF).

## 🧪 Проверь себя
- Чем `section` отличается от `div`?
- Зачем `label` привязывать к `input`?
- Что покажет скринридер на `<img>` без `alt`?
- Как сделать интерактивный элемент доступным с клавиатуры?

## 📎 Ресурсы
См. [[Ресурсы — Frontend]] — раздел HTML/a11y (MDN, web.dev, A11y Project).
