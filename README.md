# Реализация API Яндекс.Диска для 1Script

Библиотека предоставляет возможность взаимодействия с [REST API Яндекс.Диска](https://tech.yandex.ru/disk/rest/) на языке [1Script](http://oscript.io).

Реализована поддержка всех методов REST API Яндекс.Диска за исключением [метода установки дополнительных (custom) свойств](https://tech.yandex.ru/disk/api/reference/meta-add-docpage/) ресурсов (папок или файлов).

## Установка

Для работы библиотеки необходимо **oscript-yadisk** предварительно установить [Стандартную библиотеку скриптов](http://oscript.io/library) 1Script.

### Из исходников

1. Клонируйте репозиторий библиотеки:

    ```
    git clone https://github.com/kuntashov/oscript-yadisk.git
    ```

2. Добавьте в конфигурационном файле 1Script `oscript.cfg` в список дополнительных библиотек путь к каталогу, в который вы клонировали репозиторий:

    ```
    lib.additional = C:\libs\oscript-yadisk;
    ```

### Из пакетов opm

В настоящий момент не поддерживается.

## Использование

Библиотека к вашему скрипту подключается с помощью директивы `#Использовать yadisk`.

    ЯндексДиск = Новый ЯндексДиск;
    ЯндексДиск.УстановитьТокенАвторизации(OAuth_Токен);

Примеры использования вызовов всех реализованных методов можно увидеть в коде автоматических тестов, которые поставляются вместе с библиотекой в каталоге `tests`.

**Примечание.** В linux для корректной работы HTTPS-соединения может потребоваться выполнить команду 

    mozroots --import --sync

## Запуск тестов библиотеки

Для запуска автоматических тестов библиотеки необходимо тестам передать [OAuth-токен авторизации](https://tech.yandex.ru/oauth/).

Токен авторизации в тесты может быть передан либо через переменную окружения `YADISK_OAUTH_TOKEN`, либо через файл `oauth_token.txt`, в который надо сохранить полученный токен авторизации. Сам файл необходимо разместить рядом с тестами в папке `tests`.

**Важно!** Не рекомедуется запускать тесты для действующего аккаунта Яндекс.Диска, т.к. в процессе выполнения тестов выполняются различные операции над содержимым Диска. Рекомендуется для целей тестирования создать отдельную учетную запись на сервисах Яндекса и использовать ее.

## Лицензия

Библиотека **oscript-yadisk** распространяется под лицензией *Apache 2.0*, ее текст находится в файле [LICENSE](LICENSE). Лицензия распространяется только на код библиотеки **oscript-yadisk**. Использование API Яндекс.Диска регламентируется [Условиями использования сервиса "API Яндекс.Диска"](https://yandex.ru/legal/disk_api/) (https://yandex.ru/legal/disk_api/).