# Сценарии использования

Упрощенные сценарии использования API

## Заказ с ценой заказчика

1. Заказчик публикует заказ [`order.publish`](Customer.md#orderpublish)
2. Исполнитель создает предложение [`offer.create`](Performer.md#offercreate)
3. Заказчик принимает предложение [`offer.accept`](Customer.md#offeraccept) из списка [`offer.getList`](Customer.md#offergetlist)
4. Исполнитель отправляет работу [`order.finishWork`](Performer.md#orderfinishwork)
5. Заказчик получает работу [`document.getList`](Customer.md#documentgetlist)
6. Заказчик завершает заказ [`order.finish`](Customer.md#orderfinish)

## Заказ с ценой исполнителя

1. Заказчик публикует заказ [`order.publish`](Customer.md#orderpublish)
2. Исполнитель создает предложение [`offer.create`](Performer.md#offercreate)
3. Заказчик принимает предложение [`offer.accept`](Customer.md#offeraccept) из списка [`offer.getList`](Customer.md#offergetlist)
4. Исполнитель отправляет работу [`order.finishWork`](Performer.md#orderfinishwork)
5. Заказчик получает работу [`document.getList`](Customer.md#documentgetlist)
6. Заказчик завершает заказ [`order.finish`](Customer.md#orderfinish)

## Персональный заказ

1. Заказчик публикует заказ [`order.publish`](Customer.md#orderpublish) с выбранным исполнителем, при этом создается персональное предложение
2. Исполнитель принимает предложение [`offer.accept`](Performer.md#offeraccept) из списка [`offer.getList`](Performer.md#offergetlist)
3. Исполнитель отправляет работу [`order.finishWork`](Performer.md#orderfinishwork)
4. Заказчик получает работу [`document.getList`](Customer.md#documentgetlist)
5. Заказчик завершает заказ [`order.finish`](Customer.md#orderfinish)

## Заказ с автопринятием предложения по таймеру

1. Заказчик публикует заказ [`order.publish`](Customer.md#orderpublish) с установленным параметром [`performerRequirements.acceptOfferAt`](Entities.md#Структура-performerrequirements)
2. Исполнитель создает предложение [`offer.create`](Performer.md#offercreate)
3. По истечению времени ожидания система принимает в работу релевантное предложение
4. Исполнитель отправляет работу [`order.finishWork`](Performer.md#orderfinishwork)
5. Заказчик получает работу [`document.getList`](Customer.md#documentgetlist)
6. Заказчик завершает заказ [`order.finish`](Customer.md#orderfinish)

## Заказ с автопринятием первого предложения

1. Заказчик публикует заказ [`order.publish`](Customer.md#orderpublish)
2. Исполнитель создает предложение [`offer.create`](Performer.md#offercreate), одновременно с этим предложение принимается в работу
3. По истечению времени ожидания система принимает в работу релевантное предложение
4. Исполнитель отправляет работу [`order.finishWork`](Performer.md#orderfinishwork)
5. Заказчик получает работу [`document.getList`](Customer.md#documentgetlist)
6. Заказчик завершает заказ [`order.finish`](Customer.md#orderfinish)

