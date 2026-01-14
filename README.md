# AI Calories Tracker

Приложение для подсчета калорий и отслеживания питания, созданное на основе инструмента из проекта AIgram.

## Технологии

### Backend
- FastAPI
- SQLModel (SQLite)
- Pydantic
- JWT аутентификация
- LangChain для AI чата

### Frontend
- React 18
- Vite
- TailwindCSS
- React Query
- React Router

## Быстрый запуск

### Windows

**Вариант 1: Автоматический запуск (рекомендуется)**
```bash
start.bat
```
Этот скрипт автоматически:
- Проверит и установит зависимости
- Создаст необходимые конфигурационные файлы
- Запустит backend и frontend в отдельных окнах

**Вариант 2: Ручной запуск**
```bash
# Терминал 1 - Backend
start-backend.bat

# Терминал 2 - Frontend
start-frontend.bat
```

### Linux/Mac

```bash
# Сделайте скрипт исполняемым
chmod +x start.sh stop.sh

# Запуск
./start.sh

# Остановка
./stop.sh
```

## Установка и запуск (детально)

### Backend

1. Перейдите в директорию backend:
```bash
cd backend
```

2. Создайте виртуальное окружение:
```bash
python -m venv venv
```

3. Активируйте виртуальное окружение:
- Windows:
```bash
venv\Scripts\activate
```
- Linux/Mac:
```bash
source venv/bin/activate
```

4. Установите зависимости:
```bash
pip install -r requirements.txt
```

5. Создайте файл `.env` в директории backend:
```env
# Для использования OpenRouter (рекомендуется)
OPENROUTER_API_KEY=your-openrouter-api-key

# Или для использования OpenAI напрямую
OPENAI_API_KEY=your-openai-api-key

# Секретный ключ для JWT
SECRET_KEY=your-secret-key-change-in-production
```

6. Запустите сервер:
```bash
uvicorn main:app --reload --port 8000
```

Backend будет доступен по адресу: http://localhost:8000

### Frontend

1. Перейдите в директорию frontend:
```bash
cd frontend
```

2. Установите зависимости:
```bash
npm install
```

3. Создайте файл `.env` в директории frontend:
```env
VITE_API_URL=http://localhost:8000
```

4. Запустите dev сервер:
```bash
npm run dev
```

Frontend будет доступен по адресу: http://localhost:5173

## Функциональность

- Регистрация и авторизация пользователей
- Настройка профиля (пол, возраст, рост, вес, цели)
- Автоматический расчет BMR, TDEE и целевых калорий
- Дневник питания с отслеживанием калорий и макронутриентов
- Отслеживание веса
- Отслеживание потребления воды
- Статистика за день
- Навигация по датам
- **Чат с AI диетологом** - персональный помощник, использующий ваши данные через RAG (Retrieval-Augmented Generation)

## API Endpoints

### Аутентификация
- `POST /auth/register` - Регистрация
- `POST /auth/login` - Вход

### Профиль
- `GET /dietitian/profile` - Получить профиль
- `PUT /dietitian/profile` - Обновить профиль

### Дневник питания
- `GET /dietitian/meal-logs` - Получить записи
- `POST /dietitian/meal-logs` - Создать запись
- `PUT /dietitian/meal-logs/{id}` - Обновить запись
- `DELETE /dietitian/meal-logs/{id}` - Удалить запись

### Вес
- `GET /dietitian/weight-logs` - Получить записи
- `POST /dietitian/weight-logs` - Создать запись
- `PUT /dietitian/weight-logs/{id}` - Обновить запись

### Вода
- `GET /dietitian/water-logs` - Получить записи
- `POST /dietitian/water-logs` - Создать запись
- `PUT /dietitian/water-logs/{id}` - Обновить запись

### Статистика
- `GET /dietitian/daily-stats` - Статистика за день

### Чат с AI
- `POST /chat/send` - Отправить сообщение в чат с AI диетологом

## Структура проекта

```
.
├── backend/
│   ├── api/          # API endpoints
│   ├── core/         # Основные утилиты (auth, database)
│   ├── models/       # Модели данных
│   ├── services/     # Бизнес-логика
│   ├── utils/        # Утилиты (расчеты калорий)
│   └── main.py       # Точка входа
├── frontend/
│   ├── src/
│   │   ├── api/      # API клиент
│   │   ├── components/ # React компоненты
│   │   ├── hooks/    # React хуки
│   │   ├── pages/    # Страницы
│   │   └── App.jsx   # Главный компонент
│   └── package.json
├── start.bat         # Быстрый запуск (Windows)
├── start.sh          # Быстрый запуск (Linux/Mac)
└── README.md
```

## Получение API ключей

### OpenRouter (рекомендуется)
1. Зарегистрируйтесь на https://openrouter.ai
2. Получите API ключ в настройках
3. Добавьте в `backend/.env`: `OPENROUTER_API_KEY=your-key`

### OpenAI
1. Зарегистрируйтесь на https://platform.openai.com
2. Создайте API ключ
3. Добавьте в `backend/.env`: `OPENAI_API_KEY=your-key`

## Лицензия

MIT
