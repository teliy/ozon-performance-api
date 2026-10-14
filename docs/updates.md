# Обновления Ozon Performance API

> История изменений API. Источник: «Документация Ozon Performance API (2.0)». Возврат к [главной странице](../README.md).

## 5 октября 2026

| Метод | Изменение |
|---|---|
| — | В разделе «Лимиты на запросы» обновили информацию о лимитах на работу с кампаниями |

## 4 сентября 2026

| Метод | Изменение |
|---|---|
| — | В раздел «Лимиты на запросы» добавили лимиты на работу с кампаниями. Введём лимиты 14 сентября 2026 года |

## 6 августа 2026

| Метод | Изменение |
|---|---|
| `GET /api/client/campaign` | Добавили значение `PLACEMENT_TILE_MAIN` в параметре `list.placement` в ответе метода |
| `POST /api/client/statistics` | Обновили описание метода |

## 8 июня 2026

| Метод | Изменение |
|---|---|
| `GET /api/client/statistics/campaign/product` | Обновили описание метода |
| `POST /api/client/statistics/products/sku` | Добавили метод для получения статистики по товарам для кампании с оплатой за клик |

## 2 июня 2026

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/{campaignId}/products` | Добавили параметр `bids.topPosition` в запрос методов |
| `PUT /api/client/campaign/{campaignId}/products` | Добавили параметр `bids.topPosition` в запрос методов |
| `GET /api/client/campaign/{campaignId}/v2/products` | Добавили параметр `products.topPosition` в ответ метода |
| `GET /api/client/campaign/all_sku_promo/activate` | Добавили параметр `selectedBid` в ответ метода |
| `GET /api/client/campaign/all_sku_promo/set_bid` | Добавили метод для установки ставки продвижения в Оплате за заказ |

## 22 мая 2026

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/cpc/v2/product` | Обновили описание метода. В запросе метода: обновили описание параметра `productAutopilotStrategy`; удалили параметр `ProductAdvPlacements`; пометили устаревшим параметр `dailyBudget` |
| `POST /api/client/campaign/{campaignId}/activate` | В ответе методов: обновили описание параметров `productAutopilotStrategy` и `placement`; удалили параметры `ProductAdvPlacements` и `advObjectType`; пометили устаревшим параметр `dailyBudget` |
| `POST /api/client/campaign/{campaignId}/deactivate` | Аналогично `activate` |
| `PATCH /api/client/campaign/{campaignId}` | В запросе метода: удалили параметр `ProductAdvPlacements`; пометили устаревшим параметр `dailyBudget` |
| `POST /api/client/campaign/{campaignId}/products` | В запросе методов: добавили параметр `bids.targetCir`; обновили описание параметра `bids.bid` |
| `PUT /api/client/campaign/{campaignId}/products` | В запросе методов: добавили параметр `bids.targetCir`; обновили описание параметра `bids.bid` |
| `GET /api/client/campaign/{campaignId}/v2/products` | В ответе метода: добавили параметр `products.targetCir`; обновили описание параметра `products.bid` |

## 6 апреля 2026

| Метод | Изменение |
|---|---|
| — | Изменили название раздела «Как получить API-ключ» на «Авторизация через API-ключ» |
| — | Добавили раздел «Авторизация через OAuth-токен» |

## 19 марта 2026

| Метод | Изменение |
|---|---|
| `GET /api/client/campaign/all_sku_promo/activate` | Добавили методы для работы с продвижением всех товаров в оплате за заказ |
| `GET /api/client/campaign/all_sku_promo/deactivate` | Добавили методы для работы с продвижением всех товаров в оплате за заказ |
| `GET /api/client/statistics/all_sku_promo/orders/generate` | Добавили методы для работы с продвижением всех товаров в оплате за заказ |
| `GET /api/client/statistics/all_sku_promo/products/generate` | Добавили методы для работы с продвижением всех товаров в оплате за заказ |
| `POST /api/client/statistic/orders/generate` | Обновили названия методов |
| `POST /api/client/statistic/products/generate` | Обновили названия методов |

## 16 февраля 2026

| Метод | Изменение |
|---|---|
| `POST /api/client/statistics/phrases` | Добавили метод для получения отчёта по поисковым запросам |

## 20 января 2026

| Метод | Изменение |
|---|---|
| `POST /api/client/statistics/video` | Изменили содержание отчётов в описании методов |
| `POST /api/client/statistics/attribution` | Изменили содержание отчётов в описании методов |
| `GET /api/client/statistics/campaign/media` | Изменили содержание отчётов в описании методов |
| `GET /api/client/statistics/expense` | Изменили содержание отчётов в описании методов |
| `GET /api/client/statistics/daily` | Изменили содержание отчётов в описании методов |
| `GET /api/client/statistics/campaign/product` | Изменили содержание отчётов в описании методов |
| `POST /api/client/statistic/orders/generate` | Изменили содержание отчётов в описании методов |
| `POST /api/client/statistic/products/generate` | Изменили содержание отчётов в описании методов |
| `POST /api/client/statistics` | Изменили содержание отчётов в описании методов |

