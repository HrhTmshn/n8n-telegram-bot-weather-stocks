# Changelog

## [v0.1.1] — 2025-06-08

### 📝 Улучшения документации:
- обновлён README и добавлен скриншот схемы workflow (PNG)

---

## [v0.1.0] — 2025-06-08

### ✨ Основное:
- Реализован Telegram-бот на базе n8n с двумя основными функциями:
  - Погода по городу (с анализом температуры)
  - Цена акции по тикеру NASDAQ
- Добавлена логика цикличного диалога с пользователем
- Интеграция с Google Sheets для логирования:
  - user_id, chat_id, действия, результат
- Использование переменных окружения вместо жёстко заданных токенов
- Обработка ошибок и невалидных данных (например, несуществующий город или тикер)
- Универсальный механизм определения источника запроса (сообщение или нажатие кнопки)
- Инлайн-кнопки с переключением между режимами

---

## [v0.0.1] — 2025-06-06

### 🛠 Стартовая структура:
- Настроен Telegram Trigger и интеграция с WeatherAPI / Alpha Vantage
- Настроено ветвление по типу запроса
- Базовый вывод сообщений Telegram с клавиатурой
- Экспортирован шаблон workflow в `.json` с безопасной структурой