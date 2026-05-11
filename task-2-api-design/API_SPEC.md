# Запрос на получение данных о магазинах партнерах

| Атрибут | Значение |
|---|---|
| Назначение | Получить список магазинов партнеров |
| HTTP Method | GET |
| Endpoint | /api/v1/partners |
| URL пример | http://{домен}/api/v1/partners <br> api/v1/partners?search=metro <br> api/v1/partners?deliveryAvailable=true |

## Response Body

### 200 OK

```json
{
    "status": "success",
    "data": [
      {
       "id": 1,
       "name": "Metro",
       "externalUrl": "https://online.metro-cc.ru",
       "isActive": true
       },
       {
        "id": 2,
        "name": "Ашан",
        "externalUrl": "https://online.ashan-cc.ru",
        "isActive": true
        }
    ],
  "pagination": {
    "currentPage": 1,
    "totalPages": 2,
    "totalItems": 20,
    "itemsPerPage": 10
  }
}

```

## Ошибки

| HTTP Code | Код ошибки | Описание | Текст ошибки |
|---|---|---|---|
| 401 | AUTHORIZATION_REQUIRED | Требуется авторизация | `{"error": "Для дальнейших действий требуется авторизация"}`|
| 404 | PARTNER_NOT_FOUND | Конкретный магазин не найден | Возвращает на фронт при некорректно заданных query param `{"error": "Магазин {} не найден"`|
| 500 | INTERNAL_ERROR | Внутренняя ошибка сервера | Сервер недоступен `{"error": "Внутренняя ошибка сервера "}`|
