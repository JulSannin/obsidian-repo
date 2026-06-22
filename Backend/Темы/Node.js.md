---
tags:
  - backend
  - тема/nodejs
type: тема
---

# Node.js

[[Backend Roadmap|← карта]] · база: [[JavaScript]] · [[TypeScript]]

> [!info] Зачем
> Node.js — это JavaScript вне браузера, на сервере. Для фронтендера это **самый быстрый вход в backend**: язык тот же, переиспользуешь всё знание JS, асинхронности и npm.

> [!important] Сначала JS
> Node — не отдельный язык, а среда выполнения JS. Без уверенного [[JavaScript]] (замыкания, промисы, event loop) сюда рано.

## 🟢 Intern → [[Backend · Intern]]
- Что такое Node.js, V8, чем серверный JS отличается от браузерного (нет DOM/window, есть `process`, `fs`, `__dirname`).
- Запуск файла: `node app.js`.
- **Модули**: CommonJS (`require`/`module.exports`) и ESM (`import`/`export`).
- npm/pnpm: `package.json`, скрипты, зависимости, `npx`.
- Встроенные модули: `fs` (файлы), `path`, `os`, `http`.
- Менеджер версий: nvm/fnm; `nodemon` для авто-перезапуска.
- Поднять HTTP-сервер на чистом `http`, затем на **Express**.

## 🟡 Junior → [[Backend · Junior]]
- **Express**: маршруты, middleware, `req`/`res`, роутеры.
- Асинхронность на сервере: `async/await`, обработка ошибок, `Promise.all`.
- Потоки (streams) и буферы — базово (чтение больших файлов, загрузки).
- Event loop на сервере (libuv, неблокирующий I/O) — почему Node быстрый на I/O.
- Переменные окружения (`process.env`, `dotenv`).
- Логирование (pino/winston), а не `console.log` в проде.
- Перевод проекта на **TypeScript** → [[TypeScript]].
- Базовое тестирование (Vitest/Jest + Supertest) → [[Серверная архитектура и DevOps]].

## 💡 Примеры кода

**HTTP-сервер на чистом Node** (понять основу):
```js
import http from 'node:http';

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'application/json' });
  res.end(JSON.stringify({ message: 'Привет с сервера' }));
});

server.listen(3000, () => console.log('http://localhost:3000'));
```

**То же на Express** (так пишут в реальности):
```js
import express from 'express';

const app = express();
app.use(express.json()); // парсинг JSON-тела

app.get('/api/health', (req, res) => {
  res.json({ status: 'ok' });
});

app.listen(3000, () => console.log('Сервер на :3000'));
```

**Middleware** — функция в цепочке обработки запроса:
```js
function logger(req, res, next) {
  console.log(`${req.method} ${req.url}`);
  next(); // передать управление дальше
}
app.use(logger);
```

## 🧪 Проверь себя
- Чем серверный JS отличается от браузерного?
- Что такое middleware в Express?
- Почему Node хорош для I/O-нагрузки, но не для тяжёлых вычислений?
- В чём разница CommonJS и ESM?

## 📎 Ресурсы
[[Ресурсы — Backend]] — nodejs.org/docs, Express docs, The Odin Project (NodeJS).