## 15 января 2026

| Метод | Изменение |
|---|---|
| `GET /api/client/campaign` | Обновили описание методов. Удалили параметр `autoIncrease` из ответа методов |
| `POST /api/client/campaign/cpc/v2/product` | В запросе метода: пометили параметр `ProductAdvPlacements` как устаревший; удалили параметр `autoIncreasePercent`. Удалили значение `PLACEMENT_OVERTOP` параметра `placement` и значение `TAKEOVER` параметра `productAutopilotStrategy` в запросе метода |
| `POST /api/client/campaign/{campaignId}/activate` | Пометили параметр `ProductAdvPlacements` как устаревший в ответе метода. Удалили параметр `autoIncrease` из ответа методов |
| `POST /api/client/campaign/{campaignId}/deactivate` | Обновили описание методов. Удалили параметр `autoIncrease` из ответа методов |
| `PATCH /api/client/campaign/{campaignId}` | В запросе методов: пометили параметр `ProductAdvPlacements` как устаревший; удалили параметр `autoIncreasePercent` |

## 18 ноября 2025

| Метод | Изменение |
|---|---|
| `GET /api/client/products_with_bonuses` | Добавили метод для получения списка товаров с бонусами |

## 31 октября 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/statistic/products/generate` | Обновили описание метода |

## 29 октября 2025

| Метод | Изменение |
|---|---|
| `GET /api/client/statistics/campaign/product` | Обновили описание метода |

## 23 октября 2025

| Метод | Изменение |
|---|---|
| `GET /api/client/campaign` | Добавили значение `TOP_PROMOTION` в параметр `list.productAutopilotStrategy` в ответе метода |
| `POST /api/client/campaign/{campaignId}/activate` | Добавили значение `TOP_PROMOTION` в параметр `productAutopilotStrategy` в ответе методов |
| `POST /api/client/campaign/{campaignId}/deactivate` | Добавили значение `TOP_PROMOTION` в параметр `productAutopilotStrategy` в ответе методов |
| `POST /api/client/campaign/cpc/v2/product` | Добавили значение `TOP_PROMOTION` в параметр `productAutopilotStrategy` в запросе метода |

## 21 октября 2025

| Метод | Изменение |
|---|---|
| `GET /api/client/campaign` | Параметр автоподнятия `list.autoIncrease` устаревает, отключим его с 29 октября 2025 |
| `POST /api/client/campaign/cpc/v2/product` | Параметр автоподнятия `autoIncreasePercent` устаревает, отключим его с 29 октября 2025 |
| `PATCH /api/client/campaign/{campaignId}` | Параметр автоподнятия `autoIncreasePercent` устаревает, отключим его с 29 октября 2025 |
| `POST /api/client/campaign/{campaignId}/activate` | Параметр автоподнятия `autoIncrease` устаревает, отключим его с 29 октября 2025 |
| `POST /api/client/campaign/{campaignId}/deactivate` | Параметр автоподнятия `autoIncrease` устаревает, отключим его с 29 октября 2025 |

## 13 октября 2025

| Метод | Изменение |
|---|---|
| `GET /api/client/campaign` | Добавили параметры `list.isAutocreated` и `list.autostopStatus` в ответ метода |
| `POST /api/client/campaign/{campaignId}/activate` | Добавили параметры `isAutocreated` и `autostopStatus` в ответ методов |
| `POST /api/client/campaign/{campaignId}/deactivate` | Добавили параметры `isAutocreated` и `autostopStatus` в ответ методов |

## 2 октября 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/search_promo/carrots/enable` | Обновили описание методов |
| `POST /api/client/campaign/search_promo/carrots/disable` | Обновили описание методов |

## 2 сентября 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/search_promo/carrots/enable` | Добавили методы для включения и отключения продвижения товара в акции «Морковск» |
| `POST /api/client/campaign/search_promo/carrots/disable` | Добавили методы для включения и отключения продвижения товара в акции «Морковск» |
| `POST /api/client/campaign/search_promo/v2/products` | Добавили параметры `products.bidWithoutAdditive`, `products.carrotsAdditive` и `products.carrotsStatus` в ответ метода |

