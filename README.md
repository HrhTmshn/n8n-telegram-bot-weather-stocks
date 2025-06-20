# n8n Telegram Bot: Weather & Stocks

Телеграм-бот, созданный с помощью [n8n](https://n8n.io) для получения информации о погоде и текущих ценах акций.  
Простой и интуитивный интерфейс: даже ваша бабушка сможет пользоваться.

---

### 🛠️ Технологии

- [n8n (cloud)](https://n8n.io) — визуальный low-code редактор
- [Telegram Bot API](https://core.telegram.org/bots/api)
- [WeatherAPI](https://www.weatherapi.com/) — данные о погоде
- [Alpha Vantage](https://www.alphavantage.co/) — котировки акций
- [Google Sheets API](https://developers.google.com/sheets/api) — логирование запросов

---

### 🚀 Возможности

- Командное меню с инлайн-кнопками
- Получение текущей температуры по городу с советом по одежде
- Получение текущей цены акций по тикеру NASDAQ
- Логирование действий пользователя в Google Таблицы
- Минималистичный и легко расширяемый workflow
---

### 🧭 Схема workflow

![Workflow Overview](workflow_overview.png)

---

### 📦 Установка и запуск

1. Зарегистрируйтесь в [n8n cloud](https://n8n.io/) или установите локально.

2. Импортируйте файл `TelegramBot_n8n_Workflow.json` в n8n.

3. Создайте в n8n переменные окружения в разделе **Settings → Variables**:

| Имя переменной           | Описание                                      |
|--------------------------|-----------------------------------------------|
| `WEATHER_API_KEY`        | Ключ API от [weatherapi.com](https://weatherapi.com) |
| `STOCKS_API_KEY`         | Ключ API от [alphavantage.co](https://alphavantage.co) |
| `TELEGRAM_BOT_TOKEN`     | Токен вашего Telegram-бота                    |
| `SPREADSHEET_ID`         | ID Google таблицы, куда писать лог            |
| `LOGLIST_SHEET_NAME`     | Название листа для логов                      |
| `USER_ACTION_SHEET_NAME` | Название листа с действиями                   |

4. Задайте нужные креды для Telegram и Google Sheets (ноды будут выделены как "Missing credentials").

5. Активируйте workflow и начните общение с ботом.

---

### 📋 Настройка Google Таблицы

Для корректной работы логирования необходимо:

1. Создать Google Таблицу и скопировать ёё `SPREADSHEET_ID` — это часть ссылки между `/d/` и `/edit`, например:
   `https://docs.google.com/spreadsheets/d/your_spreadsheet_id/edit`

2. Создать два листа (вкладки) внутри таблицы:

#### 📄 Лист 1: `LOGLIST_SHEET_NAME` (например, Log)

В первую строку добавьте следующую шапку (заголовки колонок):

```
Date,User,User ID,Chat ID,Action,Query,Weather,Stock Symbol,Price,Answer
```

→ Чтобы заголовки корректно встали **по столбцам**, сделайте так:

1. Выделите первую строку таблицы.
2. Вставьте скопированный текст в Google Sheets с помощью
   **Правка → Специальная вставка → Разделить текст на столбцы**,
   или нажмите `Ctrl + Shift + V`, затем выберите **разделитель: запятая**.

🧰 В результате должно получиться:

| Date | User | User ID | Chat ID | Action | Query | Weather | Stock Symbol | Price | Answer |
| ---- | ---- | ------- | ------- | ------ | ----- | ------- | ------------ | ----- | ------ |

---

#### 📄 Лист 2: `USER_ACTION_SHEET_NAME` (например, Users)

Шапка таблицы:

```
User ID,Last Action
```

После вставки также используйте “Разделить текст на столбцы”.

| User ID | Last Action |
| ------- | ----------- |

⚠️ Без этих заголовков Google Sheets API не сможет правильно записывать данные.

---

### 🖼 Пример использования

Пользователь запускает бота → нажимает кнопку "🌍 Погода" → вводит город → получает совет:  
```
Сегодня в Киев 23° C — отличный день, можно бегать в футболке.
```

Или:  
```
Текущая цена акций AAPL: $187.90
```

---

### ⚠️ Заметки

- Бот разработан в рамках тестового задания для позиции Python/n8n-разработчика.
- Все API-ключи вынесены в переменные окружения — безопасно для публикации.
- Workflow построен с учётом минимизации количества нод.

---

### 📄 Лицензия

Проект распространяется **только в образовательных целях**.  
Любое коммерческое использование, распространение или модификация — **запрещены**.

Подробнее — в [LICENSE](./LICENSE).