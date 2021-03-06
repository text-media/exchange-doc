# Сущности

 * [Order](#order)
 * [Offer](#offer)
 * [Document](#document)
 * [Folder](#folder)
 * [Comment](#comment)
 * [Claim](#claim)

## Order

Заказ

| Поле | Назначение | Тип значения |
| ---- | ---------- | ------------ |
| exchangeType | Тип биржи | `int`, [константное значение](#Константы-exchangetype) |
| title | Заголовок | `string` |
| description | Описание задачи | `string` |
| type | Тип заказа | `int`, [константное значение](#Константы-type) |
| price | Цена | `string` |
| deadline | Дедлайн | `ISO 8601` |
| customerId | ID заказчика | `int` |
| performerId | ID исполнителя | `int` |
| folderId | ID папки | `int`, `null` |
| languageId | Язык ТЗ | `int` |
| state | Текущее состояние заказа | `int`, [константное значение](#Константы-state) |
| performerRequirements | Требования к исполнителю | Структура |
| workRequirements | Требования к работе | Структура |
| languageRequirements | Требования к языку | Структура |

### Константы `exchangeType`

| Значение | Описание |
| -------- | -------- |
| 1 | Биржа копирайтинга |
| 2 | Биржа рерайтинга |

### Константы `type`

| Значение | Описание |
| -------- | -------- |
| 1 | Цена заказчика |
| 2 | Цена исполнителя |
| 3 | Персональный заказ |
| 4 | Автоматическое принятие релевантного отклика по таймеру |
| 5 | Автоматическое принятия первого отклика |

### Константы `state`

| Значение | Описание |
| -------- | -------- |
| 1 | Опубликован |
| 2 | Выбран исполнитель |
| 3 | Черновик |
| 4 | Шаблон |
| 5 | В работе |
| 6 | Предпросмотор работы |
| 7 | Исполнитель завершил работу |
| 8 | На доработке |
| 9 | Заказ завершен |
| 10 | Арбитраж |
| 12 | Архив |

### Структура `performerRequirements`

Требования к исполнителю

| Поле | Назначение | Тип значения |
| ---- | ---------- | ------------ |
| minimalRank | Минимальный ранг исполнителя | `int` |
| maximumOrders | Ограничение на количество заказов одному исполнителю | `int` |
| inWhitelist | Исполнитель из белого списка | `bool` |
| acceptOfferAt | Время автопринятия отклика | `ISO 8601` |

### Структура `workRequirements`

Требования к работе

| Поле | Назначение | Тип значения |
| ---- | ---------- | ------------ |
| sizeType | Способо подсчета размера работы | `int`, [константное значение](#Константы-workrequirementssizetype) |
| minimalSize | Минимальный размер работы | `int` |

### Структура `languageRequirements`

Требования к языку работы и владение языком исполнителем

| Поле | Назначение | Тип значения |
| ---- | ---------- | ------------ |
| languageId | Язык работы | `int` |
| skillLevel | Владения языком исполнителем | `int` |

### Константы `WorkRequirements.sizeType`

| Значение | Описание |
| -------- | -------- |
| 0 | Контроль размера отключен |
| 1 | Символы с пробелами |
| 2 | Символы без пробелов |
| 3 | Число слов |

## Offer

Предложение (так же используется термин *отклик*)

| Поле | Назначение | Тип значения |
| ---- | ---------- | -------------|
| orderId | ID заказа | `int` |
| performerId | ID исполнителя | `int` |
| message | Сообщение | `string` |
| expirationAt | Время истечения отклика | `ISO 8601` |
| offeredPrice | Предложенная цена | `string` |
| offeredDeadline | Предложенный дедлайн | `ISO 8601` |

## Document

Документ (единица работы)

| Поле | Назначение | Тип значения |
| ---- | ---------- | ------------ |
| orderId | ID заказа | `int` |
| title | Название | `string` |
| text | Текст   | `string` |

## Folder

Папка

| Поле | Назначение | Тип значения |
| ---- | ---------- | ------------ |
| customerId | ID заказчика | `int` |
| exchangeType | Тип биржи | `int`, [константное значение](#Константы-exchangetype) |
| name | Имя папки | `string` |

## Comment

Комментарий

| Поле | Назначение | Тип значения |
| ---- | ---------- | ------------ |
| orderId | ID заказа | `int` |
| actorId | ID актора (текущий заказчик или исполнитель) | `int` |
| message | Сообщение | `string` |

## Claim

Жалоба

| Поле | Назначение | Тип значения |
| ---- | ---------- | ------------ |
| orderId | ID заказа | `int` |
| message | Сообщение | `string` |
| ownerType | Владелец | `int` |
| applicantId | ID истца | `int` |
| respondentId | ID ответчика | `int` |