## 1 сентября 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/cpc/v2/product` | Обновили описание параметров `placement` и `productAutopilotStrategy` в запросе метода |
| `POST /api/client/campaign/{campaignId}/activate` | Обновили описание параметров `paymentType`, `advObjectType`, `placement` и `productAutopilotStrategy` в ответе методов |
| `POST /api/client/campaign/{campaignId}/deactivate` | Аналогично `activate` |
| `POST /external/api/dynamic_budget` | Обновили описание параметров `createCampaign.autopilotStrategy`, `createCampaign.placement` и `updateCampaign.autopilotStrategy` в запросе метода |
| `GET /api/client/campaign` | Обновили описание параметра `advObjectType` в запросе метода. Обновили описание параметров `list.advObjectType`, `list.placement` и `list.productAutopilotStrategy` в ответе метода |
| `GET /api/client/campaign/{campaignId}/objects` | Обновили описание методов |
| `POST /api/client/statistics` | Обновили описание метода |
| `GET /api/client/limits/list` | Обновили описание метода. Обновили описание параметров `limits.objectType` и `limit.placement` в ответе метода |
| `POST /api/client/min/sku` | Обновили описание параметра `paymentType` в запросе метода |
| `GET /api/client/statistics/campaign/product` | Изменили название метода |
| — | Изменили название раздела «Трафареты и вывод в топ» на «Оплата за клик» |
| — | Изменили название раздела «Товары в Трафаретах и Выводе в топ» на «Товары в Оплате за клик и Спецразмещении» |

## 25 августа 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/cpc/v2/product` | Обновили описание метода. В запросе метода: добавили значение `PLACEMENT_OVERTOP` в параметр `placement`; добавили значение `TAKEOVER` в параметр `productAutopilotStrategy`; добавили параметр `ProductAdvPlacements` |
| `PATCH /api/client/campaign/{campaignId}` | Добавили параметр `ProductAdvPlacements` в запрос метода |
| `POST /api/client/campaign/{campaignId}/activate` | В ответе методов: добавили значение `PLACEMENT_OVERTOP` в параметр `placement`; добавили значение `TAKEOVER` в параметр `productAutopilotStrategy`; добавили параметр `ProductAdvPlacements` |
| `POST /api/client/campaign/{campaignId}/deactivate` | Аналогично `activate` |

## 19 августа 2025

| Метод | Изменение |
|---|---|
| `POST /external/api/dynamic_budget` | Метод устаревает и будет отключён 1 сентября 2025 года |

## 24 июля 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/cpc/v2/product` | В запросе метода: пометили устаревшим значение `PLACEMENT_TAKEOVER` в параметре `placement`; удалили значение `TAKEOVER` в параметре `productAutopilotStrategy`; обновили описание значения `TARGET_BIDS` в параметре `productAutopilotStrategy` |
| `POST /api/client/min/sku` | Обновили описание параметра `paymentType` в запросе метода |
| `GET /api/client/campaign` | Обновили описание параметра `advObjectType` в запросе метода. Обновили описание параметра `list.advObjectType` в ответе метода. Добавили значение `PLACEMENT_OVERTOP` в параметре `list.placement` в ответе метода |
| `POST /api/client/campaign/{campaignId}/activate` | В ответе методов: пометили устаревшим значение `PLACEMENT_TAKEOVER` в параметре `placement`; удалили значение `TAKEOVER` в параметре `productAutopilotStrategy`; обновили описание параметра `advObjectType` |
| `POST /api/client/campaign/{campaignId}/deactivate` | Аналогично `activate` |
| `GET /api/client/limits/list` | Обновили описание параметра `limits.objectType` в ответе метода. Добавили значение `CAMPAIGN_PLACEMENT_OVERTOP` в параметре `limits.placement` в ответе метода |
| `POST /api/client/campaign/search_promo/v2/products` | Обновили описание метода. Обновили описание параметров `products.isSearchPromoAvailable` и `products.searchPromoStatus` в ответе метода |
| `GET /api/client/statistics/{UUID}` | Изменили название метода. Обновили описание параметра `kind` в ответе метода |
| `GET /api/client/statistics/list` | Обновили описание параметра `items.meta.kind` в ответе методов |
| `GET /api/client/statistics/externallist` | Обновили описание параметра `items.meta.kind` в ответе методов |
| `GET /api/client/campaign/{campaignId}/objects` | Обновили описание методов |
| `POST /api/client/statistics` | Обновили описание методов |
| `POST /api/client/statistic/orders/generate` | Изменили название методов |
| `POST /api/client/statistic/products/generate` | Изменили название методов |
| `POST /api/client/campaign/search_promo/v2/bids/delete` | Изменили название методов |
| `POST /api/client/search_promo/product/enable` | Изменили название методов |
| `POST /api/client/search_promo/product/disable` | Изменили название методов |
| `POST /external/api/dynamic_budget` | В запросе метода: пометили устаревшим значение `CAMPAIGN_PLACEMENT_TAKEOVER` в параметре `createCampaign.placement`; удалили значение `TAKEOVER` в параметре `createCampaign.autopilotStrategy`; удалили значение `TAKEOVER` в параметре `updateCampaign.autopilotStrategy` |
| — | Изменили название раздела «Продвижение в поиске» на «Оплата за заказ» |

## 17 июля 2025

| Метод | Изменение |
|---|---|
| `POST /external/api/dynamic_budget` | Обновили описание параметра `skuPrice` в ответе метода |

