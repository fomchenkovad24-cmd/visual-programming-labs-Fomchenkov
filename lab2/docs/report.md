# Лаба 2

## Краткое описание выполненного

В ходе лабораторной работы я освоил Node-RED как инструмент визуального программирования. Собрал и задеплоил 12 потоков, покрывающих базовые и расширенные возможности:

1. Inject - Debug — простейший поток, отправка сообщения по таймеру.
2. Function — обработка сообщения на JavaScript.
3. Switch — ветвление потока по условию.
4. Change — изменение полей сообщения (topic, timestamp, payload).
5. Template — формирование текста или JSON через Mustache-шаблон.
6. HTTP Request — запрос к публичному API.
7. MQTT — публикация и подписка через публичный брокер.
8. GET-эндпоинты — три собственных HTTP-эндпоинта в Node-RED.
9. Dashboard — визуализация данных (стрелочный индикатор и график).
10. Telegram-бот — бот с командами /start, /help и эхо-ответом.
11. Файлы — запись и чтение файла, проверка сохранения между перезапусками.
12. Контекст — работа с контекстом вкладки, глобальным контекстом и переменной окружения.


## Способ установки

Изначально я пытался установить Node-RED через Docker Desktop, но он не смог запуститься из-за проблем с виртуализацией (WSL2). Поэтому я установил Node-RED через npm.


## Скрины версий
![Node-RED](../screenshots/Node-RED-version.png)
![Node.js](../screenshots/Node-js-version.png)


## AI-промпты

1. Сгенерируй код для function node в Node-RED: использует let, const, if/else, цикл for, массив и объект, возвращает объект в msg.payload.

2. Сделай Mustache-шаблон для template node, который формирует JSON из объекта с полями name, group, year.

3. Напиши код для function node — GET-эндпоинт с валидацией query-параметра count (от 1 до 10), возвращает 400 при ошибке.

4. Помоги выбрать публичный API без регистрации и токенов, который возвращает JSON. Нужен пример для потока inject - http request - debug.

5. «Напиши код для function node, который считает счётчик в контексте вкладки и в глобальном контексте, и читает переменную окружения.»

6. «Сделай простой Telegram-бот в Node-RED с командами /start, /help и эхо-ответом на произвольное сообщение.»

## Освоенные ноды

- inject
- debug
- function
- switch
- change
- template
- http request
- http in
- http response
- mqtt in
- mqtt out
- ui_gauge
- ui_chart
- telegram receiver
- telegram command
- telegram sender
- write file
- read file
- json

## Скрины потоков

### 2.1. Inject - Debug
![Inject - Debug](../screenshots/01-inject-debug.png)

### 2.2. Function
![Function](../screenshots/02-function.png)

### 2.3. Switch
![Switch](../screenshots/03-switch1.png)
![Switch](../screenshots/03-switch2.png)

### 2.4. Change
![Change](../screenshots/04-change.png)

### 2.5. Template
![Template](../screenshots/05-template.png)

### 2.6. HTTP Request
![HTTP Request](../screenshots/06-http-request1.png)
![HTTP Request](../screenshots/06-http-request2.png)

### 2.7. MQTT
![MQTT](../screenshots/07-mqtt.png)

### 2.8. GET-эндпоинты
![Endpoints success](../screenshots/08-endpoints1.png)
![Endpoints success](../screenshots/08-endpoints2.png)
![Endpoints success](../screenshots/08-endpoints3.png)
![Endpoints success](../screenshots/08-endpoints4.png)
![Endpoints success](../screenshots/08-endpoints5.png)

### 2.9. Dashboard
![Dashboard](../screenshots/09-dashboard.png)

### 2.10. Telegram-бот
![Telegram](../screenshots/10-telegram1.png)
![Telegram](../screenshots/10-telegram2.png)

### 2.11. Файлы
![Files write](../screenshots/11-files1.png)
![Files write](../screenshots/11-files2.png)
![Files write](../screenshots/11-files3.png)

### 2.12. Контекст
![Context](../screenshots/12-context1.png)
![Context](../screenshots/12-context2.png)

## Потоки
[flow-01](../flows/flow-01-inject-debug.json)
[flow-02](../flows/flow-02-function.json)
[flow-03](../flows/flow-03-switch.json)
[flow-04](../flows/flow-04-change.json)
[flow-05](../flows/flow-05-template.json)
[flow-06](../flows/flow-06-http-request.json)
[flow-07](../flows/flow-07-mqtt.json)
[flow-08](../flows/flow-08-endpoints.json)
[flow-09](../flows/flow-09-dashboard.json)
[flow-10](../flows/flow-10-telegram.json)
[flow-11](../flows/flow-11-files.json) 
[flow-12](../flows/flow-12-context.json)

## Вывод

Node-RED - это удобный инструмент для быстрого прототипирования. Потоки собираются из готовых блоков, и для большинства задач не нужно писать много кода. Основную логику можно реализовать через function node, если готовых нод не хватает.

Что понравилось:
- Быстрое подключение к MQTT, HTTP, Telegram - не нужно писать сетевой код вручную.
- Dashboard позволяет сразу видеть данные на графике.
- Файлы сохраняются между перезапусками — можно использовать для простого хранения.
- Контекст вкладки и глобальный контекст помогают хранить состояние между сообщениями.

Что оказалось сложным:
- Установка через Docker не заработала из-за проблем с виртуализацией. Пришлось ставить через npm.
- При работе с MQTT и Telegram нужно внимательно следить за настройками подключения - одна опечатка, и ничего не работает.
- Настройка группы и вкладки в Dashboard сначала показалась запутанной, но потом разобрался.
- При работе с графиком в Dashboard нужно правильно формировать формат данных (массив объектов с полями x и y).