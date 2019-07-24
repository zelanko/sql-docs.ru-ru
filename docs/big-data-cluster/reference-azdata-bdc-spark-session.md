---
title: Справочник по сеансу аздата BDC Spark
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам сеанса аздата BDC Spark.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 20b7ac3dcf72482e80278ce0f0df922026232a6d
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426104"
---
# <a name="azdata-bdc-spark-session"></a>сеанс аздата BDC Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

В следующей статье приводятся ссылки на команды **сеанса Spark для BDC** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md) .

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Создание сеанса аздата BDC Spark](#azdata-bdc-spark-session-create) | Создайте новый сеанс Spark.
[Список сеансов аздата BDC Spark](#azdata-bdc-spark-session-list) | Перечислите все активные сеансы в Spark.
[сведения о сеансе аздата BDC Spark](#azdata-bdc-spark-session-info) | Получение сведений об активном сеансе Spark.
[Журнал сеансов аздата BDC Spark](#azdata-bdc-spark-session-log) | Получение журналов выполнения для активного сеанса Spark.
[состояние сеанса Spark BDC аздата](#azdata-bdc-spark-session-state) | Получение состояния выполнения для активного сеанса Spark.
[Удаление сеанса аздата BDC Spark](#azdata-bdc-spark-session-delete) | Удаление сеанса Spark.
## <a name="azdata-bdc-spark-session-create"></a>Создание сеанса аздата BDC Spark
При этом создается новый интерактивный сеанс Spark. Вызывающий объект должен указать тип сеанса Spark. Этот сеанс находится за пределами жизненного цикла выполнения аздата и должен быть удален с помощью удаления сеанса Spark
```bash
azdata bdc spark session create [--session-kind -k] 
                                [--jar-files -j]  
                                [--py-files -p]  
                                [--files -f]  
                                [--driver-memory]  
                                [--driver-cores]  
                                [--executor-memory]  
                                [--executor-cores]  
                                [--executor-count]  
                                [--archives -a]  
                                [--queue -q]  
                                [--name -n]  
                                [--config -c]  
                                [--timeout-seconds -t]
```
### <a name="examples"></a>Примеры
Создайте сеанс.
```bash
azdata spark session create --session-kind pyspark
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--session-kind -k`
Имя типа создаваемого сеанса.  Один из Spark, pyspark, Spark или SQL.
#### `--jar-files -j`
Список путей к JAR-файлам.  Чтобы передать в список JSON, необходимо закодировать значения.  Пример: "[" entry1 "," entry2 "]".
#### `--py-files -p`
Список путей к файлам Python.  Чтобы передать в список JSON, необходимо закодировать значения.  Пример: "[" entry1 "," entry2 "]".
#### `--files -f`
Список путей к файлам.  Чтобы передать в список JSON, необходимо закодировать значения.  Пример: "[" entry1 "," entry2 "]".
#### `--driver-memory`
Объем памяти, выделяемой драйверу.  Укажите единицы измерения в качестве части значения.  Пример 512M или 2G.
#### `--driver-cores`
Количество ядер ЦП, выделяемых драйверу.
#### `--executor-memory`
Объем памяти, выделяемой для исполнителя.  Укажите единицы измерения в качестве части значения.  Пример 512M или 2G.
#### `--executor-cores`
Количество ядер ЦП, выделяемых для исполнителя.
#### `--executor-count`
Число выполняемых экземпляров исполнителя.
#### `--archives -a`
Список путей к архивам.  Чтобы передать в список JSON, необходимо закодировать значения.  Пример: "[" entry1 "," entry2 "]".
#### `--queue -q`
Имя очереди Spark, в которой будет выполняться сеанс.
#### `--name -n`
Имя сеанса Spark.
#### `--config -c`
Список пар "имя значение", содержащих значения конфигурации Spark.  Кодируется как словарь JSON.  Пример: "{" Name ":" value "," имя2 ":" value2 "}".
#### `--timeout-seconds -t`
Время ожидания простоя сеанса в секундах.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-spark-session-list"></a>Список сеансов аздата BDC Spark
Перечислите все активные сеансы в Spark.
```bash
azdata bdc spark session list 
```
### <a name="examples"></a>Примеры
Список всех активных сеансов.
```bash
azdata spark session list
```
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-spark-session-info"></a>сведения о сеансе аздата BDC Spark
Получает сведения о сеансе для активного сеанса Spark с заданным ИДЕНТИФИКАТОРом.  Идентификатор сеанса возвращается из "Создание сеанса Spark".
```bash
azdata bdc spark session info --session-id -i 
                              
```
### <a name="examples"></a>Примеры
Получение сведений о сеансе с ИДЕНТИФИКАТОРом 0.
```bash
azdata spark session info --session-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-spark-session-log"></a>Журнал сеансов аздата BDC Spark
Получает записи журнала сеанса для активного сеанса Spark с заданным ИДЕНТИФИКАТОРом.  Идентификатор сеанса возвращается из "Создание сеанса Spark".
```bash
azdata bdc spark session log --session-id -i 
                             
```
### <a name="examples"></a>Примеры
Получение журнала сеанса для сеанса с ИДЕНТИФИКАТОРом 0.
```bash
azdata spark session log --session-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-spark-session-state"></a>состояние сеанса Spark BDC аздата
Получает состояние сеанса для активного сеанса Spark с заданным ИДЕНТИФИКАТОРом.  Идентификатор сеанса возвращается из "Создание сеанса Spark".
```bash
azdata bdc spark session state --session-id -i 
                               
```
### <a name="examples"></a>Примеры
Получение состояния сеанса для сеанса с ИДЕНТИФИКАТОРом 0.
```bash
azdata spark session state --session-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-spark-session-delete"></a>Удаление сеанса аздата BDC Spark
Это приведет к удалению интерактивного сеанса Spark. Идентификатор сеанса возвращается из "Создание сеанса Spark".
```bash
azdata bdc spark session delete --session-id -i 
                                
```
### <a name="examples"></a>Примеры
Удаление сеанса.
```bash
azdata spark session delete --session-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md). Дополнительные сведения об установке средства **аздата** см. в [статье Установка аздата для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
