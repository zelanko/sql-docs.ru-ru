---
title: Справочник по командам azdata arc postgres server
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata arc postgres server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3f34baeca8914adfcceda30766d46da50aa13517
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90942889"
---
# <a name="azdata-arc-postgres-server"></a>azdata arc postgres server

Применяется к `azdata`

В следующей статье приводятся справочные сведения по командам **sql** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды

|Команда|Описание|
| --- | --- |
[azdata arc postgres server create](#azdata-arc-postgres-server-create) | Создание группы серверов PostgreSQL.
[azdata arc postgres server edit](#azdata-arc-postgres-server-edit) | Изменение конфигурации группы серверов PostgreSQL.
[azdata arc postgres server delete](#azdata-arc-postgres-server-delete) | Удаление группы серверов PostgreSQL.
[azdata arc postgres server show](#azdata-arc-postgres-server-show) | Отображение сведений о группе серверов PostgreSQL.
[azdata arc postgres server list](#azdata-arc-postgres-server-list) | Список групп серверов PostgreSQL.
[azdata arc postgres server config](reference-azdata-arc-postgres-server-config.md) | Команды настройки.
[azdata arc postgres server backup](reference-azdata-arc-postgres-server-backup.md) | Управление резервными копиями группы серверов PostgreSQL.
## <a name="azdata-arc-postgres-server-create"></a>azdata arc postgres server create
Чтобы задать пароль для группы серверов, укажите переменную среды AZDATA_PASSWORD
```bash
azdata arc postgres server create --name -n 
                                  [--path]  
                                  
[--cores-limit -cl]  
                                  
[--cores-request -cr]  
                                  
[--memory-limit -ml]  
                                  
[--memory-request -mr]  
                                  
[--storage-class-data -scd]  
                                  
[--storage-class-logs -scl]  
                                  
[--storage-class-backups -scb]  
                                  
[--extensions]  
                                  
[--volume-size-data -vsd]  
                                  
[--volume-size-logs -vsl]  
                                  
[--volume-size-backups -vsb]  
                                  
[--workers -w]  
                                  
[--engine-version -ev]  
                                  
[--no-external-endpoint]  
                                  
[--dev]  
                                  
[--port]  
                                  
[--no-wait]  
                                  
[--engine-settings -e]
```
### <a name="examples"></a>Примеры
Создание группы серверов PostgreSQL.
```bash
azdata arc postgres server create -n pg1
```
Создание группы серверов PostgreSQL с параметрами подсистемы. Оба приведенных ниже примера допустимы.
```bash
azdata arc postgres server create -n pg1 --engine-settings "key1=val1"
azdata arc postgres server create -n pg1 --engine-settings "key2=val2"
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя экземпляра.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--path`
Путь к исходному файлу JSON для группы серверов PostgreSQL. Делать это не обязательно.
#### `--cores-limit -cl`
Максимальное количество ядер ЦП для экземпляра Postgres, которые могут использоваться на каждом узле. Поддерживаются дробные ядра.
#### `--cores-request -cr`
Минимальное количество ядер ЦП, которые должны быть доступны на каждом узле для планирования службы. Поддерживаются дробные ядра.
#### `--memory-limit -ml`
Ограничение памяти для экземпляра Postgres в виде числа, за которым следует обозначение Ki (килобайты), Mi (мегабайты) или Gi (гигабайты).
#### `--memory-request -mr`
Запрос памяти для экземпляра Postgres в виде числа, за которым следует обозначение Ki (килобайты), Mi (мегабайты) или Gi (гигабайты).
#### `--storage-class-data -scd`
Класс хранения, используемый для томов постоянного хранения данных.
#### `--storage-class-logs -scl`
Класс хранения, используемый для томов постоянного хранения журналов.
#### `--storage-class-backups -scb`
Класс хранения, используемый для томов постоянного хранения резервных копий.
#### `--extensions`
Разделенный запятыми список расширений Postgres, которые должны загружаться при запуске. Поддерживаемые значения см. в документации по Postgres.
#### `--volume-size-data -vsd`
Размер тома хранилища, которое будет использоваться для данных, в виде положительного числа, за которым следует обозначение Ki (килобайты), Mi (мегабайты) или Gi (гигабайты).
#### `--volume-size-logs -vsl`
Размер тома хранилища, которое будет использоваться для журналов, в виде положительного числа, за которым следует обозначение Ki (килобайты), Mi (мегабайты) или Gi (гигабайты).
#### `--volume-size-backups -vsb`
Размер тома хранилища, которое будет использоваться для резервных копий, в виде положительного числа, за которым следует обозначение Ki (килобайты), Mi (мегабайты) или Gi (гигабайты).
#### `--workers -w`
Количество рабочих узлов для формирования сегментированного кластера или нуль (по умолчанию) Postgres, состоящего из одного узла.
#### `--engine-version -ev`
Должно быть 11 или 12. Значение по умолчанию — 12.
#### `--no-external-endpoint`
Если задано, внешняя служба не создается. В противном случае внешняя служба будет создана с использованием того же типа службы, что и контроллер данных.
#### `--dev`
Если указан данный параметр, то этот экземпляр считается экземпляром разработчика и не учитывается при оплате.
#### `--port`
Необязательный элемент.
#### `--no-wait`
Если указан данный параметр, команда не будет ждать, пока экземпляр перейдет в состоянии готовности.
#### `--engine-settings -e`
Разделенный запятыми список параметров подсистемы Postgres в формате "key1=val1, key2=val2".
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-arc-postgres-server-edit"></a>azdata arc postgres server edit
Изменение конфигурации группы серверов PostgreSQL.
```bash
azdata arc postgres server edit --name -n 
                                [--path]  
                                
[--workers -w]  
                                
[--engine-version -ev]  
                                
[--cores-limit -cl]  
                                
[--cores-request -cr]  
                                
[--memory-limit -ml]  
                                
[--memory-request -mr]  
                                
[--extensions]  
                                
[--dev]  
                                
[--port]  
                                
[--no-wait]  
                                
[--engine-settings -e]  
                                
[--replace-engine-settings -re]  
                                
[--admin-password]
```
### <a name="examples"></a>Примеры
Изменение конфигурации группы серверов PostgreSQL.
```bash
azdata arc postgres server edit --src ./spec.json -n pg1
```
Изменение группы серверов PostgreSQL с параметрами подсистемы.
```bash
azdata arc postgres server edit -n pg1 --engine-settings "key2=val2"
```
Изменение группы серверов PostgreSQL и замена существующих параметров подсистемы новым параметром key1=val1.
```bash
azdata arc postgres server edit -n pg1 --engine-settings "key1=val1" --replace-engine-settings
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя изменяемой группы серверов PostgreSQL. Имя, под которым развернут ваш экземпляр, изменить нельзя.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--path`
Путь к исходному файлу JSON для группы серверов PostgreSQL. Делать это не обязательно.
#### `--workers -w`
Количество рабочих узлов для формирования сегментированного кластера или нуль (по умолчанию) Postgres, состоящего из одного узла.
#### `--engine-version -ev`
Версию подсистемы изменить нельзя. --engine-version можно использовать вместе с параметром --name для обнаружения гипермасштабированной группы серверов PostgreSQL, если две группы серверов с подсистемами разных версий имеют одинаковое имя. --engine-version — необязательный параметр, который должен иметь значение 11 или 12, когда он используется для обнаружения группы серверов.
#### `--cores-limit -cl`
Максимальное количество ядер ЦП для экземпляра Postgres, которые могут использоваться на каждом узле, поддерживаются дробные ядра. Чтобы удалить параметр cores_limit, укажите его значение как пустую строку.
#### `--cores-request -cr`
Минимальное количество ядер ЦП, которые должны быть доступны на каждом узле для планирования службы; поддерживаются дробные ядра. Чтобы удалить параметр cores_request, укажите его значение как пустую строку.
#### `--memory-limit -ml`
Ограничение памяти для экземпляра Postgres в виде числа, за которым следует обозначение Ki (килобайты), Mi (мегабайты) или Gi (гигабайты). Чтобы удалить параметр memory_limit, укажите его значение как пустую строку.
#### `--memory-request -mr`
Запрос памяти для экземпляра Postgres в виде числа, за которым следует обозначение Ki (килобайты), Mi (мегабайты) или Gi (гигабайты). Чтобы удалить параметр memory_request, укажите его значение как пустую строку.
#### `--extensions`
Разделенный запятыми список расширений Postgres, которые должны загружаться при запуске. Поддерживаемые значения см. в документации по Postgres.
#### `--dev`
Если указан данный параметр, то этот экземпляр считается экземпляром разработчика и не учитывается при оплате.
#### `--port`
Необязательный элемент.
#### `--no-wait`
Если указан данный параметр, команда не будет ждать, пока экземпляр перейдет в состоянии готовности.
#### `--engine-settings -e`
Разделенный запятыми список параметров подсистемы Postgres в формате "key1=val1, key2=val2". Указанные параметры будут объединены с существующими параметрами. Чтобы удалить параметр, укажите пустое значение, например "removedKey=". При изменении параметра подсистемы, требующего перезагрузки, служба будет перезапущена, чтобы немедленно применить новые параметры.
#### `--replace-engine-settings -re`
Если задан параметр --engine-settings, то все существующие пользовательские параметры подсистемы будут заменены новым набором параметров и значений.
#### `--admin-password`
Если указан этот параметр, то в качестве пароля администратора сервера Postgres будет использоваться значение переменной среды AZDATA_PASSWORD, если она есть, или значение, введенное по приглашению.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-arc-postgres-server-delete"></a>azdata arc postgres server delete
Удаление группы серверов PostgreSQL.
```bash
azdata arc postgres server delete --name -n 
                                  [--engine-version -ev]
```
### <a name="examples"></a>Примеры
Удаление группы серверов PostgreSQL.
```bash
azdata arc postgres server delete -n pg1
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя группы серверов PostgreSQL.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--engine-version -ev`
--engine-version можно использовать вместе с параметром --name для обнаружения гипермасштабированной группы серверов PostgreSQL, если две группы серверов с подсистемами разных версий имеют одинаковое имя. --engine-version — необязательный параметр, который должен иметь значение 11 или 12, когда он используется для обнаружения группы серверов.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-arc-postgres-server-show"></a>azdata arc postgres server show
Отображение сведений о группе серверов PostgreSQL.
```bash
azdata arc postgres server show --name -n 
                                [--engine-version -ev]  
                                
[--path -p]
```
### <a name="examples"></a>Примеры
Отображение сведений о группе серверов PostgreSQL.
```bash
azdata arc postgres server show -n pg1
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя группы серверов PostgreSQL.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--engine-version -ev`
--engine-version можно использовать вместе с параметром --name для обнаружения гипермасштабированной группы серверов PostgreSQL, если две группы серверов с подсистемами разных версий имеют одинаковое имя. --engine-version — необязательный параметр, который должен иметь значение 11 или 12, когда он используется для обнаружения группы серверов.
#### `--path -p`
Путь, куда должна быть записана полная спецификация для группы серверов PostgreSQL. Если этот параметр опущен, спецификация будет записана в стандартный вывод.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-arc-postgres-server-list"></a>azdata arc postgres server list
Список групп серверов PostgreSQL.
```bash
azdata arc postgres server list 
```
### <a name="examples"></a>Примеры
Список групп серверов PostgreSQL.
```bash
azdata arc postgres server list
```
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). 

Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata](..\install\deploy-install-azdata.md).

