# OrderBookScreener
Торгово-аналитический терминал на основа Finam Trade API

Программа разработана для участия в хакатоне.

Скринер стакана - позволяет подписываться на большое количество стаканов и искать среди них большие заявки.
При этом программа не требовательна к ресурсам компьютера.

<img src="https://github.com/VozyakovAV/OrderBookScreener/blob/main/ReadmeResources/main.png" />

## Возможности
- Подписка на стаканы по акциям, фьючерсам, валютам
- Поиск больших заявок среди всех подписанных стаканов
- Расчет спреда всех стаканов
- Фильтр по названию инструмента и по типу инструмента
- Просмотр портфеля: деньги, позиции, заявки
- Выставление и снятие заявки
- Бонус1: Получение дополнительной информации по инструменту из API мосбиржи (оборот за день в деньгах и контрактах)

## Требования
- Операционная система Windows
- Фреймворк .Net 6

## Технические особенности
- Программа разработана на фреймворке .Net6, код на C#, визуальная часть на WPF
- Класс FinamClient реализует взаимодействие с Finam Api по протоколу gRPC
- Взаимодействие с клиентом (FinamClient) реализовано через интерфейс IConnector, что позволяет в дальнейшем легко подключить другой поставщик данных, например криптобиржу
- При запуске программы идет подписка на все российские акции (TQBR), фьючерсы (FUT) и валюты (CETS). Данные поступают в очередь и обрабатываются без задержки в отдельном потоке, что не нагружает систему

## Запуск
### Скачать готовый релиз
- Скачать последнией релиз https://github.com/VozyakovAV/OrderBookScreener/releases
- Распаковать zip файл
- Запустить OrderBookScreener.exe

Программа запустится с настройками по умолчанию, доступен только просмотр инструментов и заявок.

Чтобы указать свой токен смотрите настройку файла config.txt

### Запуск из Visual Studio
- Скачать проект
- Открыть OrderBookScreener.sln
- Запустить проект (F5)

## Настройка файла config.txt
В файле config.txt указывается токен к Trade Api и клиентский код.

По указанным настройкам программа будет получать инструменты подписываться на стаканы.

Если токен имеет разрешение на работу с портфелем, то дополнительно в программе будет доступен просмотр баланса, позиций и заявок, a так же можно будет выставлять и снимать заявки

```json
{
  "Token": "<Токен от Trade API>",
  "ClientId": "<Торговый код клиента>"
}
```
