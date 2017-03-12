# Customer API

Управление заказами, офферами, папками, комментариями и жалобами от лица заказчика.

Все запросы используют спецификацию [JSON-RPC 2.0](http://www.jsonrpc.org/specification).

URL для запросов: `/api/customer`.

## Оглавление

* [Order](#order)
  - [publish](#orderpublish)
  - [saveAsDraft](#ordersaveasdraft)
  - [saveAsTemplate](#ordersaveastemplate)
  - [edit](#orderedit)
  - [packing](#orderpacking)
  - [unpacking](#orderunpacking)
  - [finish](#orderfinish)
  - [demandRevision](#orderdemandrevision)
  - [delete](#orderdelete)
  - [deferDeadline](#orderdeferdeadline)
  - [getList](#ordergetlist)
  - [getOne](#ordergetone)
  - [getHistory](#ordergethistory)
  - [getMeta](#ordergetmeta)
* [Offer](#offer)
  - [accept](#offeraccept)
  - [refuse](#offerrefuse)
  - [decline](#offerdecline)
  - [getMeta](#offergetmeta)
  - [getList](#offergetlist)
* [Folder](#folder)
  - [create](#foldercreate)
  - [rename](#folderrename)
  - [move](#foldermove)
  - [priorityUp](#folderpriorityup)
  - [priorityDown](#folderprioritydown)
  - [delete](#folderdelete)
  - [getList](#foldergetlist)
* [Comment](#comment)
  - [create](#commentcreate)
  - [delete](#commentdelete)
  - [enable](#commentenable)
  - [disable](#commentdisable)
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
  - [downloadAll](#documentdownloadall)
  - [download](#documentdownload)

## Order

[Описание сущности Order](Entities.md#order)

### order.publish

Публикация заказа

#### Существующий заказ

```json
{
    "jsonrpc":"2.0",
    "method":"order.publish",
    "params": {
        "orderId":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

#### Новый заказ

```json
{
    "jsonrpc":"2.0",
    "method":"order.publish",
    "params": {
        "exchangeType":1,
        "title":"ASDFG",
        "description":"ZXZXZXZXZX",
        "type":1,
        "price":"12.00",
        "deadline":"2016-07-25T09:03:13+0300",
        "customerId":55,
        "performerId":66,
        "folderId":77,
        "performer": {
            "minimalRank":1,
            "maximumOrders":1,
            "inWhitelist":true,
            "acceptOfferAt":"2016-07-25T12:00:00+0300"
        },
        "work": {
            "minimalSize":1,
            "sizeType":1
        }
    },
    "id":1
}
```

| Название     | Обязательный |
| ------------ | :----------: |
| exchangeType | +            |
| title        | +            |
| description  | +            |
| type         | +            |
| price        | +            |
| deadline     | +            |
| customerId   | +            |
| performerId  | -            |
| folderId     | -            |
| performer    | +            |
| work         | +            |

Параметры для **performer**:

| Название      | Обязательный |
| ------------- | :----------: |
| minimalRank   | +            |
| maximumOrders | +            |
| inWhitelist   | +            |
| acceptOfferAt | -            |

Параметры для **work**:

| Название    | Обязательный |
| ----------- | :----------: |
| minimalSize | +            |
| sizeType    | +            |

### order.saveAsDraft

Сохранение заказа как черновика

#### Существующий заказ

```json
{
    "jsonrpc":"2.0",
    "method":"order.saveAsDraft",
    "params": {
        "orderId":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

#### Новый заказ

```json
{
    "jsonrpc":"2.0",
    "method":"order.saveAsDraft",
    "params": {
        "exchangeType":1,
        "title":"ASDFG",
        "description":"ZXZXZXZXZX",
        "type":1,
        "price":"12.00",
        "deadline":"2016-07-25T09:03:13+0300",
        "customerId":55,
        "performerId":66,
        "folderId":77,
        "performer": {
            "minimalRank":1,
            "maximumOrders":1,
            "inWhitelist":true,
            "acceptOfferAt":"2016-07-25T12:00:00+0300"
        },
        "work": {
            "minimalSize":1,
            "sizeType":1
        }
    },
    "id":1
}
```

| Название     | Обязательный |
| ------------ | :----------: |
| exchangeType | +            |
| title        | +            |
| description  | +            |
| type         | +            |
| price        | +            |
| deadline     | +            |
| customerId   | +            |
| performerId  | -            |
| folderId     | -            |
| performer    | +            |
| work         | +            |

Параметры для **performer**:

| Название      | Обязательный |
| ------------- | :----------: |
| minimalRank   | +            |
| maximumOrders | +            |
| inWhitelist   | +            |
| acceptOfferAt | -            |

Параметры для **work**:

| Название    | Обязательный |
| ----------- | :----------: |
| minimalSize | +            |
| sizeType    | +            |

### order.saveAsTemplate

Сохранение заказа как шаблона

#### Существующий заказ

```json
{
    "jsonrpc":"2.0",
    "method":"order.saveAsTemplate",
    "params": {
        "orderId":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

#### Новый заказ

```json
{
    "jsonrpc":"2.0",
    "method":"order.saveAsTemplate",
    "params": {
        "exchangeType":1,
        "title":"ASDFG",
        "description":"ZXZXZXZXZX",
        "type":1,
        "price":"12.00",
        "deadline":"2016-07-25T09:03:13+0300",
        "customerId":55,
        "performerId":66,
        "folderId":77,
        "performer": {
            "minimalRank":1,
            "maximumOrders":1,
            "inWhitelist":true,
            "acceptOfferAt":"2016-07-25T12:00:00+0300"
        },
        "work": {
            "minimalSize":1,
            "sizeType":1
        }
    },
    "id":1
}
```

| Название     | Обязательный |
| ------------ | :----------: |
| exchangeType | +            |
| title        | +            |
| description  | +            |
| type         | +            |
| price        | +            |
| deadline     | +            |
| customerId   | +            |
| performerId  | -            |
| folderId     | -            |
| performer    | +            |
| work         | +            |

Параметры для **performer**:

| Название      | Обязательный |
| ------------- | :----------: |
| minimalRank   | +            |
| maximumOrders | +            |
| inWhitelist   | +            |
| acceptOfferAt | -            |

Параметры для **work**:

| Название    | Обязательный |
| ----------- | :----------: |
| minimalSize | +            |
| sizeType    | +            |

### order.edit

Редактирование заказа

```json
{
    "jsonrpc":"2.0",
    "method":"order.edit",
    "params": {
        "orderId":1,
        "title":"Какое-то название",
        "description":"Какое-то описание",
        "type":1,
        "price":"12.50",
        "deadline":"2016-05-05T12:00:00+0300",
        "performerId":2,
        "folderId":77,
        "performer": {
            "minimalRank":1,
            "maximumOrders":1,
            "inWhitelist":true,
            "acceptOfferAt":"2016-07-25T12:00:00+0300"
        },
        "work": {
            "minimalSize":1,
            "sizeType":1
        }
    },
    "id":1
}
```

| Название    | Обязательный |
| ----------- | :----------: |
| orderId     | +            |
| title       | -            |
| description | -            |
| type        | -            |
| price       | -            |
| deadline    | -            |
| performerId | -            |
| folderId    | -            |
| performer   | -            |
| work        | -            |

Параметры для **performer**:

| Название      | Обязательный |
| ------------- | :----------: |
| minimalRank   | -            |
| maximumOrders | -            |
| inWhitelist   | -            |
| acceptOfferAt | -            |

Параметры для **work**:

| Название    | Обязательный |
| ----------- | :----------: |
| minimalSize | -            |
| sizeType    | -            |

### order.packing

Упаковка заказа в архив

```json
{
    "jsonrpc":"2.0",
    "method":"order.packing",
    "params": {
        "orderId":1960756383
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

### order.unpacking

Распаковка заказа из архива

```json
{
    "jsonrpc":"2.0",
    "method":"order.unpacking",
    "params": {
        "orderId":1253777645
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

### order.finish

Завершение заказа

```json
{
    "jsonrpc":"2.0",
    "method":"order.finish",
    "params": {
        "orderId":1660330193
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

### order.demandRevision

Отправка заказа на доработку

```json
{
    "jsonrpc":"2.0",
    "method":"order.demandRevision",
    "params": {
        "orderId":540244221,
        "comment":"ZXZXZXZX",
        "deadline":"2016-07-25T09:03:13+0300"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| comment  | +            |
| deadline | -            |

### order.delete

Удаление заказа

```json
{
    "jsonrpc":"2.0",
    "method":"order.delete",
    "params": {
        "orderId":1307207252
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

### order.deferDeadline

Продление deadline

```json
{
    "jsonrpc":"2.0",
    "method":"order.deferDeadline",
    "params": {
        "orderId":1307207252,
        "deadline":"2016-07-25T09:03:13+0300"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| deadline | +            |

### order.getList

Получение списка заказов

```json
{
    "jsonrpc":"2.0",
    "method":"order.getList",
    "params": {
        "customerId":55,
        "sort": {
            "name":"Order.id",
            "dir":"ASC"
        },
        "exchangeType":1,
        "state":[1],
        "folderId":77,
        "performerId":66,
        "limit":10,
        "offset":0
    },
    "id":1
}
```

| Название     | Обязательный |
| ------------ | :----------: |
| customerId   | +            |
| sort         | +            |
| exchangeType | -            |
| state        | -            |
| folderId     | -            |
| performerId  | -            |
| limit        | -            |
| offset       | -            |

Параметры для **sort**:

| Название | Обязательный |
| -------- | :----------: |
| name     | +            |
| dir      | +            |

Доступные значения для **sort.name**:

* Order.id
* Order.title
* Order.deadline
* Order.price
* Order.state
* Order.createdAt

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

### order.getHistory

Получение истории заказа

```json
{
    "jsonrpc":"2.0",
    "method":"order.getHistory",
    "params": {
        "orderId":1307207252,
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

### order.getMeta

Получение информации по доступным методам и допустимым состояниям заказа для их вызова

```json
{
    "jsonrpc":"2.0",
    "method":"order.getMeta",
    "id":1
}
```

## Offer

[Описание сущности Offer](Entities.md#offer)

### offer.accept

Принятие оффера исполнителя

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

### offer.refuse

Отказ от оффера исполнителя

```json
{
    "jsonrpc":"2.0",
    "method":"offer.refuse",
    "params": {
        "offerId":5
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| offerId  | +            |

### offer.decline

Отклонение предложения

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

### offer.getMeta

Получение информации по доступным методам и допустимым состояниям заказа для их вызова

```json
{
    "jsonrpc":"2.0",
    "method":"offer.getMeta",
    "id":1
}
```

### offer.getList

Получение списка предложений

```json
{
    "jsonrpc":"2.0",
    "method":"offer.getList",
    "params": {
        "orderId":1689433326,
        "performerId":77,
        "relevance":true,
        "state":[1],
        "sort": {
            "name":"Order.createdAt",
            "dir":"DESC"
        },
        "limit":10,
        "offset":0
    },
    "id":1
}
```

| Название    | Обязательный |
| ----------- | :----------: |
| orderId     | +            |
| performerId | -            |
| relevance   | -            |
| state       | -            |
| sort        | +            |
| limit       | +            |
| offset      | +            |

Параметры для **sort**:

| Название | Обязательный |
| -------- | :----------: |
| name     | +            |
| dir      | +            |

Доступные значения для **sort.name**:

* Offer.offeredPrice
* Offer.offeredDeadline
* Offer.expirationAt
* Offer.createdAt
* Offer.relevance
* Order.createdAt
* User.rating

## Folder

[Описание сущности Folder](Entities.md#folder)

### folder.create

Создание папки

```json
{
    "jsonrpc":"2.0",
    "method":"folder.create",
    "params": {
        "customerId":55,
        "exchangeType":1,
        "name":"ZX"
    },
    "id":1
}
```

| Название     | Обязательный |
| ------------ | :----------: |
| customerId   | +            |
| exchangeType | +            |
| name         | +            |

### folder.rename

Переименование папки

```json
{
    "jsonrpc":"2.0",
    "method":"folder.rename",
    "params": {
        "folderId":1,
        "name":"ZXZXZXZXZX"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| folderId | +            |
| name     | +            |

### folder.move

Перемещение заказа в другую папку

```json
{
    "jsonrpc":"2.0",
    "method":"folder.move",
    "params": {
        "orderId":1689433326,
        "folderId":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| folderId | +            |

### folder.priorityUp

Поднятие приоритета папки

```json
{
    "jsonrpc":"2.0",
    "method":"folder.priorityUp",
    "params": {
        "folderId":4
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| folderId | +            |

### folder.priorityDown

Понижение приоритета папки

```json
{
    "jsonrpc":"2.0",
    "method":"folder.priorityDown",
    "params": {
        "folderId":7
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| folderId | +            |

### folder.delete

Удаление папки

```json
{
    "jsonrpc":"2.0",
    "method":"folder.delete",
    "params": {
        "folderId":7
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| folderId | +            |

### folder.getList

Получение списка папок

```json
{
    "jsonrpc":"2.0",
    "method":"folder.getList",
    "params": {
        "customerId":55,
        "exchangeType":1
    },
    "id":1
}
```

| Название     | Обязательный |
| ------------ | :----------: |
| customerId   | +            |
| exchangeType | -            |

## Comment

[Описание сущности Comment](Entities.md#comment)

### comment.create

Добавление комментария

```json
{
    "jsonrpc":"2.0",
    "method":"comment.create",
    "params": {
        "orderId":1512310066,
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

### comment.enable

Разрешение комментариев

```json
{
    "jsonrpc":"2.0",
    "method":"comment.enable",
    "params": {
        "orderId":1307207252
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

### comment.disable

Запрет комментариев

```json
{
    "jsonrpc":"2.0",
    "method":"comment.disable",
    "params": {
        "orderId":1307207252
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |

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

[Описание сущности Claim](Entities.md#claim)

### claim.create

Создание жалобы

```json
{
    "jsonrpc":"2.0",
    "method":"claim.create",
    "params": {
        "orderId":1048527118,
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
        "customerId":55,
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

| Название   | Обязательный |
| ---------- | :----------: |
| customerId | +            |
| state      | +            |
| side       | +            |
| sort       | +            |
| limit      | +            |
| offset     | +            |
| orderId    | -            |

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

[Описание сущности Document](Entities.md#document)

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

### document.downloadAll

```json
{
    "jsonrpc":"2.0",
    "method":"document.downloadAll",
    "params": {
        "orderId":[1711505024],
        "format":"txt"
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| format   | +            |

### document.download

```json
{
    "jsonrpc":"2.0",
    "method":"document.download",
    "params": {
        "orderId":1711505024,
        "format":"txt",
        "number":1
    },
    "id":1
}
```

| Название | Обязательный |
| -------- | :----------: |
| orderId  | +            |
| format   | +            |
| number   | -            |