## 10 июня 2025

| Метод | Изменение |
|---|---|
| `GET /api/client/campaign` | Добавили параметры `page` и `pageSize` в запрос метода |

## 17 апреля 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/min/sku` | Добавили новый метод для получения минимальной ставки для товаров по SKU |
| `GET /api/client/campaign/{campaignId}/brand_shelf/{brandShelfId}` | Удалили метод из документации |
| `POST /api/client/campaign/cpc/v2/product` | Добавили параметр `autoIncreasePercent` в запрос методов |
| `PATCH /api/client/campaign/{campaignId}` | Добавили параметр `autoIncreasePercent` в запрос методов |
| `GET /api/client/campaign` | Добавили параметры `autoIncrease.autoIncreasePercent`, `autoIncrease.isAutoIncreased`, `autoIncrease.autoIncreasedBudget`, `autoIncrease.recommendedAutoIncreasePercent` в ответ методов |
| `POST /api/client/campaign/{campaignId}/activate` | Аналогично `GET /campaign` |
| `POST /api/client/campaign/{campaignId}/deactivate` | Аналогично `GET /campaign` |

## 4 апреля 2025

| Метод | Изменение |
|---|---|
| `GET /api/client/statistics/report` | Обновили описание метода. Изменили структуру заголовков и тела ответа |

## 1 апреля 2025

| Метод | Изменение |
|---|---|
| `GET /api/client/statistics/campaign/product` | Обновили описание метода |

## 25 марта 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/search_promo/get_cpo_min_bids` | Обновили название параметра в запросе метода |

## 3 марта 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/cpc/v2/product` | Обновили описание параметров `placement` и `productAutopilotStrategy` в запросе метода |
| `POST /api/client/campaign/{campaignId}/activate` | Обновили описание параметров `placement` и `productAutopilotStrategy` в ответе методов |
| `POST /api/client/campaign/{campaignId}/deactivate` | Аналогично `activate` |
| `POST /external/api/dynamic_budget` | Обновили описание параметров `createCampaign.autopilotStrategy`, `createCampaign.placement` и `updateCampaign.autopilotStrategy.strategy` в запросе метода |

## 26 февраля 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/search_promo/bids/recommendation` | Пометили методы устаревшими |
| `POST /api/client/campaign/search_promo/v2/bids/set` | Пометили методы устаревшими |
| `POST /api/client/search_promo/get_cpo_min_bids` | Добавили метод для получения фиксированных ставок на товары |

## 20 января 2025

| Метод | Изменение |
|---|---|
| `POST /external/api/dynamic_budget` | Добавили метод для расчёта минимального бюджета кампании |

