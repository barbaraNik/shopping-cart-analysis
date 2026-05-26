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
        "name": "METRO",
        "logoUrl": "https://cdn.petrushka.ru/partners/metro.png",
        "externalUrl": "https://online.metro-cc.ru",
        "deliveryInfo": {
          "type": "scheduled",
          "label": "Ближайшая доставка",
          "value": "сегодня 21:00–23:00"
        }
      },
       {
        "id": 2,
        "name": "Ашан",
        "logoUrl": "https://cdn.petrushka.ru/partners/auchan.png",
        "externalUrl": "https://online.ashan-cc.ru",
        "deliveryInfo": {
          "type": "scheduled",
          "label": "Ближайшая доставка",
          "value": "сегодня 18:00–20:00"
        }
       },
      {
        "id": 3,
        "name": "ВкусВилл",
        "logoUrl": "https://cdn.petrushka.ru/partners/vkusvill.png",
        "externalUrl": "https://vkusvill.ru",
        "deliveryInfo": {
          "type": "express",
          "label": "Быстрая доставка",
          "value": "от 20 до 60 минут"
        }
      },
      {
        "id": 4,
        "name": "ВИКТОРИЯ",
        "logoUrl": "https://cdn.petrushka.ru/partners/victoria.png",
        "externalUrl": "https://victoria-group.ru",
        "deliveryInfo": {
          "type": "scheduled",
          "label": "Ближайшая доставка",
          "value": "сегодня 17:00–19:00"
        }
      }
    ],
  "pagination": {
    "currentPage": 1,
    "totalPages": 1,
    "totalItems": 4,
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
