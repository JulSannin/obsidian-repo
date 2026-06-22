---
tags:
  - frontend
  - тема/git
  - тема/tooling
type: тема
---

# Git и инструменты

[[Frontend Roadmap|← карта]]

> [!info] Зачем
> Без Git не возьмут даже стажёром. Инструменты (сборка, линтеры) — повседневная гигиена кода в команде.

## 🟢 Intern → [[Frontend · Intern]]
### Git
- Что такое система контроля версий, репозиторий, коммит.
- `git init`, `clone`, `add`, `commit`, `status`, `log`.
- `push`, `pull`, связь с удалённым репозиторием.
- GitHub: аккаунт, репозиторий, GitHub Pages для деплоя.
- `.gitignore`.

### Окружение
- VS Code и полезные расширения.
- Терминал: навигация, базовые команды.
- DevTools браузера: Elements, Console.

## 🟡 Junior → [[Frontend · Junior]]
### Git
- **Ветки**: создание, переключение, merge.
- Разрешение конфликтов слияния.
- **Pull Request** и базовый командный флоу (feature branches).
- Осмысленные сообщения коммитов (Conventional Commits).

### Сборка и качество
- **npm / pnpm**: `package.json`, скрипты, dev/prod зависимости, semver.
- **Vite** — dev-сервер, сборка, переменные окружения.
- **ESLint** + **Prettier** — линтинг и автоформат.
- Что такое транспиляция и бандлинг (на уровне идеи).

## 🟠 Junior+ / Middle → [[Frontend · Junior+]] · [[Frontend · Middle]]
- Git глубже: `rebase`, `cherry-pick`, `stash`, `reset` vs `revert`, интерактивный rebase.
- Git-хуки (husky), lint-staged, commitlint.
- Стратегии ветвления: Git Flow, trunk-based.
- **CI/CD**: GitHub Actions — прогон тестов/линтеров, автодеплой.
- Монорепозитории (обзорно: pnpm workspaces, Turborepo).
- Анализ и оптимизация бандла, tree-shaking, code splitting.
- Мониторинг: Sentry; базовая аналитика.
- Контейнеризация (Docker) — обзорно, чтобы читать конфиги.

## 🧪 Проверь себя
- Чем `merge` отличается от `rebase`?
- Что делать, если запушил секрет в репозиторий?
- В чём разница `reset` и `revert`?
- Зачем нужен lock-файл (`package-lock` / `pnpm-lock`)?

## 📎 Ресурсы
[[Ресурсы — Frontend]] — Pro Git (книга), learngitbranching.js.org, доки Vite/ESLint.
