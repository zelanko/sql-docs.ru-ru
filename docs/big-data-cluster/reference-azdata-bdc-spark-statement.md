---
title: Справочник по azdata bdc spark statement
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc spark statement.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 57044b75219f4c2827c322c100a5d25d5f0b274a
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653198"
---
# <a name="azdata-bdc-spark-statement"></a>azdata bdc spark statement

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

В следующей статье приводятся справочные сведения по командам **bdc spark statement** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata bdc spark statement list](#azdata-bdc-spark-statement-list) | Список всех инструкций в заданном сеансе Spark.
[azdata bdc spark statement create](#azdata-bdc-spark-statement-create) | Создание инструкции Spark в заданном сеансе.
[azdata bdc spark statement info](#azdata-bdc-spark-statement-info) | Получение сведений о запрошенной инструкции в заданном сеансе Spark.
[azdata bdc spark statement cancel](#azdata-bdc-spark-statement-cancel) | Отмена инструкции в рамках заданного сеанса Spark.
## <a name="azdata-bdc-spark-statement-list"></a>azdata bdc spark statement list
Список всех инструкций в заданном сеансе Spark.
```bash
azdata bdc spark statement list --session-id -i 
                                
```
### <a name="examples"></a>Примеры
Список всех инструкции сеанса.
```bash
azdata bdc spark statement list --session-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-spark-statement-create"></a>azdata bdc spark statement create
Создание и выполнение инструкции в заданном сеансе.  Если выполнение производится быстро, результат содержит выходные данные выполнения.  В противном случае результат можно получить с помощью команды spark session info после завершения инструкции.
```bash
azdata bdc spark statement create --session-id -i 
                                  --code -c
```
### <a name="examples"></a>Примеры
Выполнение инструкции.
```bash
azdata bdc spark statement create --session-id 0 --code "2+2"
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
#### `--code -c`
Строка с кодом, выполняемым в рамках инструкции.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-spark-statement-info"></a>azdata bdc spark statement info
Возвращает состояние и результаты выполнения, если инструкция завершена. Идентификатор инструкции возвращается из команды spark statement create.
```bash
azdata bdc spark statement info --session-id -i 
                                --statement-id -s
```
### <a name="examples"></a>Примеры
Получение сведений об инструкции для сеанса с идентификатором 0 и идентификатора инструкции 0.
```bash
azdata bdc spark statement info --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
#### `--statement-id -s`
Идентификатор инструкции Spark в заданном идентификаторе сеанса.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-spark-statement-cancel"></a>azdata bdc spark statement cancel
Отмена инструкции в рамках заданного сеанса Spark. Идентификатор инструкции возвращается из команды spark statement create.
```bash
azdata bdc spark statement cancel --session-id -i 
                                  --statement-id -s
```
### <a name="examples"></a>Примеры
Отмена инструкции.
```bash
azdata bdc spark statement cancel --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
#### `--statement-id -s`
Идентификатор инструкции Spark в заданном идентификаторе сеанса.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства **аздата** см. в разделе [Установка [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]аздата для управления ](deploy-install-azdata.md).
