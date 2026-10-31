# Лаба 4

## Краткое описание выполненного
В ходе работы я освоил low-code платформу n8n. Запуск осуществлялся локально через `npx n8n`. Были изучены базовые ноды (Set, Code, IF, HTTP Request, Schedule), настроен Redis (через `redis-memory-server` из-за отсутствия Docker). Реализованы workflows для создания/чтения и удаления/проверки ключей Redis. Все workflow сохранены в виде JSON-файлов, сделаны скриншоты.

## Использованные AI-промпты
- Как установить n8n через Git Bash?
- Сгенерируй код на JavaScript для ноды Code
- Помоги установить redis через Git Bash

## Освоенные ноды
- **Manual Trigger**: запуск workflow по кнопке.
- **Set**: создание и изменение полей.
- **Code**: выполнение JavaScript.
- **IF**: ветвление логики.
- **HTTP Request**: GET-запросы к публичному API (catfact.ninja) и обработка JSON-ответа.
- **Schedule Trigger**: запуск по расписанию.
- **Redis** (Set, Get, Delete, Keys): работа с базой данных ключ-значение.

## Скриншоты
Все скриншоты находятся в папке `screenshots/`:
- [установка n8n](../screenshots/Установка-n8n.png)
- [n8n установлен](../screenshots/n8n-установлен.png)
- [версия n8n и запуск](../screenshots/Версия-n8n-и-запуск.png)
- [n8n запустился](../screenshots/n8n-запущен.png)
- [01-manual-set.png](../screenshots/01-manual-set.png)
- [02-code.png](../screenshots/02-code.png)
- [03-if.png](../screenshots/03-if.png)
- [04-set.png](../screenshots/04-set.png)
- [05-http.png](../screenshots/05-http.png)
- [06-schedule1.png](../screenshots/06-schedule1.png)
- [06-schedule1.png](../screenshots/06-schedule2.png)
- [09-redis-set.png](../screenshots/09-redis.png)
- [10-redis-delete.png](../screenshots/10-redis.png)


## Выводы
n8n — это мощный инструмент для визуального программирования, который позволяет быстро автоматизировать рутинные задачи без написания большого количества кода. Удобно, что можно комбинировать готовые ноды с кодом на JavaScript. Redis отлично подходит для быстрого обмена данными, а Schedule Trigger — для регулярных задач. Также я научился обходить ограничения (например, отсутствие Docker и ноды Exists в Redis), используя альтернативные инструменты и логику.