## 9 января 2025

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/cpc/v2/product` | Обновили описание параметра `productAutopilotStrategy` в запросе метода |
| `PATCH /api/client/campaign/{campaignId}` | Удалили параметр `autopilot.skuAddMode` в запросе метода |

## 28 ноября 2024

| Метод | Изменение |
|---|---|
| `GET /api/client/statistics/campaign/product` | Добавили недельный бюджет в отчёт |

## 31 октября 2024

| Метод | Изменение |
|---|---|
| `POST /api/client/campaign/cpc/v2/product` | Удалили параметр `productCampaignMode` в запросе метода |
| `GET /api/client/statistics/campaign/media` | Обновили описание методов |
| `GET /api/client/statistics/campaign/product` | Обновили описание методов |

## 11 октября 2024

| Метод | Изменение |
|---|---|
| `GET /api/client/statistics/externallist` | Добавили метод для получения списка отчётов, сгенерированных через API |
| `GET /api/client/statistics/list` | Обновили описание метода |
| `GET /api/client/campaign` | Обновили значение `CAMPAIGN_STATE_STOPPED` параметра `state` в запросе и параметра `list.state` в ответе метода |
| `POST /api/client/campaign/{campaignId}/activate` | Обновили значение `CAMPAIGN_STATE_STOPPED` параметра `state` в ответах методов |
| `POST /api/client/campaign/{campaignId}/deactivate` | Обновили значение `CAMPAIGN_STATE_STOPPED` параметра `state` в ответах методов |

## 26 сентября 2024

| Метод | Изменение |
|---|---|
| Все методы | С 15 января 2025 года хост `performance.ozon.ru` перестаёт работать. Перейдите на новый хост `api-performance.ozon.ru` |

## 3 сентября 2024

| Метод | Изменение |
|---|---|
| `GET /campaign/{campaignId}/products` | Метод устарел, удалили его из документации. Используйте `GET /campaign/{campaignId}/v2/products` |
| `POST /campaign/{campaignId}/search_promo/products` | Метод устарел, удалили его из документации. Используйте `POST /campaign/search_promo/v2/products` |
| `POST /campaign/{campaignId}/search_promo/bids/set` | Метод устарел, удалили его из документации. Используйте `POST /campaign/search_promo/v2/bids/set` |
| `POST /campaign/cpc/product` | Метод устарел, удалили его из документации. Используйте `POST /campaign/cpc/v2/product` |
| `POST /campaign/{campaignId}/search_promo/bids/delete` | Метод устарел, удалили его из документации. Используйте `POST /campaign/search_promo/v2/bids/delete` |
| `POST /campaign/cpm/v2/product` | Методы устарели, удалили их из документации |
| `PATCH /campaign/{campaignId}/brand_shelf/{brandShelfId}` | Методы устарели, удалили их из документации |
| `POST /campaign/search_promo/v2/bids/delete` | В описании методов добавили, что в одном запросе можно передать максимум 1000 товаров |
| `POST /search_promo/product/enable` | В описании методов добавили, что в одном запросе можно передать максимум 1000 товаров |
| `POST /search_promo/product/disable` | В описании методов добавили, что в одном запросе можно передать максимум 1000 товаров |

## 29 августа 2024

| Метод/раздел | Описание |
|---|---|
| `POST /campaign/cpc/v2/product` | Обновили описание параметра `productAutopilotStrategy` в запросе метода |
| `POST /campaign/{campaignId}/activate` | Обновили в ответе метода описание параметров `advObjectType`, `placement` и `productAutopilotStrategy` |
| `POST /campaign/{campaignId}/deactivate` | Аналогично `activate` |
| `GET /campaign` | Обновили описание параметра `advObjectType` в запросе метода |
| `GET /campaign/{campaignId}/objects` | Обновили описание метода |
| `GET /limits/list` | Обновили описание метода и параметров в ответе: `limits.objectType` и `limits.placement` |
| `GET /statistics/campaign/product` | Обновили примеры запросов |
| `GET /statistics/campaign/media` | Обновили примеры запросов |
| Трафареты и Вывод в топ | Обновили названия разделов |
| Товары в Трафаретах и Выводе в топ | Обновили названия разделов |

## 15 августа 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/{campaignId}/products` | В параметрах `bid`, `bids` и SKU уточнили, что ставка применяется только к заказам или кликам |
| `PUT /campaign/{campaignId}/products` | Аналогично |
| `GET /campaign/{campaignId}/v2/products` | Аналогично |
| `POST /campaign/search_promo/v2/products` | Аналогично |
| `POST /search_promo/bids/recommendation` | Аналогично |
| `POST /campaign/search_promo/v2/bids/set` | Аналогично |

## 7 августа 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/{campaignId}/v2/activate` | Методы не использовались, удалили их из документации. Используйте `POST /campaign/{campaignId}/activate` и `POST /campaign/{campaignId}/deactivate` |
| `POST /campaign/{campaignId}/v2/deactivate` | Аналогично |
| `POST /campaign/{campaignId}/activate` | Убрали отметки, что методы устарели |
| `POST /campaign/{campaignId}/deactivate` | Убрали отметки, что методы устарели |
| `POST /campaign/search_promo/v2/bids/set` | Обновили параметры ответа методов |
| `POST /search_promo/product/enable` | Обновили параметры ответа методов |
| `POST /campaign/{campaignId}/search_promo/bids/reset` | Метод устарел, удалили его из документации |

## 22 июля 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/cpc/product` | Добавили параметр `weeklyBudget` в запросы методов |
| `POST /campaign/cpc/v2/product` | Добавили параметр `weeklyBudget` в запросы методов |
| `PATCH /campaign/{campaignId}` | Добавили параметр `weeklyBudget` в запросы методов |
| `POST /campaign/{campaignId}/v2/activate` | Добавили параметр `weeklyBudget` в запросы методов |
| `POST /campaign/{campaignId}/activate` | Добавили параметр `weeklyBudget` в ответы методов |
| `GET /campaign` | Добавили параметр `weeklyBudget` в ответы методов |

## 3 июля 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/cpm/product` | Метод устарел, удалили его из документации |
| `POST /campaign/cpm/v2/product` | Пометили метод устаревшим |
| `POST /campaign/{campaignId}/v2/activate` | Обновили описания методов |
| `POST /campaign/{campaignId}/activate` | Обновили описания методов |

## 1 июля 2024

| Метод | Изменение |
|---|---|
| `GET /campaign/{campaignId}/brand_shelf/{brandShelfId}` | Брендовая полка перестала работать, пометили методы устаревшими |
| `PATCH /campaign/{campaignId}/brand_shelf/{brandShelfId}` | Брендовая полка перестала работать, пометили методы устаревшими |
| `GET /limits/list` | Убрали упоминание брендовой полки в описании методов и параметров |
| `GET /campaign/{campaignId}/objects` | Убрали упоминание брендовой полки |
| `POST /statistics` | Убрали упоминание брендовой полки |
| `POST /statistics/attribution` | Убрали упоминание брендовой полки |

