# 📘 API Документация Iris

## 📑 Оглавление
- [📦 Методы Pocket](#-методы-pocket)
    - [pocket/balance](#pocketbalance)
    - [pocket/sweets/give](#pocketsweetsgive)
    - [pocket/gold/give](#pocketgoldgive)
    - [pocket/donate_score/give](#pocketdonate_scoregive)
    - [pocket/sweets/history](#pocketsweetshistory)
    - [pocket/gold/history](#pocketgoldhistory)
    - [pocket/donate_score/history](#pocketdonate_scorehistory)
    - [pocket/enable / disable / allow_all / deny_all](#pocketenable--pocketdisable--pocketallow_all--pocketdeny_all)
    - [pocket/allow_user](#pocketallow_user)
- [👤 Методы User Info](#-методы-user-info)
    - [user_info/reg](#user_inforeg)
    - [user_info/activity](#user_infoactivity)
    - [user_info/spam](#user_infospam)
    - [user_info/stars](#user_infostars)
    - [user_info/pocket](#user_infopocket)
- [🔄 Методы Updates](#-методы-updates)
    - [updates/getUpdates](#updatesgetupdates)
- [💰 Методы Trade](#-методы-trade)
    - [trade/buy](#tradebuy)
    - [trade/sell](#tradesell)
    - [trade/cancel_price](#tradecancel_price)
    - [trade/cancel_all](#tradecancel_all)
    - [trade/deals](#tradedeals)
    - [trade/order_book](#tradeorder_book)
- [⚙️ Остальные методы](#-остальные-методы)
    - [/iris_agents](#iris_agents)
    - [/last_version](#last_version)

---

# 📦 Методы Pocket

---

## `pocket/balance`

**💬 Ответ:**
```json
{
  "gold": float,
  "sweets": float,
  "donate_score": integer
}
```

---

## `pocket/sweets/give`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, которому отправляются ириски |
| `sweets` | float | ✅ Количество ирисок для отправки |
| `comment` | string | 💬 Комментарий к переводу |

**💬 Ответ:**
```json
{ "result": integer }
```

---

## `pocket/gold/give`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, которому отправляется голда |
| `gold` | float | ✅ Количество голды для отправки |
| `comment` | string | 💬 Комментарий к переводу |

**💬 Ответ:**
```json
{ "result": integer }
```

---

## `pocket/donate_score/give`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, которому отправляются донат-очки |
| `amount` | integer | ✅ Количество очков для отправки |
| `comment` | string | 💬 Комментарий к переводу |

**💬 Ответ:**
```json
{ "result": integer }
```

---

## `pocket/sweets/history`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `offset` | integer | 💬 Вернуть записи, где `id ≥ offset` |
| `limit` | integer | 💬 Количество записей в ответе |

**💬 Ответ:**
```json
{
  "date": integer,
  "amount": float,
  "balance": float,
  "to_user_id": integer,
  "details": {
    "total": float,
    "amount": float,
    "fee": float,
    "donate_score": integer
  },
  "id": integer,
  "type": string,
  "peer_id": integer
}
```

---

## `pocket/gold/history`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `offset` | integer | 💬 Минимальный ID записи |
| `limit` | integer | 💬 Количество записей |

**💬 Ответ:**
```json
{
  "date": integer,
  "amount": float,
  "balance": float,
  "to_user_id": integer,
  "details": {
    "total": float,
    "amount": float,
    "fee": float,
    "donate_score": integer
  },
  "id": integer,
  "type": string,
  "peer_id": integer
}
```

---

## `pocket/donate_score/history`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `offset` | integer | 💬 Минимальный ID записи |
| `limit` | integer | 💬 Количество записей |

**💬 Ответ:**
```json
[
  {
    "date": integer,
    "amount": integer,
    "balance": integer,
    "id": integer,
    "type": string,
    "peer_id": integer
  }
]
```

---

## `pocket/enable` / `pocket/disable` / `pocket/allow_all` / `pocket/deny_all`

**📤 Структура запроса:**

(Параметры отсутствуют)

**💬 Ответ:**
```json
{ "result": boolean }
```

---

## `pocket/allow_user`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, которому разрешено отправлять валюту |

---

# 👤 Методы User Info

---

## `user_info/reg`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, для получения даты регистрации |

**💬 Ответ:**
```json
{ "result": integer }
```

---

## `user_info/activity`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, для получения статистики активности |

**💬 Ответ:**
```json
{
  "result": {
    "total": integer,
    "week": integer,
    "month": integer,
    "day": integer
  }
}
```

---

## `user_info/spam`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, для проверки в базах спама/скама/игнора |

**💬 Ответ:**
```json
{
  "result": {
    "is_spam": boolean,
    "is_ignore": boolean,
    "is_scam": boolean
  }
}
```

---

## `user_info/stars`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, звёздность которого требуется получить |

**💬 Ответ:**
```json
{ "result": integer }
```

---

## `user_info/pocket`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `user_id` | integer | ✅ ID пользователя, чей мешок требуется получить |

**💬 Ответ:**
```json
{
  "result": {
    "gold": float,
    "coins": integer,
    "sweets": float,
    "stars": integer
  }
}
```

---

# 🔄 Методы Updates

---

## `updates/getUpdates`

**📤 Структура запроса:**

| Параметр | Тип     | Где   | Описание                                                                               |
| -------- | ------- | ----- | -------------------------------------------------------------------------------------- |
| `offset` | integer | query | ID последнего полученного события. Следующие события будут возвращены с `id > offset`. |


**💬 Ответ:**
```json
[
  {
    "id": 11,
    "type": "donate_score_log",
    "date": 1756286741,
    "object": { ... }
  }
]
```
📘 Описание полей:

| Поле     |   Тип   | Описание                                                                                                                        |
| :------- | :-----: | :------------------------------------------------------------------------------------------------------------------------------ |
| `id`     | integer | Уникальный идентификатор события                                                                                                |
| `type`   |  string | Тип события: `sweets_log`, `gold_log`, `donate_score_log`                                                                       |
| `date`   | integer | Время события в формате UNIX (секунды)                                                                                          |
| `object` |  object | Объект события. Совпадает по структуре с методами `pocket/sweets/history`, `pocket/gold/history`, `pocket/donate_score/history` |


---

# 💰 Методы Trade

---

## `trade/buy`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `price` | float | ✅ Цена, которую вы готовы заплатить за 1 ед. голды |
| `volume` | integer | ✅ Количество голды для покупки |

**💬 Ответ (если сделка совершена):**
```json
{
  "done_volume": integer,
  "sweets_spent": float
}
```

**💬 Ответ (если нет предложений — создаётся заявка):**
```json
{
  "done_volume": integer,
  "sweets_spent": float,
  "new_order": {
    "volume": integer,
    "price": float,
    "id": integer
  }
}
```

---

## `trade/sell`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `price` | float | ✅ Цена, по которой вы хотите продать 1 ед. голды |
| `volume` | integer | ✅ Количество голды для продажи |

**💬 Ответ (моментальная продажа):**
```json
{
  "done_volume": integer,
  "sweets_received": float
}
```

**💬 Ответ (если нет покупателей — создаётся заявка):**
```json
{
  "done_volume": integer,
  "sweets_received": float,
  "new_order": {
    "volume": integer,
    "price": float,
    "id": integer
  }
}
```

---

## `trade/cancel_price`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `price` | float | ✅ Цена покупки (от `0.01` до `1_000_000`) |

**💬 Ответ:**
```json
{
  "result": {
    "gold": float,
    "sweets": float
  }
}
```

---

## `trade/cancel_all`

**📤 Структура запроса:**

(Параметров нет)

**💬 Ответ:**
```json
{
  "result": {
    "gold": float,
    "sweets": float
  }
}
```

---


---

## `trade/deals`

**📤 Структура запроса:**

| Параметр | Тип | Описание |
|-----------|-----|-----------|
| `from_id` | integer | ID сделки, начиная с которой нужно вернуть данные (опционально) |

**💬 Ответ:**
```json
[
  {
    "id": integer,
    "group_id": integer,
    "date": integer,
    "price": float,
    "volume": integer,
    "type": string
  }
]
```

**📘 Описание полей:**

| Поле | Тип | Описание |
|:------|:------:|:------|
| `id` | integer | Уникальный идентификатор сделки |
| `group_id` | integer | Идентификатор группы связанных сделок (0, если сделка одиночная) |
| `date` | integer | Время сделки в формате UNIX (секунды) |
| `price` | float | Цена, по которой была совершена сделка |
| `volume` | integer | Объём сделки |
| `type` | string | Тип сделки: `buy` — покупка, `sell` — продажа |


## `trade/order_book`

**📤 Структура запроса:**  
(Параметров нет)

**💬 Ответ:**
```json
{
  "buy": [
    { "volume": integer, "price": float },
    { "volume": integer, "price": float }
  ],
  "sell": [
    { "volume": integer, "price": float },
    { "volume": integer, "price": float }
  ]
}
```

**📘 Описание полей:**

| Поле | Тип | Описание |
|------|-----|-----------|
| `buy` | array | Список заявок на покупку |
| `sell` | array | Список заявок на продажу |
| `volume` | integer | Объём ордера |
| `price` | float | Цена ордера |

---

# ⚙️ Остальные методы

---

## `/iris_agents`

**📤 Структура запроса:**

| Параметр | Тип   | Описание                                                                                    |
| --------  | ----- | ------------------------------------------------------------------------------------------- |
| `token`   | string | Конкатенация `{bot_id}_{iris_token}`. Пример: `5293075118_SEibvWeRC19iRDk6SAwvu7TfzyOe4m6o` |

**💬 Ответ:**

```json
[ integer, integer, ... ]
```

**📘 Описание:**

Возвращает массив int64 — идентификаторов Telegram-аккаунтов агентов Iris.

Пример:
```json
[571497337, 6826112951, 7057861690, 1072639353, 6530053533, 956560198, 1135399536, 5484288853, 1082239406, 661079614]
```

## `/last_version`
**📤 Структура запроса:**  
(Параметров нет)

**💬 Ответ:**
```json
{
  "result": "0.3"
}
```

**📘 Описание:**
Возвращает строку с текущей актуальной версией API Iris.
Используется для проверки обновлений и совместимости клиентов.
---

# ⚠️ Ошибки API

При выполнении запросов сервер может возвращать ошибки в следующем формате:

```json
{
  "error": {
    "description": "Error description",
    "code": integer
  }
}
```
---
**📘 Возможные ошибки:**

| Код | Сообщение | Описание |
|:----|:-----------|:----------|
| `400` | `Sweets/Gold is 0` | Передано нулевое количество валюты |
| `400` | `User is not set` | Не указан пользователь в запросе |
| `404` | `User not found` | Пользователь не найден |
| `403` | `Account is not user` | Указан неверный тип аккаунта |
| `500` | `Ошибка в расчёте сжигании ирисок. Обратитесь к агентам` | Внутренняя ошибка сервера при расчёте |
| `409` | `Not enough sweets/gold. Need $value` | Недостаточно валюты на счету |
| `409` | `Unsuccessful donate score decrease` | Ошибка при уменьшении донат-очков |
| `409` | `Unsuccessful sweets/gold decrease` | Ошибка при уменьшении валюты |

