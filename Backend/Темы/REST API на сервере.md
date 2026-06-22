---
tags:
  - backend
  - тема/api
  - тема/rest
type: тема
---

# REST API на сервере

[[Backend Roadmap|← карта]] · смежное: [[Сеть и HTTP]] · [[Node.js]]

> [!info] Зачем
> API — точка, где фронтенд встречается с бэкендом. Раньше ты **потреблял** API из React ([[Сеть и HTTP]]), теперь учишься его **строить**. Это центральный навык backend-джуна.

## 🟡 Junior → [[Backend · Junior]]

### Проектирование
- Ресурсы и эндпоинты (`/users`, `/users/:id`, `/users/:id/posts`).
- Правильные **HTTP-методы**: GET (читать), POST (создать), PUT/PATCH (изменить), DELETE (удалить).
- Правильные **статус-коды**: 200, 201, 204, 400, 401, 403, 404, 409, 500.
- Именование (существительные, множественное число, без глаголов в URL).
- Версионирование API (`/api/v1/...`).

### Реализация (Express)
- Маршруты и роутеры, разбиение по ресурсам.
- **Middleware**: логирование, парсинг тела, аутентификация → [[Аутентификация и безопасность]].
- Контроллеры и сервисы (логика отдельно от роутов) → [[Серверная архитектура и DevOps]].
- Работа с `params`, `query`, `body`.
- **CORS** — настроить доступ для фронтенда.

### Надёжность
- **Валидация входных данных** (Zod / Joi) — не доверяй клиенту никогда.
- **Централизованная обработка ошибок** (error-middleware).
- Единый формат ответа и ошибок.
- Пагинация, фильтрация, сортировка списков.
- Документация: **Swagger / OpenAPI** (базово).
- Идемпотентность и почему она важна (база).

## 💡 Примеры кода

**CRUD-роут с валидацией** (Express + Zod):
```ts
import { Router } from 'express';
import { z } from 'zod';

const router = Router();

const createUserSchema = z.object({
  name: z.string().min(1),
  email: z.string().email(),
});

router.post('/users', async (req, res, next) => {
  try {
    const data = createUserSchema.parse(req.body); // валидация
    const user = await userService.create(data);
    res.status(201).json(user); // 201 Created
  } catch (err) {
    next(err); // в централизованный обработчик
  }
});

export default router;
```

**Централизованная обработка ошибок** (последний middleware):
```ts
app.use((err, req, res, next) => {
  if (err instanceof z.ZodError) {
    return res.status(400).json({ error: 'Невалидные данные', details: err.issues });
  }
  console.error(err);
  res.status(500).json({ error: 'Внутренняя ошибка сервера' });
});
```

## 🧪 Проверь себя
- Когда POST, а когда PUT/PATCH?
- Что вернуть при успешном создании ресурса? (201)
- Почему нельзя доверять данным с клиента?
- Где обрабатывать ошибки — в каждом роуте или централизованно?
- Что такое middleware и в каком порядке они выполняются?

## 📎 Ресурсы
[[Ресурсы — Backend]] — Express docs, «REST API Design», Zod docs, Swagger/OpenAPI.