## 23 мая 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/cpm/v2/product` | Удалили параметр `expenseStrategy` в запросе метода |
| `POST /campaign/cpc/v2/product` | Удалили параметр `expenseStrategy` в запросе метода |
| `PATCH /campaign/{campaignId}` | Удалили параметр `expenseStrategy` в запросе метода |
| `POST /campaign/cpc/v2/product` | Дополнили описание параметра `productAutopilotStrategy` в запросе метода |
| `GET /campaign` | Дополнили описание параметра `list.placement` в ответе метода |
| `POST /campaign/cpm/v2/product` | Дополнили описание параметра `placement` в запросе метода |
| `POST /campaign/{campaignId}/v2/activate` | Дополнили описание параметра `productAutopilotStrategy` в ответе метода |
| `POST /campaign/{campaignId}/v2/deactivate` | Дополнили описание параметра `productAutopilotStrategy` в ответе метода |

## 26 апреля 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/search_promo/v2/products` | Добавили параметр `products.isSearchPromoAvailable` в ответ метода |

## 22 апреля 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/cpm/v2/product` | В запросе метода: удалили параметр `autopilot`; изменили значение по умолчанию у параметра `productCampaignMode` |
| `POST /campaign/cpc/v2/product` | В запросе метода: удалили параметр `autopilot`; изменили значение по умолчанию у параметра `productCampaignMode` |
| `POST /statistic/orders/generate` | Добавили метод для получения отчёта по заказам в оплате за заказ |
| `POST /statistic/products/generate` | Добавили метод для получения отчёта по товарам в оплате за заказ |

## 19 марта 2024

| Метод | Изменение |
|---|---|
| `GET /limits/list` | Добавили метод для получения: минимальных и максимальных ставок для «Оплаты за заказ», «Трафаретов» и «Брендовой полки»; минимальных ставок по категориям товаров в «Оплате за заказ» и «Трафаретах» |

## 5 марта 2024

| Метод | Изменение |
|---|---|
| `PUT /campaign/{campaignId}/products` | Обновили описание метода |
| `POST /campaign/search_promo/v2/products` | Обновили описание параметра `page` в запросе |
| — | В разделе «Лимиты на запросы» повысили лимиты до 2000 на количество выгрузок за 24 часа с аккаунта и в рамках организации |

## 22 февраля 2024

| Метод | Изменение |
|---|---|
| `GET /campaign/{campaignId}/products` | Пометили метод устаревшим. Используйте `GET /campaign/{campaignId}/v2/products` |
| `POST /campaign/cpm/product` | Пометили метод устаревшим |
| `POST /campaign/cpc/product` | Пометили метод устаревшим. Используйте `POST /campaign/cpc/v2/product` |
| `POST /campaign/{campaignId}/activate` | Пометили метод устаревшим. Используйте `POST /campaign/{campaignId}/v2/activate` |
| `POST /campaign/{campaignId}/deactivate` | Пометили метод устаревшим. Используйте `POST /campaign/{campaignId}/v2/deactivate` |
| `GET /campaign/{campaignId}/v2/products` | Добавили новый метод для получения списка товаров кампании |
| `POST /campaign/cpm/v2/product` | Добавили новый метод для создания кампании с оплатой за показы |
| `POST /campaign/cpc/v2/product` | Добавили новый метод для создания кампании с оплатой за клики |
| `POST /campaign/{campaignId}/v2/activate` | Добавили новый метод для активации кампании |
| `POST /campaign/{campaignId}/v2/deactivate` | Добавили новый метод для выключения кампании |
| `GET /campaign/{campaignId}/products/bids/competitive` | Добавили новый метод для получения конкурентных ставок для товара в Трафаретах |

## 26 января 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/{campaignId}/search_promo/products` | Пометили методы устаревшими, используйте новые методы для управления оплатой за заказ |
| `POST /campaign/{campaignId}/search_promo/bids/set` | Пометили методы устаревшими |
| `POST /campaign/{campaignId}/search_promo/bids/reset` | Пометили методы устаревшими |
| `POST /campaign/{campaignId}/search_promo/bids/delete` | Пометили методы устаревшими |
| `POST /campaign/search_promo/v2/products` | Добавили метод для получения списка товаров из оплаты за заказ |
| `POST /search_promo/bids/recommendation` | Добавили метод для получения рекомендованных ставок для товаров из оплаты за заказ |
| `POST /campaign/search_promo/v2/bids/set` | Добавили метод для установки ставок на оплату за заказ для товаров |
| `POST /search_promo/product/enable` | Добавили метод для включения оплаты за заказ для товара |
| `POST /search_promo/product/disable` | Добавили метод для отключения оплаты за заказ для товара |
| `POST /campaign/search_promo/v2/bids/delete` | Добавили метод для удаления товаров из оплаты за заказ |

## 17 января 2024

