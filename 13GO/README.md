# 13GO
# Arithmetic Expression Calculator

Этот проект представляет собой веб-сервис, который вычисляет арифметические выражения, отправленные пользователем через HTTP.

## Как пользоваться

Сервис имеет один endpoint:

### POST /api/v1/calculate

Тело запроса:

```json
{
    "expression": "выражение, которое ввёл пользователь"
}
```

Примеры использования:

1. Успешный запрос:

```bash
curl --location 'localhost:8080/api/v1/calculate' \
--header 'Content-Type: application/json' \
--data '{
  "expression": "2+2*2"
}'
```

Ответ:

```json
{
    "result": "6"
}
```

2. Ошибка 422 (неверное выражение):

```bash
curl --location 'localhost:8080/api/v1/calculate' \
--header 'Content-Type: application/json' \
--data '{
  "expression": "2+2*2a"
}'
```

Ответ:

```json
{
    "error": "Expression is not valid"
}
```

3. Ошибка 500 (внутренняя ошибка сервера):

```bash
curl --location 'localhost:8080/api/v1/calculate' \
--header 'Content-Type: application/json' \
--data '{
  "expression": "2/0"
}'
```

Ответ:

```json
{
    "error": "Internal server error"
}
```

### Запуск проекта

Чтобы запустить проект, выполните следующую команду:

```bash
go run ./cmd/calc_service/...
```


### Инструкция по запуску

1. Убедитесь, что у вас установлен Go.
2. Склонируйте репозиторий на свой локальный компьютер.
3. Перейдите в директорию проекта.
4. Запустите сервис командой `go run ./cmd/calc_service/...`.
5. Используйте `curl` для отправки запросов к вашему сервису.

