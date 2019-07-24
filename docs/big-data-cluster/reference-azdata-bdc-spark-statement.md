---
title: Справочник по инструкциям Spark для BDC аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам инструкции Spark для аздата BDC.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 778980ac6b93e7db79d59182fbd18ab4cfdb8b75
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426094"
---
# <a name="azdata-bdc-spark-statement"></a>аздата BDC, инструкция Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

В следующей статье приводятся ссылки на команды **инструкции Spark для BDC** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md) .

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[список инструкций Spark BDC аздата](#azdata-bdc-spark-statement-list) | Перечисление всех инструкций в заданном сеансе Spark.
[создание инструкции Spark BDC аздата](#azdata-bdc-spark-statement-create) | Создать новую инструкцию Spark в заданном сеансе.
[сведения о инструкции Spark BDC аздата](#azdata-bdc-spark-statement-info) | Получение сведений о запрошенной инструкции в заданном сеансе Spark.
[отмена инструкции Spark BDC аздата](#azdata-bdc-spark-statement-cancel) | Отмена инструкции в рамках данного сеанса Spark.
## <a name="azdata-bdc-spark-statement-list"></a>список инструкций Spark BDC аздата
Перечисление всех инструкций в заданном сеансе Spark.
```bash
azdata bdc spark statement list --session-id -i 
                                
```
### <a name="examples"></a>Примеры
Вывод списка всех инструкций сеанса.
```bash
azdata spark statement list --session-id 0
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
## <a name="azdata-bdc-spark-statement-create"></a>создание инструкции Spark BDC аздата
При этом создается и выполняется новая инструкция в заданном сеансе.  Если выполняется быстрое выполнение, результат содержит выходные данные выполнения.  В противном случае результат можно получить с помощью команды "сведения о сеансе Spark" после завершения инструкции.
```bash
azdata bdc spark statement create --session-id -i 
                                  --code -c
```
### <a name="examples"></a>Примеры
Выполните инструкцию.
```bash
azdata spark statement create --session-id 0 --code "2+2"
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
#### `--code -c`
Строка, содержащая код, выполняемый как часть инструкции.
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
## <a name="azdata-bdc-spark-statement-info"></a>сведения о инструкции Spark BDC аздата
Это получает состояние выполнения и результаты выполнения, если Инструкция завершена. Идентификатор инструкции возвращается из "инструкции Spark Create".
```bash
azdata bdc spark statement info --session-id -i 
                                --statement-id -s
```
### <a name="examples"></a>Примеры
Получение сведений о инструкции для сеанса с ИДЕНТИФИКАТОРом 0 и ИДЕНТИФИКАТОРом инструкции 0.
```bash
azdata spark statement info --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
#### `--statement-id -s`
Идентификатор инструкции Spark в заданном ИДЕНТИФИКАТОРе сеанса.
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
## <a name="azdata-bdc-spark-statement-cancel"></a>отмена инструкции Spark BDC аздата
Это отменяет инструкцию в рамках данного сеанса Spark. Идентификатор инструкции возвращается из "инструкции Spark Create".
```bash
azdata bdc spark statement cancel --session-id -i 
                                  --statement-id -s
```
### <a name="examples"></a>Примеры
Отмена инструкции.
```bash
azdata spark statement cancel --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--session-id -i`
Идентификатор сеанса Spark.
#### `--statement-id -s`
Идентификатор инструкции Spark в заданном ИДЕНТИФИКАТОРе сеанса.
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
