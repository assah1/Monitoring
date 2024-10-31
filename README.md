# Задание №3 Мониторинг доступности ptsecurity.com
## Ссылка на публичный Git-репозиторий, содержащий файлы конфигурации Prometheus и Blackbox exporter с настройками сбора метрик доступности https:<span></span>//ptsecurity.com

## Описание
Эта документ описывает настройки конфигураций для мониторинга доступности сайта с помощью Prometheus и Blackbox Exporter.

### Основной источник
Конфигурации основаны на официальной документации Prometheus и Blackbox Exporter:
- [Prometheus Blackbox Exporter Configuration](https://github.com/prometheus/blackbox_exporter/blob/master/CONFIGURATION.md)

## Конфигурация Prometheus

Prometheus настроен на сбор метрик каждые 15 секунд и использует Blackbox Exporter для проверки доступности через различные протоколы. Конфигурация содержит несколько задач для каждой проверки:

1. **HTTP Blackbox**
   - Проверяет доступность веб-страниц через HTTP.
   - Модуль: `check_http`

2. **TCP Blackbox**
   - Выполняет TCP-проверку для заданного домена на порту 443.
   - Модуль: `check_tcp`

3. **DNS Blackbox**
   - Выполняет DNS-запрос к домену.
   - Модуль: `check_dns`

4. **ICMP Blackbox**
   - Выполняет ICMP-запрос (ping) к домену.
   - Модуль: `check_icmp`

## Конфигурация Blackbox Exporter

Blackbox Exporter настроен на выполнение различных типов проверок, которые используются Prometheus:

- **check_http**: Проверка HTTP с поддержкой перенаправлений и указанием валидных кодов ответа.
- **check_tcp**: TCP-проверка с ожиданием простого ответа от сервера.
- **check_dns**: Запрос DNS с типом запроса A и проверкой на успешное разрешение имени.
- **check_icmp**: ICMP-проверка с использованием заданного размера пакета и TTL.

--- 

