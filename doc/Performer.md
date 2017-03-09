# Performer API

Управление офферами, комментариями, жалобами и работами от лица исполнителя.

Все запросы используют спецификацию [JSON-RPC 2.0](http://www.jsonrpc.org/specification).

URL для запросов: `/api/performer`.

## Оглавление

* [Offer](#offer)
  - [accept](#offeraccept)
  - [decline](#offerdecline)
  - [create](#offercreate)
  - [refuse](#offerrefuse)
  - [revoke](#offerrevoke)
  - [getList](#offergetlist)
  - [getMeta](#offergetmeta)
* [Comment](#comment)
  - [create](#commentcreate)
  - [delete](#commentdelete)
  - [getList](#commentgetlist)
  - [getMeta](#commentgetmeta)
* [Claim](#claim)
  - [create](#claimcreate)
  - [revoke](#claimrevoke)
  - [createComment](#claimcreatecomment)
  - [getList](#claimgetlist)
  - [getOne](#claimgetone)
  - [getComments](#claimgetcomments)
  - [getMeta](#claimgetmeta)
* [Document](#document)
  - [getList](#documentgetlist)
  - [getOne](#documentgetone)
  - [getVersions](#documentgetversions)
  - [create](#documentcreate)
  - [edit](#documentedit)
  - [delete](#documentdelete)
  - [priorityUp](#documentpriorityup)
  - [priorityDown](#documentprioritydown)
  - [preview](#documentpreview)
  - [getMeta](#documentgetmeta)
* [Rating](#rating)
  - [addPositive](#ratingaddpositive)
  - [addNegative](#ratingaddnegative)
  - [revoke](#ratingrevoke)
* [Order](#order)
  - [getList](#ordergetlist)
  - [getOne](#ordergetone)
  - [finishWork](#orderfinishwork)
  - [getMeta](#ordergetmeta)
  - [getRevisions](#ordergetrevisions)

## Offer

### offer.accept

Принятие персонального оффера от заказчика

```json
{
    "jsonrpc":"2.0",
    "method":"offer.accept",
    "params": {
        "offerId":2
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| offerId  | +            |

### offer.decline

Отклонение оффера

```json
{
    "jsonrpc":"2.0",
    "method":"offer.decline",
    "params": {
        "offerId":5
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| offerId  | +            |

### offer.create

Создание оффера

```json
{
    "jsonrpc":"2.0",
    "method":"offer.create",
    "params": {
        "orderId":1689433326,
        "performerId":55,
        "message":"ZX",
        "expirationAt":"2016-07-25T10:26:17+0300",
        "offeredPrice":"10.50",
        "offeredDeadline":"2016-07-25T11:00:00+0300"
    },
    "id":1
}
```

| Название        | Обязательный |
| --------------- | :----------: |
| orderId         | +            |
| performerId     | +            |
| message         | +            |
| expirationAt    | +            |
| offeredPrice    | -            |
| offeredDeadline | -            |

### offer.refuse

Прерывание выполнения оффера

```json
{
    "jsonrpc":"2.0",
    "method":"offer.refuse",
    "params": {
        "offerId":8,
        "message":"Nothing"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| offerId  | +            |
| message  | +            |

### offer.revoke

Отзыв оффера

```json
{
    "jsonrpc":"2.0",
    "method":"offer.revoke",
    "params": {
        "offerId":8
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| offerId  | +            |

### offer.getList

Получение списка предложений

```json
{
    "jsonrpc":"2.0",
    "method":"offer.getList",
    "params": {
        "performerId":77,
        "ownerType":1,
        "exchangeType":1,
        "state":[1],
        "orderId":1689433326,
        "sort": {
            "name":"Offer.id",
            "dir":"DESC"
        },
        "limit":10,
        "offset":0
    },
    "id":1
}
```

| Название     | Обязательный |
| ------------ | :----------: |
| performerId  | +            |
| ownerType    | -            |
| exchangeType | -            |
| state        | -            |
| orderId      | -            |
| sort         | +            |
| limit        | +            |
| offset       | +            |

Параметры для **sort**:

| Название | Обязательный |
| -------- | :----------: |
| name     | +            |
| dir      | +            |

Доступные значения для **sort.name**:

* Offer.id
* Offer.performerId
* Offer.state
* Offer.offeredPrice
* Offer.offeredDeadline
* Offer.modifiedAt
* Order.id
* Order.title
* Order.deadline
* Order.modifiedAt

### offer.getMeta

Получение информации по доступным методам и допустимым состояниям заказа для их вызова

```json
{
    "jsonrpc":"2.0",
    "method":"offer.getMeta",
    "id":1
}
```

## Comment

### comment.create

Добавление комментария

```json
{
    "jsonrpc":"2.0",
    "method":"comment.create",
    "params": {
        "orderId":1038723239,
        "actorId":55,
        "message":"Что тут происходит?"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| actorId  | +            |
| message  | +            |

### comment.delete

Удаление комментария

```json
{
    "jsonrpc":"2.0",
    "method":"comment.delete",
    "params": {
        "commentId":1
    },
    "id":1
}
```

| Название  | Обязательный |
| --------- | :----------: |
| commentId | +            |

### comment.getList

Получение списка комментариев

```json
{
    "jsonrpc":"2.0",
    "method":"comment.getList",
    "params": {
        "orderId":1048527118,
        "limit":10,
        "offset":0
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| limit    | +            |
| offset   | +            |

### comment.getMeta

Получение информации по доступным методам и допустимым состояниям заказа для их вызова

```json
{
    "jsonrpc":"2.0",
    "method":"comment.getMeta",
    "id":1
}
```

## Claim

### claim.create

Создание жалобы

```json
{
    "jsonrpc":"2.0",
    "method":"claim.create",
    "params": {
        "orderId":1686885030,
        "message":"Работа не устраивает"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| message  | +            |

### claim.revoke

Отзыв жалобы

```json
{
    "jsonrpc":"2.0",
    "method":"claim.revoke",
    "params": {
        "claimId":2
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| claimId  | +            |

### claim.createComment

Комментирование жалобы

```json
{
    "jsonrpc":"2.0",
    "method":"claim.createComment",
    "params": {
        "claimId":4,
        "message":"Что может быть хуже?"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| claimId  | +            |
| message  | +            |

### claim.getList

Получение списка жалоб

```json
{
    "jsonrpc":"2.0",
    "method":"claim.getList",
    "params": {
        "performerId":55,
        "state":0,
        "side":1,
        "sort": {
            "name":"Claim.createdAt",
            "dir":"ASC"
        },
        "limit":10,
        "offset":0,
        "orderId":1048527118
    },
    "id":1
}
```

| Название    | Обязательный |
| ----------- | :----------: |
| performerId | +            |
| state       | +            |
| side        | +            |
| sort        | +            |
| limit       | +            |
| offset      | +            |
| orderId     | -            |

Доступные значения для **side**:

* 1 (Claim.externalApplicantId = current user)
* 2 (Claim.externalRespondentId = current user)

Параметры для **sort**:

| Название | Обязательный |
| -------- | :----------: |
| name     | +            |
| dir      | +            |

Доступные значения для **sort.name**:

* Claim.createdAt 
* Claim.finishedAt

### claim.getOne

Получение жалобы

```json
{
    "jsonrpc":"2.0",
    "method":"claim.getOne",
    "params": {
        "claimId":4
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| claimId  | +            |

### claim.getComments

Получение комментариев жалобы

```json
{
    "jsonrpc":"2.0",
    "method":"claim.getComments",
    "params": {
        "claimId":4,
        "limit":10,
        "offset":0
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| claimId  | +            |
| limit    | +            |
| offset   | +            |

### claim.getMeta

Получение информации по доступным методам и допустимым состояниям заказа для их вызова

```json
{
    "jsonrpc":"2.0",
    "method":"claim.getMeta",
    "id":1
}
```

## Document

### document.getList

Получение списка документов

```json
{
    "jsonrpc":"2.0",
    "method":"document.getList",
    "params": {
        "orderId":1711505024,
        "limit":10,
        "offset":0
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| limit    | -            |
| offset   | -            |

### document.getOne

Получение документа с версиями

```json
{
    "jsonrpc":"2.0",
    "method":"document.getOne",
    "params": {
        "orderId":1711505024,
        "number":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| number   | +            |

### document.getVersions

Получение версий документа

```json
{
    "jsonrpc":"2.0",
    "method":"document.getVersions",
    "params": {
        "orderId":1711505024,
        "number":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| number   | +            |

### document.create

Создание документа

```json
{
    "jsonrpc":"2.0",
    "method":"document.create",
    "params": {
        "orderId":1711505024,
        "title":"ZX",
        "text":"ASDF"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| title    | +            |
| text     | +            |

### document.edit

Редактирование документа

```json
{
    "jsonrpc":"2.0",
    "method":"document.edit",
    "params": {
        "orderId":1711505024,
        "number":1,
        "title":"ZX",
        "text":"ASDF"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| number   | +            |
| title    | +            |
| text     | +            |

### document.delete

Удаление документа

```json
{
    "jsonrpc":"2.0",
    "method":"document.delete",
    "params": {
        "orderId":1711505024,
        "documentId":123
    },
    "id":1
}
```

| Название   | Обязательный |
| ---------- | :----------: |
| orderId    | +            |
| documentId | +            |

### document.priorityUp

Повышение приоритета

```json
{
    "jsonrpc":"2.0",
    "method":"document.priorityUp",
    "params": {
        "orderId":1711505024,
        "number":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| number   | +            |

### document.priorityDown

Понижение приоритета

```json
{
    "jsonrpc":"2.0",
    "method":"document.priorityDown",
    "params": {
        "orderId":1711505024,
        "number":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| number   | +            |

### document.preview

Разрешение предпросмотра работы

```json
{
    "jsonrpc":"2.0",
    "method":"document.preview",
    "params": {
        "orderId":1711505024,
        "documentId":257
    },
    "id":1
}
```

| Название   | Обязательный |
| ---------- | :----------: |
| orderId    | +            |
| documentId | +            |

### document.getMeta

Получение информации по доступным методам и допустимым состояниям заказа для их вызова

```json
{
    "jsonrpc":"2.0",
    "method":"document.getMeta",
    "id":1
}
```

## Rating

### rating.addPositive

Добавление единицы положительного рейтинга

```json
{
    "jsonrpc":"2.0",
    "method":"rating.addPositive",
    "params": {
        "orderId":1181775755,
        "performerId":1
    },
    "id":1
}
```

| Название    | Обязательный |
| ----------- | :----------: |
| orderId     | +            |
| performerId | +            |

### rating.addNegative

Добавление единицы отрицательного рейтинга

```json
{
    "jsonrpc":"2.0",
    "method":"rating.addNegative",
    "params": {
        "orderId":602902821,
        "performerId":1
    },
    "id":1
}
```

| Название    | Обязательный |
| ----------- | :----------: |
| orderId     | +            |
| performerId | +            |

### rating.revoke

Отзыв голоса

```json
{
    "jsonrpc":"2.0",
    "method":"rating.revoke",
    "params": {
        "orderId":1309900369,
        "performerId":1
    },
    "id":1
}
```

| Название    | Обязательный |
| ----------- | :----------: |
| orderId     | +            |
| performerId | +            |

## Order

### order.getList

Получение списка заказов

```json
{
    "jsonrpc":"2.0",
    "method":"order.getList",
    "params": {
        "participant":true,
        "performerId":77,
        "exchangeType":1,
        "sort": {
            "name":"Order.createdAt",
            "dir":"DESC"
        },
        "createdAt": {
            "from":"2016-07-25T09:00:00+0300",
            "till":"2016-07-29T12:00:00+0300"
        },
        "price": {
            "from":"0",
            "till":"100"
        },
        "limit":10,
        "offset":0,
        "fromWhitelist":false,
        "enableBlacklist":false
    },
    "id":1
}
```

| Название        | Обязательный |
| --------------- | :----------: |
| participant     | +            |
| performerId     | +            |
| exchangeType    | +            |
| sort            | +            |
| createdAt       | -            |
| price           | -            |
| limit           | -            |
| offset          | -            |
| fromWhitelist   | -            |
| enableBlacklist | -            |

Параметры для **sort**:

| Название | Обязательный |
| -------- | :----------: |
| name     | +            |
| dir      | +            |

Параметры для **createdAt**:

| Название | Обязательный |
| -------- | :----------: |
| from     | +            |
| till     | +            |

Параметры для **price**:

| Название | Обязательный |
| -------- | :----------: |
| from     | +            |
| till     | +            |

Доступные значения для **sort.name**:

* Order.createdAt
* Order.deadline
* Order.externalCustomerId
* Order.id
* Order.price
* Order.price.charsTotal
* Order.price.charsClean
* Order.price.wordsTotal
* Order.rating
* Order.relevance
* Order.state
* Order.title

### order.getOne

Получение заказа

```json
{
    "jsonrpc":"2.0",
    "method":"order.getOne",
    "params": {
        "orderId":1307207252
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |


### order.finishWork

Завершение работы

```json
{
    "jsonrpc":"2.0",
    "method":"order.finishWork",
    "params": {
        "orderId":1609525066
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

### order.getMeta

Получение информации по доступным методам и допустимым состояниям заказа для их вызова

```json
{
    "jsonrpc":"2.0",
    "method":"order.getMeta",
    "id":1
}
```

### order.getRevisions

```json
{
    "jsonrpc":"2.0",
    "method":"order.getRevisions",
    "params": {
        "orderId":1307207252,
        "performerId":55,
        "limit":10,
        "offset":0
    },
    "id":1
}
```

| Название    | Обязательный |
| ----------- | :----------: |
| orderId     | +            |
| performerId | +            |
| limit       | +            |
| offset      | +            |
