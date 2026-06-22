---
tags:
  - frontend
  - тема/network
  - тема/browser
type: тема
---

# Сеть и HTTP

[[Frontend Roadmap|← карта]] · смежное: [[JavaScript]]

> [!info] Зачем
> Frontend живёт в браузере и общается с сервером. Понимать, как летят данные и как рисуется страница, — то, что отличает «верстальщика» от инженера.

## 🟢 Intern → [[Frontend · Intern]]
- Клиент ↔ сервер, что такое браузер и веб-сервер.
- Что такое URL, домен, IP, DNS (на пальцах).
- Что происходит при вводе адреса в браузере (классический вопрос).
- HTTP vs HTTPS — зачем шифрование.

## 🟡 Junior → [[Frontend · Junior]]
- **HTTP-методы**: GET, POST, PUT, PATCH, DELETE.
- **Статус-коды**: 2xx, 3xx, 4xx, 5xx (минимум 200, 201, 301, 400, 401, 403, 404, 500).
- Заголовки запроса/ответа, тело, `Content-Type`.
- **REST API** — принципы, как читать документацию.
- `fetch` и работа с JSON → [[JavaScript]].
- Вкладка **Network** в DevTools.
- **CORS** — почему возникает ошибка и кто её чинит.

## 🟠 Junior+ → [[Frontend · Junior+]]
- **Авторизация**: сессии vs токены, **JWT**, где хранить (cookie httpOnly vs localStorage и риски).
- OAuth 2.0 на уровне «как работает вход через Google».
- **Браузер изнутри**: Critical Rendering Path, как страница парсится и рисуется.
- Кэширование HTTP (`Cache-Control`, ETag).
- Хранилища: `localStorage`, `sessionStorage`, cookies, IndexedDB.
- Безопасность: **XSS**, **CSRF** — суть и базовая защита.

## 🔵 Middle → [[Frontend · Middle]]
- HTTP/2, HTTP/3 (обзорно), почему быстрее.
- **WebSockets** и real-time (SSE).
- **GraphQL** — хотя бы как потребитель (queries, mutations).
- CDN, оптимизация загрузки (preload, prefetch, сжатие).
- Web Vitals (LCP, INP, CLS) и как их улучшать.
- Глубже безопасность: CSP, SameSite cookies, защита токенов.

## 🧪 Проверь себя
- Чем PUT отличается от PATCH?
- Что значит 401 vs 403?
- Откуда берётся CORS-ошибка и где её исправлять?
- Где безопаснее хранить JWT и почему?
- Что такое XSS и как от него защититься?

## 📎 Ресурсы
[[Ресурсы — Frontend]] — MDN HTTP, web.dev (performance), «High Performance Browser Networking».
