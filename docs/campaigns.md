# Кампании и рекламируемые объекты

> Раздел справочника [Ozon Performance API](../README.md). Базовый URL: `https://api-performance.ozon.ru`. Аутентификация: заголовок `Authorization: Bearer <token>`.

Методы для получения списка кампаний, продвигаемых объектов, лимитов ставок, а также активации, деактивации и изменения параметров кампаний.

В этом разделе:

- [Список кампаний](#список-кампаний) — `GET /api/client/campaign`
- [Список продвигаемых объектов в кампании](#список-продвигаемых-объектов-в-кампании) — `GET /api/client/campaign/{campaignId}/objects`
- [Лимиты ставок для инструментов продвижения](#лимиты-ставок-для-инструментов-продвижения) — `GET /api/client/limits/list`
- [Минимальная ставка для товаров по SKU](#минимальная-ставка-для-товаров-по-sku) — `POST /api/client/min/sku`
- [Список товаров с бонусами](#список-товаров-с-бонусами) — `GET /api/client/products_with_bonuses`
- [Активировать кампанию](#активировать-кампанию) — `POST /api/client/campaign/{campaignId}/activate`
- [Выключить кампанию](#выключить-кампанию) — `POST /api/client/campaign/{campaignId}/deactivate`
- [Изменить параметры кампании](#параметры-кампании) — `PATCH /api/client/campaign/{campaignId}`
- [Рассчитать минимальный бюджет кампании](#рассчитать-минимальный-бюджет-кампании) — `POST /external/api/dynamic_budget` (Deprecated)

Значения перечислений (enum) — в разделе [Общие соглашения](../README.md#общие-соглашения-и-форматы).

---

## Список кампаний

```http
GET /api/client/campaign
```

Возвращает список рекламных кампаний с их параметрами: тип оплаты, состояние, даты, бюджеты, размещение и стратегия.

### Параметры запроса (query)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `campaignIds` | array of string \<uint64\> | Нет | Список идентификаторов кампаний, для которых необходимо вывести информацию. Если передать значение, то в ответе будет информация по кампаниям, которые указаны в поле `campaigns`. Если поле пустое, информация будет отдана по всем кампаниям |
| `advObjectType` | string | Нет | Тип рекламируемой кампании: `SKU` — Оплата за клик; `BANNER` — Баннерная рекламная кампания; `SEARCH_PROMO` — Оплата за заказ; `VIDEO_BANNER` — Видеобаннер |
| `state` | string | Нет | Состояние кампании. Default: `CAMPAIGN_STATE_UNKNOWN`. Enum: `CAMPAIGN_STATE_UNKNOWN`, `CAMPAIGN_STATE_RUNNING`, `CAMPAIGN_STATE_PLANNED`, `CAMPAIGN_STATE_STOPPED`, `CAMPAIGN_STATE_INACTIVE`, `CAMPAIGN_STATE_ARCHIVED`, `CAMPAIGN_STATE_MODERATION_DRAFT`, `CAMPAIGN_STATE_MODERATION_IN_PROGRESS`, `CAMPAIGN_STATE_MODERATION_FAILED`, `CAMPAIGN_STATE_FINISHED` |
| `page` | integer \<int64\> | Нет | Номер страницы. Пагинация начинается с единицы |
| `pageSize` | integer \<int64\> | Нет | Размер страницы |

### Ответ 200 — Список всех кампаний

| Поле | Тип | Описание |
|---|---|---|
| `list` | array of objects | Список кампаний |
| `list[].id` | string \<uint64\> | Идентификатор кампании |
| `list[].paymentType` | string | Тип оплаты. Default: `CAMPAIGN_TYPE_INVALID`. Enum: `CPC` — за клики; `CPM` — за показы; `CPO` — за заказы |
| `list[].title` | string | Название кампании |
| `list[].state` | string | Состояние кампании. Default: `CAMPAIGN_STATE_UNKNOWN`. Возможные значения: `CAMPAIGN_STATE_RUNNING` — активная кампания; `CAMPAIGN_STATE_PLANNED` — кампания, сроки проведения которой ещё не наступили; `CAMPAIGN_STATE_STOPPED` — кампания, приостановленная из-за нехватки бюджета; `CAMPAIGN_STATE_INACTIVE` — кампания, остановленная владельцем; `CAMPAIGN_STATE_ARCHIVED` — архивная кампания; `CAMPAIGN_STATE_MODERATION_DRAFT` — отредактированная кампания до отправки на модерацию; `CAMPAIGN_STATE_MODERATION_IN_PROGRESS` — кампания, отправленная на модерацию; `CAMPAIGN_STATE_MODERATION_FAILED` — кампания, непрошедшая модерацию; `CAMPAIGN_STATE_FINISHED` — кампания завершена, дата окончания в прошлом, такую кампанию нельзя изменить, можно только клонировать или создать новую |
| `list[].advObjectType` | string | Тип рекламируемой кампании: `SKU` — Оплата за клик; `BANNER` — Баннерная рекламная кампания; `SEARCH_PROMO` — Оплата за заказ; `VIDEO_BANNER` — Видеобаннер |
| `list[].fromDate` | string | Дата старта рекламной кампании |
| `list[].toDate` | string | Дата завершения рекламной кампании |
| `list[].autostopStatus` | string | Статус кампании. Default: `AUTOSTOP_STATUS_NONE`. Enum: `AUTOSTOP_STATUS_NONE` — продавец создал кампанию вручную; `AUTOSTOP_STATUS_ENABLED` — кампания создана автоматически и остановится, когда кончатся баллы; `AUTOSTOP_STATUS_DISABLED` — кампания создана автоматически, но она не остановится, когда кончатся баллы; `AUTOSTOP_STATUS_STOPPED` — баллы закончились, кампания остановлена автоматически |
| `list[].isAutocreated` | boolean | `true`, если кампания создана автоматически |
| `list[].budget` | string \<uint64\> | Бюджет рекламной кампании. Единица измерения — одна миллионная доля рубля, округляется до копеек. Например, значение 1 000 000 в параметре равно 1 рублю |
| `list[].dailyBudget` | string \<uint64\> | Дневной бюджет рекламной кампании. Единица измерения — одна миллионная доля рубля, округляется до копеек |
| `list[].weeklyBudget` | string \<uint64\> | Недельный бюджет рекламной кампании. Единица измерения — одна миллионная доля рубля, округляется до копеек |
| `list[].placement` | string | Место размещения продвигаемых товаров. Default: `PLACEMENT_INVALID`. Enum: `PLACEMENT_INVALID` — не определено; `PLACEMENT_PDP` — карточка товара, доступно только для кампаний с ручным управлением; `PLACEMENT_SEARCH_AND_CATEGORY` — поиск и рекомендации; `PLACEMENT_TOP_PROMOTION` — поиск; `PLACEMENT_OVERTOP` — поиск и главная (Спецразмещение); `PLACEMENT_TAKEOVER` — одновременный показ товаров на первых 4 плитках; `PLACEMENT_TILE_MAIN` — главная, нативный баннер |
| `list[].productAutopilotStrategy` | string | Стратегия, которая используется для кампании. Default: `NO_AUTO_STRATEGY`. Enum: `MAX_VIEWS` — максимальное количество показов; `MAX_CLICKS` — автостратегия для Поиска и рекомендаций; `TOP_MAX_CLICKS` — автостратегия для Поиска; `TAKEOVER` — спецразмещение для Поиска; `TOP_PROMOTION` — вывод в топ; `TARGET_BIDS` — средняя стоимость клика для Поиска и рекомендаций; `TARGET_CIR` — целевой расход; `NO_AUTO_STRATEGY` — автостратегия не используется |
| `list[].autopilot` | object | Информация о кампании. Возвращается, если в параметре `productAutopilotStrategy` включена стратегия |
| `list[].createdAt` | string \<date-time\> | Дата создания кампании в формате RFC3339 |
| `list[].updatedAt` | string \<date-time\> | Дата обновления кампании в формате RFC3339 |
| `list[].productCampaignMode` | string | Режим создания и управления товарной рекламной кампанией. Default: `PRODUCT_CAMPAIGN_MODE_AUTO`. Enum: `PRODUCT_CAMPAIGN_MODE_AUTO` — автоматически; `PRODUCT_CAMPAIGN_MODE_MANUAL` — вручную |

**Пример запроса:**

```http
GET /api/client/campaign?campaignIds=52374&advObjectType=SKU&state=CAMPAIGN_STATE_UNKNOWN HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

**Пример ответа (200):**

```json
{
  "list": {
    "id": 48949,
    "paymentType": "CPM",
    "title": "Баннерная кампания",
    "state": "CAMPAIGN_STATE_RUNNING",
    "advObjectType": "BANNER",
    "fromDate": "2019-10-07",
    "toDate": "2021-10-07",
    "dailyBudget": 504000000,
    "placement": [
      "PLACEMENT_PDP"
    ],
    "budget": 50000000,
    "createdAt": "2019-10-07T06:28:44.055042Z",
    "updatedAt": "2020-10-01T06:28:44.055042Z",
    "productAutopilotStrategy": "NO_AUTO_STRATEGY",
    "productCampaignMode": "PRODUCT_CAMPAIGN_MODE_AUTO"
  }
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Список продвигаемых объектов в кампании

```http
GET /api/client/campaign/{campaignId}/objects
```

Метод для получения списка продвигаемых объектов в кампаниях «Оплата за клик», «Баннеры» и «Видеобаннеры».

Чтобы получить товары в кампании «Оплата за заказ», используйте `POST /api/client/campaign/search_promo/v2/products` ([Оплата за заказ](order-payment.md#список-товаров-в-продвижении-в-оплате-за-заказ)).

### Параметры пути (path)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `campaignId` | string \<uint64\> | Да | Идентификатор кампании |

### Ответ 200 — Список рекламируемых объектов в кампании

| Поле | Тип | Описание |
|---|---|---|
| `list` | array of objects | Список идентификаторов рекламируемых объектов |
| `list[].id` | string \<uint64\> | Идентификатор рекламируемого объекта: `SKU` — для рекламы товаров в спонсорских полках и в каталоге; числовой идентификатор — для баннерных кампаний |

**Пример запроса:**

```http
GET /api/client/campaign/48852/objects HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

**Пример ответа (200):**

```json
{
  "list": [
    {
      "id": "string"
    }
  ]
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Лимиты ставок для инструментов продвижения

```http
GET /api/client/limits/list
```

Вы можете получить лимиты ставок по инструментам:

- **Оплата за заказ:**
  - Минимальная и максимальная ставка для инструмента.
  - Минимальные ставки за заказ для некоторых категорий товаров.
- **Спецразмещение и Оплата за клик:**
  - Минимальная и максимальная ставка за клик.
  - Минимальные ставки за клик для некоторых категорий товаров.

### Ответ 200 — Лимиты ставок

| Поле | Тип | Описание |
|---|---|---|
| `limits` | array of objects | Минимальные и максимальные ставки для инструментов продвижения |
| `limits[].categories` | array of objects | Минимальная ставка для категории второго уровня. Если категории нет в списке, применяется минимальная ставка для инструмента |
| `limits[].categories[].bid` | number | Размер ставки |
| `limits[].categories[].category` | string | Идентификатор или название категории |
| `limits[].maxBid` | number \<double\> | Максимальная ставка в рублях |
| `limits[].minBid` | number \<double\> | Минимальная ставка в рублях |
| `limits[].objectType` | string | Тип инструмента. Enum: `SKU` — Оплата за клик; `SEARCH_PROMO` — Оплата за заказ |
| `limits[].paymentMethod` | string | Способ оплаты. Enum: `CPO` — оплата за заказ; `CPC` — оплата за клик; `CPM` — оплата за 1000 показов |
| `limits[].placement` | string | Тип кампании. Enum: `CAMPAIGN_PLACEMENT_SEARCH_AND_CATEGORY` — Поиск и рекомендации; `CAMPAIGN_PLACEMENT_TOP_PROMOTION` — Поиск; `CAMPAIGN_PLACEMENT_OVERTOP` — Спецразмещение |

**Пример запроса:**

```http
GET /api/client/limits/list HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

**Пример ответа (200):**

```json
{
  "limits": [
    {
      "categories": [
        {
          "bid": 0,
          "category": "string"
        }
      ],
      "maxBid": 0,
      "minBid": 0,
      "objectType": "SKU",
      "paymentMethod": "CPO",
      "placement": "CAMPAIGN_PLACEMENT_SEARCH_AND_CATEGORY"
    }
  ]
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Минимальная ставка для товаров по SKU

```http
POST /api/client/min/sku
```

Используйте метод, чтобы узнать минимальную ставку для одного или нескольких товаров по SKU.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `marketplaceId` | string | Нет | Страна витрины. Enum: `MARKETPLACE_ID_RU` — Россия; `MARKETPLACE_ID_KZ` — Казахстан; `MARKETPLACE_ID_BY` — Белоруссия |
| `paymentType` | string | Нет | Тип минимальной ставки. Enum: `CPO` — по кампании «Оплата за заказ»; `CPC` — по поиску и рекомендациям; `CPC_TOP` — по поиску |
| `sku` | array of string \<uint64\> | Нет | Идентификатор товара: Ozon ID или SKU |

### Ответ 200 — Размер минимальной ставки

| Поле | Тип | Описание |
|---|---|---|---|
| `minBids` | array of objects | Информация о минимальных ставках |
| `minBids[].bid` | number \<double\> | Размер ставки |
| `minBids[].sku` | string \<uint64\> | Идентификатор товара: Ozon ID или SKU |

**Пример запроса:**

```http
POST /api/client/min/sku HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "marketplaceId": "MARKETPLACE_ID_RU",
  "paymentType": "CPO",
  "sku": [
    "string"
  ]
}
```

**Пример ответа (200):**

```json
{
  "minBids": [
    {
      "bid": 0,
      "sku": "string"
    }
  ]
}
```

**Ошибка:** `default` — ошибка.

---

## Список товаров с бонусами

```http
GET /api/client/products_with_bonuses
```

Возвращает список SKU товаров, на которые начислены бонусы. За клик на товар в первую очередь тратятся начисленные на него бонусы. Если бонусы кончились, тратится общий бюджет кампании.

### Ответ 200 — Список товаров с бонусами

| Поле | Тип | Описание |
|---|---|---|
| `skus` | array of string \<uint64\> | Список SKU товаров |

**Пример запроса:**

```http
GET /api/client/products_with_bonuses HTTP/1.1
Host: api-performance.ozon.ru:443
Authorization: Bearer <token>
```

**Пример ответа (200):**

```json
{
  "skus": [
    "string"
  ]
}
```

**Ошибка:** `default` — ошибка.

---

## Активировать кампанию

```http
POST /api/client/campaign/{campaignId}/activate
```

Включает рекламную кампанию.

### Параметры пути (path)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `campaignId` | string \<uint64\> | Да | Идентификатор кампании |

### Тело запроса

Пустой объект JSON: `{}`.

### Ответ 200 — Кампания активирована

| Поле | Тип | Описание |
|---|---|---|
| `id` | string \<uint64\> | Идентификатор кампании |
| `autostopStatus` | string | Статус кампании. Default: `AUTOSTOP_STATUS_NONE`. Enum: `AUTOSTOP_STATUS_NONE` — продавец создал кампанию вручную; `AUTOSTOP_STATUS_ENABLED` — кампания создана автоматически и остановится, когда кончатся баллы; `AUTOSTOP_STATUS_DISABLED` — кампания создана автоматически, но она не остановится, когда кончатся баллы; `AUTOSTOP_STATUS_STOPPED` — баллы закончились, кампания остановлена автоматически |
| `isAutocreated` | boolean | `true`, если кампания создана автоматически |
| `paymentType` | string | Тип оплаты. Default: `CAMPAIGN_TYPE_INVALID`. Enum: `CPC` — за клики; `CPM` — за показы; `CPO` — за заказы |
| `title` | string | Название кампании |
| `state` | string | Состояние кампании. Default: `CAMPAIGN_STATE_UNKNOWN`. Возможные значения аналогичны полю `state` метода [Список кампаний](#список-кампаний) |
| `fromDate` | string | Дата старта рекламной кампании |
| `toDate` | string | Дата завершения рекламной кампании |
| `budget` | string \<uint64\> | Бюджет рекламной кампании. Единица измерения — одна миллионная доля рубля, округляется до копеек |
| `dailyBudget` | string \<uint64\> | **Deprecated.** Дневной бюджет рекламной кампании. Единица измерения — одна миллионная доля рубля |
| `weeklyBudget` | string \<uint64\> | Недельный бюджет рекламной кампании. Единица измерения — одна миллионная доля рубля |
| `placement` | string | Место размещения продвигаемых товаров. Default: `PLACEMENT_INVALID`. Enum: `PLACEMENT_INVALID`; `PLACEMENT_PDP` — карточка товара, доступно только для кампаний с ручным управлением; `PLACEMENT_SEARCH_AND_CATEGORY` — поиск и рекомендации; `PLACEMENT_TOP_PROMOTION` — поиск; `PLACEMENT_OVERTOP` — поиск и главная |
| `productAutopilotStrategy` | string | Стратегия, которая используется для кампании. Enum: `MAX_CLICKS` — автостратегия для Поиска и рекомендаций; `TOP_MAX_CLICKS` — автостратегия для Поиска; `TARGET_BIDS` — средняя стоимость клика для Поиска и рекомендаций; `TOP_PROMOTION` — вывод в топ; `TARGET_CIR` — целевой расход |
| `autopilot` | object | Информация о кампании. Возвращается, если в параметре `productAutopilotStrategy` включена стратегия |
| `createdAt` | string \<date-time\> | Дата создания кампании в формате RFC3339 |
| `updatedAt` | string \<date-time\> | Дата обновления кампании в формате RFC3339 |
| `productCampaignMode` | string | Режим создания и управления товарной рекламной кампанией. Default: `PRODUCT_CAMPAIGN_MODE_AUTO`. Enum: `PRODUCT_CAMPAIGN_MODE_AUTO` — автоматически; `PRODUCT_CAMPAIGN_MODE_MANUAL` — вручную |

**Пример запроса:**

```http
POST /api/client/campaign/48852/activate HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{ }
```

**Пример ответа (200):**

```json
{
  "id": "string",
  "autostopStatus": "AUTOSTOP_STATUS_NONE",
  "isAutocreated": true,
  "paymentType": "CAMPAIGN_TYPE_INVALID",
  "title": "string",
  "state": "CAMPAIGN_STATE_UNKNOWN",
  "fromDate": "string",
  "toDate": "string",
  "budget": "string",
  "dailyBudget": "string",
  "weeklyBudget": "string",
  "placement": "PLACEMENT_INVALID",
  "productAutopilotStrategy": "MAX_CLICKS",
  "autopilot": {
    "categoryId": "string",
    "skuAddMode": "PRODUCT_CAMPAIGN_SKU_ADD_MODE_UNKNOWN"
  },
  "createdAt": "2019-08-24T14:15:22Z",
  "updatedAt": "2019-08-24T14:15:22Z",
  "productCampaignMode": "PRODUCT_CAMPAIGN_MODE_AUTO"
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Выключить кампанию

```http
POST /api/client/campaign/{campaignId}/deactivate
```

Выключает рекламную кампанию.

### Параметры пути (path)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `campaignId` | string \<uint64\> | Да | Идентификатор кампании |

### Тело запроса

Пустой объект JSON: `{}`.

### Ответ 200 — Кампания деактивирована

Схема ответа идентична ответу метода [Активировать кампанию](#активировать-кампанию): кампания с обновлёнными параметрами.

| Поле | Тип | Описание |
|---|---|---|
| `id` | string \<uint64\> | Идентификатор кампании |
| `autostopStatus` | string | Статус кампании (см. enum в методе [Активировать кампанию](#активировать-кампанию)) |
| `isAutocreated` | boolean | `true`, если кампания создана автоматически |
| `paymentType` | string | Тип оплаты: `CPC`, `CPM`, `CPO` |
| `title` | string | Название кампании |
| `state` | string | Состояние кампании |
| `fromDate` / `toDate` | string | Даты старта и завершения кампании |
| `budget` / `dailyBudget` / `weeklyBudget` | string \<uint64\> | Бюджеты кампании в миллионных долях рубля |
| `placement` | string | Место размещения продвигаемых товаров |
| `productAutopilotStrategy` | string | Стратегия кампании |
| `autopilot` | object | Информация об автостратегии |
| `createdAt` / `updatedAt` | string \<date-time\> | Даты создания и обновления в формате RFC3339 |
| `productCampaignMode` | string | Режим управления кампанией: `PRODUCT_CAMPAIGN_MODE_AUTO` / `PRODUCT_CAMPAIGN_MODE_MANUAL` |

**Пример запроса:**

```http
POST /api/client/campaign/48852/deactivate HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{ }
```

**Пример ответа (200):**

```json
{
  "id": "string",
  "autostopStatus": "AUTOSTOP_STATUS_NONE",
  "isAutocreated": true,
  "paymentType": "CAMPAIGN_TYPE_INVALID",
  "title": "string",
  "state": "CAMPAIGN_STATE_UNKNOWN",
  "fromDate": "string",
  "toDate": "string",
  "budget": "string",
  "dailyBudget": "string",
  "weeklyBudget": "string",
  "placement": "PLACEMENT_INVALID",
  "productAutopilotStrategy": "MAX_CLICKS",
  "autopilot": {
    "categoryId": "string",
    "skuAddMode": "PRODUCT_CAMPAIGN_SKU_ADD_MODE_UNKNOWN"
  },
  "createdAt": "2019-08-24T14:15:22Z",
  "updatedAt": "2019-08-24T14:15:22Z",
  "productCampaignMode": "PRODUCT_CAMPAIGN_MODE_AUTO"
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Параметры кампании

```http
PATCH /api/client/campaign/{campaignId}
```

Метод для изменения параметров кампании.

### Параметры пути (path)

| Параметр | Тип | Обязательный | Описание |
|---|---|---|---|
| `campaignId` | string \<uint64\> | Да | Идентификатор кампании |

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `autopilot` | object | Условно | Информация о кампании. Обязательный параметр, если в параметре `productAutopilotStrategy` включена автостратегия |
| `autopilot.categoryId` | string | Нет | Идентификатор категории для автостратегии |
| `autopilot.skuAddMode` | string | Нет | Режим добавления товаров в кампанию |
| `fromDate` | string | Нет | Дата начала рекламной кампании по московскому времени. Не может быть раньше текущей даты |
| `toDate` | string | Нет | Дата окончания рекламной кампании по московскому времени. Не может быть раньше даты начала |
| `budget` | string \<uint64\> | Нет | Ограничение общего бюджета рекламной кампании. Единица измерения — одна миллионная доля рубля, округляется до копеек. Учитывается только для автоматических кампаний брендов и агентств. В других организациях установить новое ограничение общего бюджета не получится. Если у кампании уже установлен бюджет, можно: убрать ограничения — передайте `0` в этом параметре; не менять бюджет кампании — когда он будет исчерпан, уберите ограничения бюджета или создайте новую кампанию с неограниченным бюджетом |
| `dailyBudget` | string \<uint64\> | Нет | **Deprecated.** Ограничение дневного бюджета рекламной кампании. Единица измерения — одна миллионная доля рубля, округляется до копеек. Если параметр не заполнен, дневной бюджет не ограничен. После создания рекламной кампании изменить бюджет с дневного на недельный и наоборот не получится |
| `weeklyBudget` | string \<uint64\> | Нет | Ограничение недельного бюджета рекламной кампании. Единица измерения — одна миллионная доля рубля, округляется до копеек. Если параметр не заполнен, недельный бюджет не ограничен. После создания рекламной кампании изменить бюджет с недельного на дневной и наоборот не получится |

### Ответ 200 — Параметры кампании обновлены

| Поле | Тип | Описание |
|---|---|---|
| `campaignId` | string \<uint64\> | Идентификатор кампании |

**Пример запроса:**

```http
PATCH /api/client/campaign/48852 HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "autopilot": {
    "categoryId": "string",
    "skuAddMode": "PRODUCT_CAMPAIGN_SKU_ADD_MODE_UNKNOWN"
  },
  "fromDate": "string",
  "toDate": "string",
  "budget": "string",
  "dailyBudget": "string",
  "weeklyBudget": "string"
}
```

**Пример ответа (200):**

```json
{
  "campaignId": "string"
}
```

**Ошибка:** `default` — ошибка запроса.

---

## Рассчитать минимальный бюджет кампании

```http
POST /external/api/dynamic_budget
```

> **Deprecated.** 1 сентября 2025 года метод был отключён. Теперь минимальный бюджет рассчитывается по формуле: **2 000 рублей × 1 SKU**.

### Тело запроса

| Поле | Тип | Обязательный | Описание |
|---|---|---|---|
| `createCampaign` | object | Нет | Параметры для расчёта при создании кампании |
| `createCampaign.autopilotStrategy` | string | Нет | Стратегия кампании, например `NO_AUTO_STRATEGY` |
| `createCampaign.placement` | string | Нет | Тип размещения, например `CAMPAIGN_PLACEMENT_INVALID` |
| `createCampaign.skusCount` | string | Нет | Количество товаров в кампании |
| `updateCampaign` | object | Нет | Параметры для расчёта при обновлении кампании |
| `updateCampaign.addingSkus` | array of string | Нет | Список добавляемых товаров |
| `updateCampaign.autopilotStrategy.strategy` | string | Нет | Стратегия кампании, например `NO_AUTO_STRATEGY` |
| `updateCampaign.campaignId` | string | Нет | Идентификатор кампании |

### Ответ 200 — Результат запроса

| Поле | Тип | Описание |
|---|---|---|
| `campaignBudget` | string \<uint64\> | Бюджет рекламной кампании. Единица измерения — одна миллионная доля рубля, округляется до копеек |
| `dynamicBudget` | string \<uint64\> | Минимальный бюджет |
| `dynamicBudgetType` | string | Тип минимального бюджета. Default: `DYNAMIC_BUDGET_REQUIRED`. Enum: `DYNAMIC_BUDGET_REQUIRED` — обязательный; `DYNAMIC_BUDGET_RECOMMENDED` — рекомендованный |
| `skuPrice` | string \<uint64\> | Сумма в рублях, на которую увеличивается минимальный бюджет за каждый добавленный в кампанию товар |

**Пример запроса:**

```http
POST /external/api/dynamic_budget HTTP/1.1
Host: api-performance.ozon.ru:443
Content-Type: application/json
Accept: application/json
Authorization: Bearer <token>
```

```json
{
  "createCampaign": {
    "autopilotStrategy": "NO_AUTO_STRATEGY",
    "placement": "CAMPAIGN_PLACEMENT_INVALID",
    "skusCount": "string"
  },
  "updateCampaign": {
    "addingSkus": [
      "string"
    ],
    "autopilotStrategy": {
      "strategy": "NO_AUTO_STRATEGY"
    },
    "campaignId": "string"
  }
}
```

**Пример ответа (200):**

```json
{
  "campaignBudget": "string",
  "dynamicBudget": "string",
  "dynamicBudgetType": "DYNAMIC_BUDGET_REQUIRED",
  "skuPrice": "string"
}
```

**Ошибка:** `default` — ошибка запроса.
