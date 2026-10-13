# Оплата за заказ

> Раздел справочника [Ozon Performance API](../README.md). Базовый URL: `https://api-performance.ozon.ru`. Аутентификация: заголовок `Authorization: Bearer <token>`.

Методы для работы с кампаниями «Оплата за заказ» (CPO / Search Promo): список товаров в продвижении, ставки, включение и отключение продвижения, акция «Морковск».

Статистика и отчёты по этим кампаниям описаны в разделе [Статистика](statistics.md).

В этом разделе:

- [Список товаров в продвижении в оплате за заказ](#список-товаров-в-продвижении-в-оплате-за-заказ) — `POST /api/client/campaign/search_promo/v2/products`
- [Рекомендованные ставки для товаров](#рекомендованные-ставки-для-товаров) — `POST /api/client/search_promo/bids/recommendation` (Deprecated)
- [Установить ставку на товар](#установить-ставку-на-товар) — `POST /api/client/campaign/search_promo/v2/bids/set` (Deprecated)
- [Получить фиксированные ставки для товаров](#получить-фиксированные-ставки-для-товаров) — `POST /api/client/search_promo/get_cpo_min_bids`
- [Включить продвижение товара в оплате за заказ](#включить-продвижение-товара-в-оплате-за-заказ) — `POST /api/client/search_promo/product/enable`
- [Отключить продвижение товара в оплате за заказ](#отключить-продвижение-товара-в-оплате-за-заказ) — `POST /api/client/search_promo/product/disable`
- [Удалить товар из продвижения в оплате за заказ](#удалить-товар-из-продвижения-в-оплате-за-заказ) — `POST /api/client/campaign/search_promo/v2/bids/delete`
- [Включить продвижение в оплате за заказ — все товары](#включить-продвижение-в-оплате-за-заказ--все-товары) — `GET /api/client/campaign/all_sku_promo/activate`
- [Выключить продвижение в оплате за заказ — все товары](#выключить-продвижение-в-оплате-за-заказ--все-товары) — `GET /api/client/campaign/all_sku_promo/deactivate`
- [Установить ставку для продвижения в Оплате за заказ — все товары](#установить-ставку-для-продвижения-в-оплате-за-заказ--все-товары) — `GET /api/client/campaign/all_sku_promo/set_bid`
- [Включить продвижение товаров в акции «Морковск»](#включить-продвижение-товаров-в-акции-морковск) — `POST /api/client/campaign/search_promo/carrots/enable`
- [Отключить продвижение товаров в акции «Морковск»](#отключить-продвижение-товаров-в-акции-морковск) — `POST /api/client/campaign/search_promo/carrots/disable`

---

## Список товаров в продвижении в оплате за заказ

```http
POST /api/client/campaign/search_promo/v2/products
```

Возвращает список товаров, добавленных в продвижение «Оплата за заказ», с их ставками и метриками видимости.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `page` | integer \<int64\> | Нет | Номер страницы. Пагинация начинается с единицы |
| `pageSize` | integer \<int64\> | Нет | Размер страницы |

### Ответ 200 — Список товаров

| Поле | Тип | Описание |
|---|---|---|
| `products` | array of objects | Список товаров |
| `products[].bid` | number | Текущая ставка |
| `products[].bidPrice` | string | Ставка в процентах от цены товара |
| `products[].bidWithoutAdditive` | number | Ставка без надбавки |
| `products[].carrotsAdditive` | number | Надбавка для акции «Морковск» |
| `products[].carrotsStatus` | string | Статус продвижения в акции «Морковск» (`CARROTS_STATUS_*`) |
| `products[].hint` | object | Подсказка: `campaignId` — идентификатор кампании, в которую входит товар; `organisationTitle` — название организации |
| `products[].imageUrl` | string | Ссылка на изображение товара |
| `products[].isSearchPromoAvailable` | boolean | Доступно ли для товара продвижение «Оплата за заказ» |
| `products[].previousBid` | object | Предыдущая ставка: `bid` — значение, `bidPrice` — в процентах, `updatedAt` — дата обновления |
| `products[].previousVisibilityIndex` | string | Предыдущий индекс видимости |
| `products[].price` | string | Цена товара |
| `products[].searchPromoStatus` | boolean | Включено ли продвижение «Оплата за заказ» |
| `products[].sku` | string | SKU товара |
| `products[].sourceSku` | string | Исходный SKU товара |
| `products[].title` | string | Название товара |
| `products[].views` | object | Просмотры: `previousWeek` — за предыдущую неделю; `thisWeek` — за текущую неделю |
| `products[].visibilityIndex` | string | Индекс видимости |
| `total` | string \<uint64\> | Количество товаров |

**Пример запроса:**

```http
POST /api/client/campaign/search_promo/v2/products HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "page": 0,
  "pageSize": 0
}
```

**Пример ответа (200):**

```json
{
  "products": [
    {
      "bid": 0,
      "bidPrice": "string",
      "bidWithoutAdditive": 0,
      "carrotsAdditive": 0,
      "carrotsStatus": "CARROTS_STATUS_NONE",
      "hint": {
        "campaignId": "string",
        "organisationTitle": "string"
      },
      "imageUrl": "string",
      "isSearchPromoAvailable": true,
      "previousBid": {
        "bid": 0,
        "bidPrice": "string",
        "updatedAt": "2019-08-24T14:15:22Z"
      },
      "previousVisibilityIndex": "string",
      "price": "string",
      "searchPromoStatus": true,
      "sku": "string",
      "sourceSku": "string",
      "title": "string",
      "views": {
        "previousWeek": "string",
        "thisWeek": "string"
      },
      "visibilityIndex": "string"
    }
  ],
  "total": "string"
}
```

**Ошибка:** `default` — ошибка.

---

## Рекомендованные ставки для товаров

```http
POST /api/client/search_promo/bids/recommendation
```

> **Deprecated.** Метод помечен устаревшим.

Возвращает рекомендованные ставки для товаров в «Оплате за заказ». За один запрос вы можете передать до **200 SKU**.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `skus` | array of string \<uint64\> | Нет | Список идентификаторов товаров |

### Ответ 200 — Рекомендованные ставки

| Поле | Тип | Описание |
|---|---|---|
| `recommendedBids` | object | Список рекомендованных ставок |
| `recommendedBids.<SKU>` | string | SKU товара и рекомендованная ставка за 1 заказ (CPO) в процентах от цены товара |

**Пример запроса:**

```http
POST /api/client/search_promo/bids/recommendation HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "skus": [
    "string"
  ]
}
```

**Пример ответа (200):**

```json
{
  "recommendedBids": {
    "sku1": "string",
    "sku2": "string"
  }
}
```

**Ошибка:** `default` — ошибка.

---

## Установить ставку на товар

```http
POST /api/client/campaign/search_promo/v2/bids/set
```

> **Deprecated.** Метод помечен устаревшим.

Устанавливает ставку на товары в «Оплате за заказ». Если товар ещё не добавлен в продвижение, система добавит его автоматически.

В одном запросе можно передать максимум **1000 товаров**.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `bids` | array of objects | Нет | Значения ставок |
| `bids[].bid` | number | Нет | Значение ставки |
| `bids[].sku` | string | Нет | SKU продвигаемого товара |

### Ответ 200 — Ставка установлена

| Поле | Тип | Описание |
|---|---|---|
| `response` | array of objects | Ответ метода |
| `response[].bid` | number | Значения ставок |
| `response[].error` | string | Ошибка, из-за которой нельзя обновить ставку |
| `response[].sku` | string \<uint64\> | SKU продвигаемого товара |
| `response[].update` | boolean | `true`, если ставка обновилась |

**Пример запроса:**

```http
POST /api/client/campaign/search_promo/v2/bids/set HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "bids": [
    {
      "bid": 0,
      "sku": "string"
    }
  ]
}
```

**Пример ответа (200):**

```json
{
  "response": [
    {
      "bid": 0,
      "error": "string",
      "sku": "string",
      "update": true
    }
  ]
}
```

**Ошибка:** `default` — ошибка.

---

## Получить фиксированные ставки для товаров

```http
POST /api/client/search_promo/get_cpo_min_bids
```

Возвращает фиксированные (минимальные) ставки для товаров в «Оплате за заказ». За один запрос вы можете передать до **200 SKU**.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `skus` | array of string \<uint64\> | Нет | Список идентификаторов товаров |

### Ответ 200 — Фиксированные ставки получены

| Поле | Тип | Описание |
|---|---|---|
| `bids` | array of objects | Информация о ставках |
| `bids[].bid` | number \<double\> | Значение ставки |
| `bids[].sku` | string \<uint64\> | SKU продвигаемого товара |

**Пример запроса:**

```http
POST /api/client/search_promo/get_cpo_min_bids HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "skus": [
    "string"
  ]
}
```

**Пример ответа (200):**

```json
{
  "bids": [
    {
      "bid": 0,
      "sku": "string"
    }
  ]
}
```

**Ошибка:** `default` — ошибка.

---

## Включить продвижение товара в оплате за заказ

```http
POST /api/client/search_promo/product/enable
```

Включает продвижение «Оплата за заказ» для товаров.

В одном запросе можно передать максимум **1000 товаров**.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `skus` | array of string \<uint64\> | Нет | Список идентификаторов товаров |

### Ответ 200 — Продвижение товара включено

| Поле | Тип | Описание |
|---|---|---|
| `response` | array of objects | Ответ метода |
| `response[].bid` | number | Значения ставок |
| `response[].error` | string | Ошибка, из-за которой нельзя включить продвижение товара |
| `response[].sku` | string \<uint64\> | SKU продвигаемого товара |
| `response[].update` | boolean | `true`, если продвижение товара включилось |

**Пример запроса:**

```http
POST /api/client/search_promo/product/enable HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "skus": [
    "string"
  ]
}
```

**Пример ответа (200):**

```json
{
  "response": [
    {
      "bid": 0,
      "error": "string",
      "sku": "string",
      "update": true
    }
  ]
}
```

**Ошибка:** `default` — ошибка.

---

## Отключить продвижение товара в оплате за заказ

```http
POST /api/client/search_promo/product/disable
```

Отключает продвижение «Оплата за заказ» для товаров.

В одном запросе можно передать максимум **1000 товаров**.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `skus` | array of string \<uint64\> | Нет | Список идентификаторов товаров |

### Ответ 200 — Продвижение товара отключено

Пустой объект:

```json
{ }
```

**Пример запроса:**

```http
POST /api/client/search_promo/product/disable HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "skus": [
    "string"
  ]
}
```

**Ошибка:** `default` — ошибка.

---

## Удалить товар из продвижения в оплате за заказ

```http
POST /api/client/campaign/search_promo/v2/bids/delete
```

Удаляет товары из продвижения «Оплата за заказ».

В одном запросе можно передать максимум **1000 товаров**.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `sku` | array of string \<uint64\> | Нет | Список идентификаторов товаров |

### Ответ 200 — Товар удалён

Пустой объект:

```json
{ }
```

**Пример запроса:**

```http
POST /api/client/campaign/search_promo/v2/bids/delete HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "sku": [
    "string"
  ]
}
```

**Ошибка:** `default` — ошибка.

---

## Включить продвижение в оплате за заказ — все товары

```http
GET /api/client/campaign/all_sku_promo/activate
```

Включает продвижение «Оплата за заказ» для всех товаров.

### Ответ 200 — Продвижение включено

| Поле | Тип | Описание |
|---|---|---|
| `selectedBid` | string \<uint64\> | Выбранная ставка для продвижения |

**Пример запроса:**

```http
GET /api/client/campaign/all_sku_promo/activate HTTP/1.1
Host: api-performance.ozon.ru:443
Authorization: Bearer <token>
```

**Пример ответа (200):**

```json
{
  "selectedBid": "string"
}
```

**Ошибка:** `default` — ошибка.

---

## Выключить продвижение в оплате за заказ — все товары

```http
GET /api/client/campaign/all_sku_promo/deactivate
```

Выключает продвижение «Оплата за заказ» для всех товаров.

### Ответ 200 — Продвижение выключено

Успешный ответ не содержит тела.

**Ошибка:** `default` — ошибка запроса:

```json
{
  "error": "text"
}
```

**Пример запроса:**

```http
GET /api/client/campaign/all_sku_promo/deactivate HTTP/1.1
Host: api-performance.ozon.ru:443
Authorization: Bearer <token>
```

---

## Установить ставку для продвижения в Оплате за заказ — все товары

```http
GET /api/client/campaign/all_sku_promo/set_bid
```

Устанавливает ставку продвижения «Оплата за заказ» для всех товаров.

### Параметры запроса (query)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `bid` | string \<uint64\> | Нет | Значение ставки в процентах. Default: 7. Возможные значения: `5`, `7`, `9` |

### Ответ 200 — Ставка установлена

Успешный ответ не содержит тела.

**Ошибка:** `default` — ошибка запроса:

```json
{
  "error": "text"
}
```

**Пример запроса:**

```http
GET /api/client/campaign/all_sku_promo/set_bid?bid=7 HTTP/1.1
Host: api-performance.ozon.ru:443
Authorization: Bearer <token>
```

---

## Включить продвижение товаров в акции «Морковск»

```http
POST /api/client/campaign/search_promo/carrots/enable
```

Добавляет товары в акцию «Морковск».

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `skus` | array of string \<uint64\> | Да | Список идентификаторов товаров |

### Ответ 200 — Продвижение включено

| Поле | Тип | Описание |
|---|---|---|
| `skuToInfo` | object | Информация о включении продвижения по SKU товара |
| `skuToInfo.<SKU>` | object | Информация об операции: `error` — код ошибки (`CARROT_ERROR_NONE` — без ошибок); `isDisabled` — признак отключения |

**Пример запроса:**

```http
POST /api/client/campaign/search_promo/carrots/enable HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "skus": [
    "string"
  ]
}
```

**Пример ответа (200):**

```json
{
  "skuToInfo": {
    "property1": {
      "error": "CARROT_ERROR_NONE",
      "isDisabled": false
    },
    "property2": {
      "error": "CARROT_ERROR_NONE",
      "isDisabled": true
    }
  }
}
```

**Ошибка:** `default` — ошибка.

---

## Отключить продвижение товаров в акции «Морковск»

```http
POST /api/client/campaign/search_promo/carrots/disable
```

Удаляет товары из акции «Морковск».

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `skus` | array of string \<uint64\> | Да | Список идентификаторов товаров |

### Ответ 200 — Продвижение отключено

| Поле | Тип | Описание |
|---|---|---|
| `skuToInfo` | object | Информация об отключении продвижения по SKU товара |
| `skuToInfo.<SKU>` | object | Информация об операции: `error` — код ошибки (`CARROT_ERROR_NONE` — без ошибок); `isDisabled` — признак отключения |

**Пример запроса:**

```http
POST /api/client/campaign/search_promo/carrots/disable HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "skus": [
    "string"
  ]
}
```

**Пример ответа (200):**

```json
{
  "skuToInfo": {
    "property1": {
      "error": "CARROT_ERROR_NONE",
      "isDisabled": true
    },
    "property2": {
      "error": "CARROT_ERROR_NONE",
      "isDisabled": false
    }
  }
}
```

**Ошибка:** `default` — ошибка.
