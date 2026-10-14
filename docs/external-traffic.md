# Аналитика внешнего трафика

> Раздел справочника [Ozon Performance API](../README.md). Базовый URL: `https://api-performance.ozon.ru`. Аутентификация: заголовок `Authorization: Bearer <token>`.

Методы для работы с отчётами об аналитике внешнего трафика: запуск формирования отчётов, получение списка отчётов и статуса по UUID, а также метка организации для UTM-разметки внешних рекламных кампаний.

В этом разделе:

- [Отчёт с аналитикой внешнего трафика](#отчёт-с-аналитикой-внешнего-трафика) — `POST /api/client/vendors/statistics`
- [Список запрошенных отчётов с аналитикой внешнего трафика](#список-запрошенных-отчётов-с-аналитикой-внешнего-трафика) — `GET /api/client/vendors/statistics/list`
- [Информация об отчёте по UUID](#информация-об-отчёте-по-uuid) — `GET /api/client/vendors/statistics/{UUID}`
- [Метка организации для внешних рекламных кампаний](#метка-организации-для-внешних-рекламных-кампаний) — `GET /api/client/organisation/vendor_tag`

---

## Отчёт с аналитикой внешнего трафика

```http
POST /api/client/vendors/statistics
```

Метод для запуска формирования отчёта с аналитикой внешнего трафика.

Разница между `dateFrom` и `dateTo` должна быть не больше трёх месяцев. Если разница больше, отчёт сформируется за 3 месяца с даты, указанной в `dateFrom`.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `dateFrom` | string | Нет | Начало отчётного периода. Дата должна быть не ранее 1 января 2022 года |
| `dateTo` | string | Нет | Конец отчётного периода. Дата должна быть позднее `dateFrom` не больше чем на 3 месяца. Если дата позднее трёх месяцев, отчёт сформируется за 3 месяца с даты, указанной в `dateFrom` |
| `type` | string | Нет | Тип отчёта. Enum: `TRAFFIC_SOURCES` — отчёт по источникам трафика; `ORDERS` — отчёт по заказам |

### Ответ 200 — Успешно

| Поле | Тип | Описание |
|---|---|---|
| `UUID` | string | Уникальный идентификатор отправленного запроса. По нему можно проверить статус формирования отчёта и скачать отчёт |
| `vendor` | boolean | Если запрашивается отчёт с аналитикой внешнего трафика — `true` |

**Пример запроса:**

```http
POST /api/client/vendors/statistics HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "dateFrom": "string",
  "dateTo": "string",
  "type": "TRAFFIC_SOURCES"
}
```

**Пример ответа (200):**

```json
{
  "UUID": "string",
  "vendor": true
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Список запрошенных отчётов с аналитикой внешнего трафика

```http
GET /api/client/vendors/statistics/list
```

Возвращает список всех запрошенных отчётов с аналитикой внешнего трафика.

### Параметры запроса (query)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `page` | integer \<int64\> | Нет | Номер страницы |
| `pageSize` | integer \<int64\> | Нет | Размер страницы |

### Ответ 200 — Отчёты

| Поле | Тип | Описание |
|---|---|---|
| `items` | array of objects | Информация об отчётах |
| `items[].meta` | object | Метаданные отчёта |
| `items[].meta.UUID` | string | Уникальный идентификатор отчёта |
| `items[].meta.createdAt` | string \<date-time\> | Дата формирования отчёта |
| `items[].meta.updatedAt` | string \<date-time\> | Время изменения статуса |
| `items[].meta.state` | string | Статус формирования отчёта: `NOT_STARTED`, `IN_PROGRESS`, `OK`, `ERROR`, `TIMEOUT`, `CANCEL` |
| `items[].meta.error` | string | Описание ошибки |
| `items[].meta.link` | string | Ссылка на отчёт |
| `items[].meta.request` | object | Исходный запрос: `dateFrom`, `dateTo`, `type` |
| `items[].name` | string | Название отчёта |
| `total` | string \<uint64\> | Количество отчётов |

**Пример запроса:**

```http
GET /api/client/vendors/statistics/list?page=1&pageSize=10 HTTP/1.1
Host: api-performance.ozon.ru:443
Authorization: Bearer <token>
```

**Пример ответа (200):**

```json
{
  "items": [
    {
      "meta": {
        "UUID": "string",
        "createdAt": "2019-08-24T14:15:22Z",
        "error": "string",
        "link": "string",
        "request": {
          "dateFrom": "string",
          "dateTo": "string",
          "type": "TRAFFIC_SOURCES"
        },
        "state": "NOT_STARTED",
        "updatedAt": "2019-08-24T14:15:22Z"
      },
      "name": "string"
    }
  ],
  "total": "string"
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Информация об отчёте по UUID

```http
GET /api/client/vendors/statistics/{UUID}
```

Возвращает информацию о формировании отчёта с аналитикой внешнего трафика по его UUID.

### Параметры пути (path)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `UUID` | string | Да | Уникальный идентификатор запроса |

### Параметры запроса (query)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `vendor` | boolean | Да | Признак, что запрашивается отчёт с аналитикой внешнего трафика. Передавайте `true` в этом параметре |

### Ответ 200 — Информация об отчёте

| Поле | Тип | Описание |
|---|---|---|
| `UUID` | string | Уникальный идентификатор отправленного запроса, с помощью которого в дальнейшем можно проверить статус выполнения запроса и скачать отчёт |
| `createdAt` | string \<date-time\> | Дата формирования отчёта |
| `updatedAt` | string \<date-time\> | Время изменения статуса |
| `state` | string | Статус формирования отчёта. Default: `NOT_STARTED`. Enum: `NOT_STARTED` — ещё не началось; `IN_PROGRESS` — в процессе; `CANCEL` — отменено; `OK` — отчёт сформирован; `ERROR` — произошла ошибка; `TIMEOUT` — время ожидания истекло |
| `error` | string | Описание ошибки |
| `link` | string | Ссылка на отчёт |
| `request` | object | Метод, с помощью которого запросили формирование отчёта: `dateFrom`, `dateTo`, `type` |

**Пример запроса:**

```http
GET /api/client/vendors/statistics/0c159c60-ab92-46d9-9a6b-d225dbf5c7b1?vendor=true HTTP/1.1
Host: api-performance.ozon.ru:443
Authorization: Bearer <token>
```

**Пример ответа (200):**

```json
{
  "UUID": "string",
  "createdAt": "2019-08-24T14:15:22Z",
  "error": "string",
  "link": "string",
  "request": {
    "dateFrom": "string",
    "dateTo": "string",
    "type": "TRAFFIC_SOURCES"
  },
  "state": "NOT_STARTED",
  "updatedAt": "2019-08-24T14:15:22Z"
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Метка организации для внешних рекламных кампаний

```http
GET /api/client/organisation/vendor_tag
```

Метод возвращает префикс для метки `UTM_CAMPAIGN` по идентификатору организации.

Подробнее о ссылках для внешних рекламных кампаний — в документации Ozon.

### Параметры запроса (query)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `orgId` | string \<uint64\> | Да | Идентификатор организации |

### Ответ 200 — Метка организации

| Поле | Тип | Описание |
|---|---|---|
| `tag` | string | Префикс организации для UTM-метки |

**Пример запроса:**

```http
GET /api/client/organisation/vendor_tag?orgId=42 HTTP/1.1
Host: api-performance.ozon.ru:443
Authorization: Bearer <token>
Content-Type: application/json
Accept: application/json
```

**Пример ответа (200):**

```json
{
  "tag": "vendor_org_42"
}
```

**Ошибка:** `default` — ошибка запроса.