| Метод | Изменение |
|---|---|
| `POST /campaign/cpm/product` | Обновили описания методов. Удалили параметр `productCampaignMode` из запросов методов |
| `POST /campaign/cpc/product` | Обновили описания методов. Удалили параметр `productCampaignMode` из запросов методов |
| `POST /campaign/{campaignId}/products` | Обновили описание метода. Удалили параметры `phrases`, `groupId` и `stopWords` из запроса метода |
| `PUT /campaign/{campaignId}/products` | Удалили параметры `phrases`, `groupId` и `stopWords` из запроса метода |
| `GET /campaign/{campaignId}/products` | Удалили параметры `phrases`, `groupId` и `stopWords` из ответа метода |
| `GET /campaign/{campaignId}/objects` | Обновили описания методов |
| `POST /statistics/attribution` | Обновили описания методов |
| `POST /statistics` | Обновили описания методов |
| `POST /statistics/video` | Обновили описания методов |
| — | Раздел «Лимиты на ставки» устарел, удалили его из документации |
| `GET /campaign/available` | Методы устарели, удалили их из документации |
| `POST /campaign/{campaignId}/group` | Методы устарели, удалили их из документации |
| `GET /campaign/{campaignId}/group/{groupId}` | Методы устарели, удалили их из документации |
| `PUT /campaign/{campaignId}/group/{groupId}` | Методы устарели, удалили их из документации |
| `POST /statistics/phrases` | Методы устарели, удалили их из документации (впоследствии метод вернули) |
| `PUT /campaign/{campaignId}/period` | Методы устарели, удалили их из документации. Используйте `PATCH /campaign/{campaignId}` |
| `PUT /campaign/{campaignId}/daily_budget` | Методы устарели, удалили их из документации. Используйте `PATCH /campaign/{campaignId}` |

## 21 декабря 2023

| Метод | Изменение |
|---|---|
| `POST /statistics/` | Добавили в описание методов информацию о JSON-формате отчётов |
| `POST /statistics/video` | Аналогично |
| `POST /statistics/attribution` | Аналогично |
| `GET /statistics/campaign/media` | Аналогично |
| `GET /statistics/campaign/product` | Аналогично |
| `GET /statistics/daily` | Аналогично |
| `GET /statistics/expense` | Аналогично |

## 20 октября 2023

| Метод | Изменение |
|---|---|
| — | Обновили заголовки разделов: «Товарные рекламные кампании» на «Трафареты» и «Товары в рекламной кампании» на «Товары в Трафаретах» |
| `GET /campaign` | Обновили описание параметра `advObjectType` в запросе метода. Добавили параметр `paymentType` в ответ метода |

## 10 апреля 2023

| Метод | Изменение |
|---|---|
| `POST /statistics/phrases` | Удалили параметр `groupBy` из запроса метода |

## 3 ноября 2022

| Метод | Изменение |
|---|---|
| — | Обновили лимиты на ставки и добавили метод оплаты «Клики» для кампаний с размещением в «Карточке товара и категории» |
| `POST /campaign/cpc/product` | Добавили метод для создания рекламных кампаний с оплатой за клики |
| `POST /campaign/{campaignId}/products` | В описание метода добавили рекомендации по добавлению товаров в кампании с оплатой за клики |
| `PUT /campaign/{campaignId}/daily_budget` | Из запроса метода убрали параметры `fromDate` и `toDate` |
| `PUT /campaign/{campaignId}/period` | Из запроса метода убрали параметр `dailyBudget` |
| `PATCH /campaign/{campaignId}` | В запрос метода добавили параметр `autopilot` для передачи информации о кампаниях с включённой автостратегией |
| `POST /campaign/cpm/product` | Изменили описание параметра `budget`. В запрос метода добавили параметр `autopilot.skuAddMode` для включения автоматического добавления товаров в кампании. В запросе метода обновили описание параметра `toDate`. В запрос метода добавили параметр `budget` |
| `GET /campaign` | В ответ метода добавили поле `autopilot.skuAddMode` для получения информации об автоматическом добавлении товаров в кампании |

## 5 сентября 2022

| Метод | Изменение |
|---|---|
| `GET /campaign` | Добавили поля с информацией об автостратегиях `productAutopilotStrategy` и `autopilot` в ответы методов |
| `POST /campaign/{campaignId}/activate` | Аналогично |
| `POST /campaign/{campaignId}/deactivate` | Аналогично |
| `POST /campaign/cpm/product` | Добавили параметры `productAutopilotStrategy` и `autopilot` для передачи информации об автостратегиях в запрос метода |
| `POST /campaign/{campaignId}/products` | Добавили ограничения при работе с кампаниями с включённой автостратегией в описания методов |
| `PUT /campaign/{campaignId}/products` | Аналогично |

## 2 сентября 2022

| Метод | Изменение |
|---|---|
| `GET /campaign/{campaignId}/products` | Добавили в ответ поля: `categories.bid` — ставка на категорию; `categories.categoryId` — идентификатор категории; `title` — название товара |

## 30 августа 2022

