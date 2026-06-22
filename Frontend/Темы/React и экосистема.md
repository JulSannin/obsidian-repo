---
tags:
  - frontend
  - тема/react
type: тема
---

# React и экосистема

[[Frontend Roadmap|← карта]] · база: [[JavaScript]] · [[TypeScript]]

> [!important] Когда начинать
> Только после уверенного [[JavaScript]]. React — это библиотека на JS; без понимания языка ты будешь копировать код, не понимая. React — самый востребованный фреймворк, поэтому он в этой карте (альтернативы: Vue, Angular, Svelte — принципы переносимы).

## 🟡 Junior → [[Frontend · Junior]]
### Основы
- JSX и как он превращается в JS.
- Компоненты (функциональные), композиция, переиспользование.
- **Пропсы** — передача данных вниз.
- **Состояние**: `useState`.
- **Эффекты**: `useEffect` (загрузка данных, подписки, очистка).
- Списки и `key`, условный рендеринг.
- Обработка событий, формы (controlled inputs).
- Подъём состояния (lifting state up).

### Экосистема
- **React Router** — клиентская навигация.
- Запросы к API из компонента, состояния loading/error/success.
- Создание проекта через **Vite**.

## 🟠 Junior+ → [[Frontend · Junior+]]
- Хуки: `useRef`, `useMemo`, `useCallback`, `useReducer`, `useContext`.
- **Кастомные хуки** — выносим и переиспользуем логику.
- Правила хуков, массив зависимостей, ловушки `useEffect`.
- **Серверное состояние**: TanStack Query (кэш, рефетч, инвалидация).
- **Клиентское состояние**: Zustand или Redux Toolkit.
- Контекст для темы/локали/авторизации.
- Базовая оптимизация ре-рендеров (`memo`, мемоизация).

## 🔵 Middle → [[Frontend · Middle]]
- **Как React работает под капотом**: virtual DOM, reconciliation, батчинг, роль ключей.
- Паттерны: compound components, render props, провайдеры, HOC.
- Производительность: профайлер, code splitting, `lazy`/`Suspense`, виртуализация (react-window).
- Формы уровня прода: React Hook Form + валидация (Zod).
- **SSR/SSG и мета-фреймворк Next.js** (App Router, server components — обзорно).
- Тестирование компонентов → [[Тестирование]].
- Доступность компонентов, управление фокусом.
- Error boundaries, обработка ошибок на уровне UI.

## 💡 Примеры кода

**Кастомный хук** — выносим логику загрузки (с защитой от гонок):
```tsx
function useFetch<T>(url: string) {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    let alive = true;
    setLoading(true);
    fetch(url)
      .then(r => r.json())
      .then(d => { if (alive) setData(d); })
      .catch(e => { if (alive) setError(String(e)); })
      .finally(() => { if (alive) setLoading(false); });
    return () => { alive = false; }; // очистка при размонтировании
  }, [url]);

  return { data, loading, error };
}
```

**Использование** — компонент остаётся чистым:
```tsx
function Users() {
  const { data, loading, error } = useFetch<User[]>('/api/users');

  if (loading) return <p>Загрузка…</p>;
  if (error)   return <p>Ошибка: {error}</p>;

  return (
    <ul>
      {data?.map(u => <li key={u.id}>{u.name}</li>)}
    </ul>
  );
}
```

> [!warning] Частая ошибка джунов
> `key={index}` ломает рендер при изменении порядка списка — используй стабильный `id`. И не клади `useEffect` туда, где можно обойтись вычислением при рендере.

## 🧪 Проверь себя
- Зачем нужен `key` в списках и почему не index?
- В чём разница `useMemo` и `useCallback`?
- Когда `useEffect` лишний (частая ошибка джунов)?
- Что вызывает ре-рендер компонента?
- Чем серверное состояние отличается от клиентского?

## 📎 Ресурсы
[[Ресурсы — Frontend]] — react.dev (офиц. доки!), TanStack Query docs, Next.js Learn.
