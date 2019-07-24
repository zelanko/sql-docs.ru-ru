---
title: Справочник по пакету аздата BDC Spark
titleSuffix: SQL Server big data clusters
description: Справочная статья по пакетным командам аздата BDC Spark.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6e242b26f439b49dbf0b3cf5ab50ea46c273f45f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426164"
---
# <a name="azdata-bdc-spark-batch"></a>пакет аздата BDC Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки на команды **пакета BDC Spark** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md) .

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Создание пакета аздата BDC Spark](#azdata-bdc-spark-batch-create) | Создайте новый пакет Spark.
[список пакетов Spark для аздата BDC](#azdata-bdc-spark-batch-list) | Перечислите все пакеты в Spark.
[сведения о пакете Spark BDC аздата](#azdata-bdc-spark-batch-info) | Получение сведений об активном пакете Spark.
[Журнал пакетной службы BDC Spark аздата](#azdata-bdc-spark-batch-log) | Получение журналов выполнения для пакета Spark.
[Пакетное состояние аздата BDC Spark](#azdata-bdc-spark-batch-state) | Получение состояния выполнения для пакета Spark.
[Удаление пакета аздата BDC Spark](#azdata-bdc-spark-batch-delete) | Удаление пакета Spark.
## <a name="azdata-bdc-spark-batch-create"></a>Создание пакета аздата BDC Spark
Будет создано новое задание пакетной службы Spark, которое выполняет предоставленный код.
```bash
azdata bdc spark batch create --file -f 
                              [--class-name -c]  
                              [--arguments -a]  
                              [--jar-files -j]  
                              [--py-files -p]  
                              [--files]  
                              [--driver-memory]  
                              [--driver-cores]  
                              [--executor-memory]  
                              [--executor-cores]  
                              [--executor-count]  
                              [--archives]  
                              [--queue -q]  
                              [--name -n]  
                              [--config]
```
### <a name="examples"></a>Примеры
Создайте новый пакет Spark.
```bash
azdata spark batch create --code "2+2"
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--file -f`
Путь к файлу для выполнения.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--class-name -c`
Имя класса для выполнения при передаче одного или нескольких JAR-файлов.
#### `--arguments -a`
Список аргументов.  Чтобы передать в список JSON, необходимо закодировать значения.  Пример: "[" entry1 "," entry2 "]".
#### `--jar-files -j`
Список путей к JAR-файлам.  Чтобы передать в список JSON, необходимо закодировать значения.  Пример: "[" entry1 "," entry2 "]".
#### `--py-files -p`
Список путей к файлам Python.  Чтобы передать в список JSON, необходимо закодировать значения.  Пример: "[" entry1 "," entry2 "]".
#### `--files`
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
#### `--archives`
Список путей к архивам.  Чтобы передать в список JSON, необходимо закодировать значения.  Пример: "[" entry1 "," entry2 "]".
#### `--queue -q`
Имя очереди Spark, в которой будет выполняться сеанс.
#### `--name -n`
Имя сеанса Spark.
#### `--config`
Список пар "имя значение", содержащих значения конфигурации Spark.  Кодируется как словарь JSON.  Пример: "{" Name ":" value "," имя2 ":" value2 "}".
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
## <a name="azdata-bdc-spark-batch-list"></a>список пакетов Spark для аздата BDC
Перечислите все пакеты в Spark.
```bash
azdata bdc spark batch list 
```
### <a name="examples"></a>Примеры
Список всех активных пакетов.
```bash
azdata spark batch list
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
## <a name="azdata-bdc-spark-batch-info"></a>сведения о пакете Spark BDC аздата
Получает сведения для пакета Spark с заданным ИДЕНТИФИКАТОРом.  Идентификатор пакета возвращается из раздела "Создание пакетной службы Spark".
```bash
azdata bdc spark batch info --batch-id -i 
                            
```
### <a name="examples"></a>Примеры
Получение сведений о пакете для пакета с ИДЕНТИФИКАТОРом 0.
```bash
azdata spark batch info --batch-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--batch-id -i`
Идентификатор пакета Spark.
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
## <a name="azdata-bdc-spark-batch-log"></a>Журнал пакетной службы BDC Spark аздата
Получает записи журнала пакетной службы для пакета Spark с заданным ИДЕНТИФИКАТОРом.  Идентификатор пакета возвращается из раздела "Создание пакетной службы Spark".
```bash
azdata bdc spark batch log --batch-id -i 
                           
```
### <a name="examples"></a>Примеры
Получите журнал пакетной службы для пакета с ИДЕНТИФИКАТОРом 0.
```bash
azdata spark batch log --batch-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--batch-id -i`
Идентификатор пакета Spark.
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
## <a name="azdata-bdc-spark-batch-state"></a>Пакетное состояние аздата BDC Spark
Получает состояние пакета для пакета Spark с заданным ИДЕНТИФИКАТОРом.  Идентификатор пакета возвращается из раздела "Создание пакетной службы Spark".
```bash
azdata bdc spark batch state --batch-id -i 
                             
```
### <a name="examples"></a>Примеры
Получение состояния пакета для пакета с ИДЕНТИФИКАТОРом 0.
```bash
azdata spark batch state --batch-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--batch-id -i`
Идентификатор пакета Spark.
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
## <a name="azdata-bdc-spark-batch-delete"></a>Удаление пакета аздата BDC Spark
Это приведет к удалению пакета Spark. Идентификатор пакета возвращается из раздела "Создание пакетной службы Spark".
```bash
azdata bdc spark batch delete --batch-id -i 
                              
```
### <a name="examples"></a>Примеры
Удаление пакета.
```bash
azdata spark batch delete --batch-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--batch-id -i`
Идентификатор пакета Spark.
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
