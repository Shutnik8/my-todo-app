
# 📝 Vue Todo App

Небольшое одностраничное приложение (SPA) для управления списком задач, созданное на Vue 3.

## 🚀 Функционал

- Загрузка задач из `tasks.json` при первом запуске
- Отметка задач как выполненных (состояние сохраняется в `localStorage`)
- Упаковано в Docker-контейнер для удобного запуска

---

## 📁 Структура проекта

- `public/tasks.json` — исходный список задач
- `src/App.vue` — основная логика отображения и работы с задачами
- `Dockerfile` — для сборки и запуска через Docker

---

## 🛠️ Установка и запуск

### 🔧 Локально

1. Клонируй репозиторий:

```bash
git clone https://github.com/твой_пользователь/vue-todo-app.git
cd vue-todo-app
```

2. Установи зависимости:

```bash
npm install
```

3. Запусти проект:

```bash
npm run dev
```

Открой в браузере: [http://localhost:5173](http://localhost:5173)

---

### 🐳 Через Docker

1. Собери образ:

```bash
docker build -t vue-todo .
```

2. Запусти контейнер:

```bash
docker run -p 8080:80 vue-todo
```

Приложение будет доступно по адресу: [http://localhost:8080](http://localhost:8080)

---

## 🧪 Пример `tasks.json`

```json
[
  { "id": 1, "title": "Задача 1", "done": false },
  { "id": 2, "title": "Задача 2", "done": false },
  { "id": 3, "title": "Задача 3", "done": false },
  { "id": 4, "title": "Задача 4", "done": false },
  { "id": 5, "title": "Задача 5", "done": false }
]
```

---

## 📦 Сохранение состояния

Состояние задач (выполнена/не выполнена) сохраняется в `localStorage` браузера. Это позволяет при перезагрузке страницы не терять прогресс.

---

## 🧾 Лицензия

MIT

---

## ✉️ Обратная связь
-
