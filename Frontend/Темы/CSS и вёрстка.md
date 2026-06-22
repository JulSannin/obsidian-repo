---
tags:
  - frontend
  - тема/css
type: тема
---

# CSS и вёрстка

[[Frontend Roadmap|← карта]] · смежное: [[HTML и доступность]]

> [!info] Зачем
> CSS — это где новички теряют больше всего времени. Понимание каскада, box model и Flexbox/Grid экономит часы борьбы с «почему оно не центрируется».

## 🟢 Intern → [[Frontend · Intern]]
- Подключение CSS, селекторы (тег, класс, id, атрибут, псевдоклассы).
- **Специфичность, каскад, наследование** — почему стиль «не применяется».
- **Box model**: `margin`, `border`, `padding`, `content`, `box-sizing`.
- `display`: block / inline / inline-block / none.
- `position`: static / relative / absolute / fixed / sticky.
- Единицы: px, %, em, rem, vh/vw.
- Цвета, шрифты, `text`-свойства, фоны.
- **Flexbox** — основной инструмент: `justify-content`, `align-items`, `flex`, `gap`.

## 🟡 Junior → [[Frontend · Junior]]
- **CSS Grid**: `grid-template`, области, `fr`, авторазмещение.
- Адаптив: media-queries, mobile-first подход.
- Псевдоэлементы `::before`/`::after`.
- Transitions и базовые `@keyframes` анимации.
- **CSS-переменные** (custom properties).
- Препроцессор **Sass** (вложенность, переменные, миксины) **или** утилитарный **Tailwind CSS**.
- Методология **BEM** для именования классов.

## 🟠 Junior+ / Middle → [[Frontend · Junior+]] · [[Frontend · Middle]]
- Современные фичи: `clamp()`, `min()`/`max()`, container queries, `:has()`, нативный nesting, `aspect-ratio`.
- CSS Modules / CSS-in-JS (styled-components, emotion) / Tailwind в проде.
- Тёмная тема, дизайн-токены, дизайн-система.
- Производительность: что вызывает reflow/repaint, `will-change`, `content-visibility`.
- Кроссбраузерность и graceful degradation.
- Логические свойства, RTL-вёрстка.

## 💡 Примеры кода

**Центрирование — 3 способа**:
```css
/* 1. Flexbox */
.parent { display: flex; justify-content: center; align-items: center; }

/* 2. Grid — короче всего */
.parent { display: grid; place-items: center; }

/* 3. Absolute + transform */
.child {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
}
```

**Адаптивная сетка без media-queries** (карточки сами переносятся):
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 16px;
}
```

**Гибкий размер через `clamp()`** (min, идеал, max):
```css
.card  { width: clamp(280px, 40vw, 560px); }
.title { font-size: clamp(1.5rem, 4vw, 3rem); }
```

## 🧪 Проверь себя
- Чем `em` отличается от `rem`?
- Как отцентрировать блок и по горизонтали, и по вертикали (3 способа)?
- Когда Grid, а когда Flexbox?
- Что такое схлопывание margin'ов (margin collapse)?
- Как работает `position: sticky`?

## 📎 Ресурсы
[[Ресурсы — Frontend]] — игры Flexbox Froggy / Grid Garden, MDN, web.dev, Kevin Powell.
