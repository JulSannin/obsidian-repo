---
tags:
  - frontend
  - тема/javascript
type: тема
---

# JavaScript

[[Frontend Roadmap|← карта]] · смежное: [[TypeScript]] · [[React и экосистема]]

> [!important] Главное
> JavaScript — это **фундамент, который нельзя пропускать**. Хороший JS важнее любого фреймворка. На собесах middle спрашивают язык, а не React.

## 🟢 Intern → [[Frontend · Intern]]
- Переменные: `let`, `const`, `var` (и почему `var` не используют).
- Типы данных: string, number, boolean, null, undefined, object, symbol, bigint.
- Операторы, приведение типов, `==` vs `===`.
- Условия (`if`, `switch`, тернарник), циклы (`for`, `while`, `for…of`).
- Функции: объявление, выражение, стрелочные, параметры по умолчанию.
- Массивы и объекты, доступ к свойствам.
- Базовые методы массивов: `map`, `filter`, `forEach`, `find`, `reduce`.
- DOM: `querySelector`, изменение содержимого, `addEventListener`.

## 🟡 Junior → [[Frontend · Junior]]
- **Область видимости**, hoisting, **замыкания (closures)**.
- `this`, контекст вызова, `call`/`apply`/`bind`.
- **Прототипы** и прототипное наследование, классы.
- Деструктуризация, spread/rest, опциональная цепочка `?.`, `??`.
- **Асинхронность**: callbacks → Promises → `async/await`.
- `fetch`, работа с JSON, `try/catch`, обработка ошибок.
- **Event loop**, микро- и макрозадачи (call stack, task queue).
- ES-модули: `import`/`export`.
- Всплытие и делегирование событий, `event` объект.

## 🟠 Junior+ / Middle → [[Frontend · Junior+]] · [[Frontend · Middle]]
- Иммутабельность, чистые функции, функциональные приёмы.
- `Map`, `Set`, `WeakMap`, генераторы, итераторы.
- Глубже event loop: `Promise.all/race/allSettled`, очереди.
- Debounce, throttle, мемоизация — и зачем.
- Сборка мусора, утечки памяти, замыкания как причина утечек.
- `Proxy`, `Reflect`, геттеры/сеттеры.
- Web API: `localStorage`, `IntersectionObserver`, `AbortController`, Web Workers.
- Особенности движка (V8), как код оптимизируется (база).

## 💡 Примеры кода

**Замыкание** — функция «помнит» своё окружение:
```js
function makeCounter() {
  let count = 0;
  return () => ++count;
}
const next = makeCounter();
next(); // 1
next(); // 2  — count живёт между вызовами
```

**Event loop** — порядок выполнения:
```js
console.log('1');
setTimeout(() => console.log('2'), 0);          // макрозадача
Promise.resolve().then(() => console.log('3')); // микрозадача
console.log('4');
// Вывод: 1, 4, 3, 2 (микрозадачи раньше макро)
```

**async/await + обработка ошибок**:
```js
async function getUser(id) {
  try {
    const res = await fetch(`/api/users/${id}`);
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    return await res.json();
  } catch (e) {
    console.error('Не удалось загрузить:', e);
    return null;
  }
}
```

**Цепочка методов массива** (декларативно вместо циклов):
```js
const total = orders
  .filter(o => o.paid)
  .map(o => o.amount)
  .reduce((sum, x) => sum + x, 0);
```

**debounce** — отложить вызов до паузы (поиск, ресайз):
```js
function debounce(fn, delay) {
  let t;
  return (...args) => {
    clearTimeout(t);
    t = setTimeout(() => fn(...args), delay);
  };
}
```

## 🧪 Проверь себя
- Что выведет код с `setTimeout` в цикле с `var` vs `let`?
- Объясни замыкание на примере счётчика.
- Чем отличаются микро- и макрозадачи?
- Как работает `this` в стрелочной функции?
- Что такое hoisting? Что происходит с `let` до объявления (TDZ)?

## 📎 Ресурсы
[[Ресурсы — Frontend]] — learn.javascript.ru (Кантор), MDN, «You Don't Know JS», javascript.info.
