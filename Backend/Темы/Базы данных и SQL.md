---
tags:
  - backend
  - тема/database
  - тема/sql
type: тема
---

# Базы данных и SQL

[[Backend Roadmap|← карта]] · применение: [[REST API на сервере]]

> [!important] Сердце backend
> Базы данных важнее любого фреймворка. 80% работы backend — это грамотно хранить и доставать данные. SQL спрашивают на **каждом** собеседовании.

## 🟢 Intern → [[Backend · Intern]]
- Зачем нужны БД, реляционные (SQL) vs нереляционные (NoSQL).
- Таблицы, строки, столбцы, типы данных.
- **Первичный ключ** (primary key), уникальность.
- **CRUD на SQL**:
  - `SELECT` — выборка, `WHERE`, `ORDER BY`, `LIMIT`.
  - `INSERT` — добавление.
  - `UPDATE` — изменение.
  - `DELETE` — удаление.
- Простые `JOIN` (объединение таблиц).
- Установить и подключиться к **PostgreSQL** (psql / GUI вроде DBeaver).

## 🟡 Junior → [[Backend · Junior]]
- **Связи**: один-к-одному, один-ко-многим, многие-ко-многим (через промежуточную таблицу).
- **Внешний ключ** (foreign key), целостность данных.
- Агрегатные функции: `COUNT`, `SUM`, `AVG`, `GROUP BY`, `HAVING`.
- Виды `JOIN`: INNER, LEFT, RIGHT.
- **Индексы** — зачем и когда (ускорение чтения).
- **Нормализация** базово (чтобы не дублировать данные).
- **Транзакции** и ACID (база) — атомарность операций.
- **ORM / Query Builder** из Node:
  - **Prisma** (рекомендуется для TS — типобезопасно).
  - Альтернативы: Knex, Drizzle, TypeORM, либо чистый драйвер `pg`.
- **Миграции** схемы (версионирование структуры БД).
- Знакомство с **NoSQL** (MongoDB) — когда документная БД уместна.

## 💡 Примеры кода

**SQL — основные операции**:
```sql
-- Создать таблицу
CREATE TABLE users (
  id    SERIAL PRIMARY KEY,
  name  TEXT NOT NULL,
  email TEXT UNIQUE NOT NULL
);

-- CRUD
INSERT INTO users (name, email) VALUES ('Анна', 'anna@mail.com');
SELECT * FROM users WHERE email = 'anna@mail.com';
UPDATE users SET name = 'Анна П.' WHERE id = 1;
DELETE FROM users WHERE id = 1;

-- JOIN: посты вместе с авторами
SELECT posts.title, users.name AS author
FROM posts
JOIN users ON users.id = posts.user_id;
```

**Запрос из Node через Prisma** (типобезопасно):
```ts
const user = await prisma.user.create({
  data: { name: 'Анна', email: 'anna@mail.com' },
});

const posts = await prisma.post.findMany({
  where: { published: true },
  include: { author: true }, // подтянуть связанного автора
});
```

## 🧪 Проверь себя
- Чем PRIMARY KEY отличается от FOREIGN KEY?
- Когда нужен индекс и какова его цена?
- Что такое транзакция и зачем она?
- Чем INNER JOIN отличается от LEFT JOIN?
- Когда выбрать NoSQL вместо SQL?

## 📎 Ресурсы
[[Ресурсы — Backend]] — PostgreSQL Tutorial, SQLBolt, Prisma docs, «SQL за 10 минут».
