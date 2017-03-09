# Документация API биржи [text.ru](https://text.ru)

Перед началом работы вы должны получить пользовательский ключ доступа (далее `UserKey`) на [этой странице](http://text.ru/api-check).

API использует спецификацию [JSON-RPC 2.0](http://www.jsonrpc.org/specification) и имеет две точки доступа:
- для заказчика - `https://exchange.text.ru/api/customer`;
- для исполнителя - `https://exchange.text.ru/api/performer`.

Именование методов соответствует шаблону: `имяСущности.имяМетода`.

- [Информация по сущностям](doc/Entities.md)
- [Информация по методам](doc/Base.md)
- [Сценарии использования](doc/Usecases.md)