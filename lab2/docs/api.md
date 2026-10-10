# API Documentation - Lab 2 (Node-RED)

Базовый URL: http://localhost:1880

Все эндпоинты реализованы в Node-RED через ноды http in и http response.

## 1. GET /api/text

Возвращает простой текстовый ответ.

Параметры: нет.

Пример запроса:

curl http://localhost:1880/api/text

Успешный ответ:

Код: 200 OK
Content-Type: text/plain; charset=utf-8

Тело ответа:
Привет от Фомченкова! Это get /api/text.

Возможные ошибки: не предусмотрены, эндпоинт всегда возвращает 200.

## 2. GET /api/info

Возвращает JSON с информацией о студенте и лабораторной работе.

Параметры: нет.

Пример запроса:

curl http://localhost:1880/api/info

Успешный ответ:

Код: 200 OK
Content-Type: application/json; charset=utf-8

Тело ответа:
{
  "student": "Фомченков",
  "lab": "lab2",
  "timestamp": "2026-10-10T08:52:05.287Z"
}

Возможные ошибки: не предусмотрены, эндпоинт всегда возвращает 200.

## 3. GET /api/items

Возвращает массив элементов. Количество элементов задается query-параметром count.

Параметры:

count - integer, обязательный, от 1 до 10, количество элементов

Пример запроса (успех):

curl "http://localhost:1880/api/items?count=3"

Успешный ответ:

Код: 200 OK
Content-Type: application/json; charset=utf-8

Тело ответа:
{
  "count": 3,
  "items": ["item-1", "item-2", "item-3"]
}

Ошибка 1 - параметр отсутствует.

Запрос:
curl "http://localhost:1880/api/items"

Ответ:
Код: 400 Bad Request

Тело ответа:
{
  "error": "count is required"
}

Ошибка 2 - параметр вне диапазона.

Запрос:
curl "http://localhost:1880/api/items?count=999"

Ответ:
Код: 400 Bad Request

Тело ответа:
{
  "error": "count must be 1..10"
}

Ошибка 3 - параметр не число.

Запрос:
curl "http://localhost:1880/api/items?count=abc"

Ответ:
Код: 400 Bad Request

Тело ответа:
{
  "error": "count must be 1..10"
}

## Сводная таблица эндпоинтов

Сводная таблица эндпоинтов:

Метод: GET, URL: /api/text, Параметры: нет, Успех: 200, Ошибки: нет

Метод: GET, URL: /api/info, Параметры: нет, Успех: 200, Ошибки: нет

Метод: GET, URL: /api/items, Параметры: count (от 1 до 10), Успех: 200, Ошибки: 400

## Формат ошибок

Все ошибки возвращаются в формате JSON:

{
  "error": "описание ошибки"
}

Возможные коды ответов:

200 OK - успешный запрос
400 Bad Request - неверные параметры запроса