| Метод | Изменение |
|---|---|
| `POST /statistics/video` | Добавили метод для получения статистики по показам видеобаннера |

## 22 августа 2022

| Метод | Изменение |
|---|---|
| `GET /organisation/vendor_tag` | Добавили метод для получения меток организации для внешних рекламных кампаний |

## 11 августа 2022

| Метод | Изменение |
|---|---|
| `GET /statistics/report` | Добавили описание ошибки некорректного UUID в ответ метода |

## 10 августа 2022

| Метод | Изменение |
|---|---|
| `GET /statistics/{UUID}` | Добавили значение для поля `kind` в ответах методов |
| `GET /statistics/list` | Добавили значение для поля `kind` в ответах методов |

## 5 августа 2022

| Метод | Изменение |
|---|---|
| `GET /campaign/{campaignId}/group/{groupId}` | Добавили метод для получения информации о группе |

## 18 июля 2022

| Метод | Изменение |
|---|---|
| — | Обновили максимальную ставку на оплату за заказ в разделе «Лимиты на ставки» |

## 15 июля 2022

| Метод | Изменение |
|---|---|
| `POST /campaign/cpm/product` | Обновили описание параметра `productCampaignMode` в запросе |
| `POST /campaign/{campaignId}/products` | Обновили описание метода |

## 14 июля 2022

| Метод | Изменение |
|---|---|
| `POST /campaign/cpm/product` | Обновили описание метода. Добавили параметр `productCampaignMode` и обновили описание параметра `placement` в запросе |
| `POST /campaign/{campaignId}/products` | Обновили описание метода. Обновили описание параметра `bids.bid` в запросе метода |
| `PUT /campaign/{campaignId}/products` | Обновили описание метода |
| `GET /campaign` | Обновили описание параметра `advObjectType` в запросе. Добавили поле `productCampaignMode` в ответ метода |
| `POST /campaign/{campaignId}/group` | Обновили описания методов |
| `PUT /campaign/{campaignId}/group/{groupId}` | Обновили описания методов |
| `POST /statistics/phrases` | Обновили описания методов |
| `GET /campaign/available` | Добавили метод для получения доступных режимов создания рекламных кампаний |

## 11 июля 2022

| Метод | Изменение |
|---|---|
| — | Добавили раздел «Лимиты на ставки» |

## 8 июля 2022

| Метод | Изменение |
|---|---|
| `GET /campaign/{campaignId}/brand_shelf/{brandShelfId}` | Добавили поля `targetDeepLink` и `bids.bidMicros` в ответ метода. Уточнили возвращаемые значения для поля `image.format` в ответе. Обновили описание полей `bids.bid` и `searchBids.bid` в ответе |
| `PATCH /campaign/{campaignId}/brand_shelf/{brandShelfId}` | Убрали поле `searchBids.relevanceStatus` из запроса метода |

## 7 июля 2022

| Метод | Изменение |
|---|---|
| `POST /vendors/statistics` | Добавили метод для запуска формирования отчёта с аналитикой внешнего трафика |
| `GET /vendors/statistics/list` | Добавили метод для получения всех запрошенных отчётов с аналитикой внешнего трафика |
| `GET /vendors/statistics/{UUID}` | Добавили метод для получения информации об отчёте с аналитикой внешнего трафика |

## 5 июля 2022

| Метод | Изменение |
|---|---|
| `POST /campaign/{campaignId}/search_promo/products` | Обновили описание методов |
| `POST /campaign/{campaignId}/search_promo/bids/delete` | Обновили описание методов |

## 4 июля 2022

| Метод | Изменение |
|---|---|
| `POST /statistics` | Изменили максимальный период, за который можно получить отчёт, в параметрах запроса `to` и `from` |
| `POST /statistics/phrases` | Аналогично |
| `POST /statistics/attribution` | Аналогично |

## 30 июня 2022

| Метод | Изменение |
|---|---|
| `GET /statistics/{UUID}` | Добавили поле `kind` в ответ и пример метода |
| `POST /statistics` | Добавили поле `vendor` в ответ и пример метода |

## 28 июня 2022

| Метод | Изменение |
|---|---|
| `POST /campaign/cpc/product` | Метод устарел, удалили его из документации |
| — | Теперь получить `client_id` и `client_secret` можно в личном кабинете продавца. Добавили инструкцию в документацию |

## 27 июня 2022

| Метод | Изменение |
|---|---|
| `PUT /campaign/{campaignId}/daily_budget` | Исправили описание к параметру `dailyBudget` в запросе |

## 2 июня 2022

| Метод | Изменение |
|---|---|
| — | Добавили раздел «Лимиты на запросы» |

## 27 сентября 2021

| Метод | Изменение |
|---|---|
| — | Добавили раздел «Список методов» |
| — | Поменяли название раздела «Начало работы» на «Введение» |
| — | Поменяли название раздела «Получить токен» на «Как получить API-ключ» |
