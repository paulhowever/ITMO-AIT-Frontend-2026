# ЛР2 — Взаимодействие с внешним API + API (JSON-server) + авторизация

## Что внутри

- `client/` — статические страницы (HTML/CSS/JS), данные загружаются через API.
- `server/` — Node-сервер: раздаёт `client/` и API на `/api/*`.

## Запуск

Из папки `Labs/lab2/server`:

```bash
rm -rf node_modules package-lock.json
npm i
npm run seed:reset
npm run dev
```

Открыть в браузере:

- Главная: `http://localhost:3000/`
- Вход/регистрация: `http://localhost:3000/auth.html`

Учётка преподавателя (после `seed:reset`):

- email: `admin@example.com`
- password: `admin123`

## Что реализовано

- Каталог курсов из API (`GET /api/courses`) + фильтрация на клиенте по направлению, уровню и цене (диапазон min/max).
- Авторизация/регистрация через JWT (закрытые эндпоинты на сервере):
  - `POST /api/auth/register`
  - `POST /api/auth/login`
  - `GET /api/auth/me` (protected)
- Кабинет студента: список добавленных курсов и прогресс через `/api/enrollments` (protected), сертификаты через `/api/certificates` (protected).
- Кабинет преподавателя: управление своими курсами и добавление контента (материалы, лекции, семинары).
- Внешний API: YouTube oEmbed — на странице курса подтягиваются метаданные видео по `videoUrl` (если доступно).
- ДЗ2/ДЗ3/ДЗ4: доступность HTML, темизация через CSS‑переменные, SVG‑спрайт иконок.

