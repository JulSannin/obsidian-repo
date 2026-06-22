---
tags:
  - frontend
  - тема/typescript
type: тема
---

# TypeScript

[[Frontend Roadmap|← карта]] · база: [[JavaScript]] · применение: [[React и экосистема]]

> [!info] Зачем
> TypeScript — стандарт индустрии. Типы ловят ошибки до рантайма, делают код самодокументируемым и упрощают рефакторинг. Без TS на middle уже не берут.

> [!warning] Сначала JS
> Не начинай TS, пока не уверен в [[JavaScript]]. TS — это надстройка над JS, а не замена.

## 🟡 Junior → начало (после уверенного JS)
- Зачем нужны типы, как подключить TS.
- Базовые типы: `string`, `number`, `boolean`, `array`, `object`, `any`, `void`, `null`, `undefined`.
- Аннотации переменных, параметров и возвращаемых значений функций.
- `interface` vs `type`.
- Опциональные (`?`) и readonly свойства.

## 🟠 Junior+ → [[Frontend · Junior+]]
- Объединения (`A | B`) и пересечения (`A & B`).
- Литеральные типы, enum, кортежи.
- **Дженерики** `<T>` — переиспользуемые типы.
- **Утилитные типы**: `Partial`, `Required`, `Pick`, `Omit`, `Record`, `ReturnType`.
- **Сужение типов** (narrowing): type guards, `typeof`, `in`, `instanceof`.
- `unknown` vs `any` (и почему `any` — зло).
- Типизация React: пропсы, `useState<T>`, события, рефы.
- Типизация ответов API.

## 🔵 Middle → [[Frontend · Middle]]
- Условные типы, `infer`, mapped types.
- Template literal types.
- Дискриминированные объединения.
- Настройка `tsconfig` (strict-режим, пути, target).
- Декларации типов для сторонних библиотек (`.d.ts`, `@types`).
- Продвинутая типобезопасность доменной логики, брендированные типы.

## 💡 Примеры кода

**Дженерик** — тип сохраняется на выходе:
```ts
function first<T>(arr: T[]): T | undefined {
  return arr[0];
}
first([1, 2, 3]);  // number | undefined
first(['a', 'b']); // string | undefined
```

**Утилитные типы** — не дублируем описание:
```ts
interface User { id: number; name: string; email: string; }

type UserPreview = Omit<User, 'email'>; // { id; name }
type UserPatch   = Partial<User>;       // все поля опциональны
type UsersById   = Record<number, User>;
```

**Сужение типа (narrowing)** — TS понимает ветки:
```ts
function printId(id: string | number) {
  if (typeof id === 'string') {
    console.log(id.toUpperCase()); // здесь id: string
  } else {
    console.log(id.toFixed(0));    // здесь id: number
  }
}
```

**Типизация пропсов React**:
```tsx
type ButtonProps = {
  label: string;
  onClick: () => void;
  variant?: 'primary' | 'ghost'; // опционально, union
};

function Button({ label, onClick, variant = 'primary' }: ButtonProps) {
  return <button className={variant} onClick={onClick}>{label}</button>;
}
```

## 🧪 Проверь себя
- Когда `interface`, а когда `type`?
- Что делает `Omit<User, 'id'>`?
- Чем `unknown` лучше `any`?
- Напиши дженерик-функцию, возвращающую первый элемент массива с сохранением типа.

## 📎 Ресурсы
[[Ресурсы — Frontend]] — TypeScript Handbook, Total TypeScript (Matt Pocock), type-challenges.
