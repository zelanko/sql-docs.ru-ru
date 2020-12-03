---
description: Вычисления pushdown в PolyBase
title: Вычисления pushdown в PolyBase | Документация Майкрософт
dexcription: Enable pushdown computation to improve performance of queries on your Hadoop cluster. You can select a subset of rows/columns in an external table for pushdown.
ms.date: 11/17/2020
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
monikerRange: '>= sql-server-2016 || =sqlallproducts-allversions'
ms.openlocfilehash: 59ff1e7807a8bdd8427e3b902bf53c111d52c7b7
ms.sourcegitcommit: 4c3949f620d09529658a2172d00bfe37aeb1a387
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2020
ms.locfileid: "96127842"
---
# <a name="pushdown-computations-in-polybase"></a>Вычисления pushdown в PolyBase

[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

Вычисление pushdown повышает производительность запросов во внешних источниках данных. Начиная с SQL Server 2016 вычисления pushdown были доступны для внешних источников данных Hadoop. SQL Server 2019 предлагает вычисления pushdown для других типов внешних источников данных.

## <a name="enable-pushdown-computation"></a> Активация вычислений pushdown

В следующих статьях содержатся сведения о настройке вычислений pushdown для конкретных типов внешних источников данных.

- [Enable pushdown computation](polybase-configure-hadoop.md#pushdown) (Активация вычислений pushdown)
- [Настройка PolyBase для доступа к внешним данным в Oracle](polybase-configure-oracle.md)
- [Настройка PolyBase для доступа к внешним данным в Teradata](polybase-configure-teradata.md)
- [Настройка PolyBase для доступа к внешним данным в MongoDB](polybase-configure-mongodb.md)
- [Настройка доступа к внешним данным в PolyBase с помощью универсальных типов ODBC](polybase-configure-odbc-generic.md)
- [Настройка PolyBase для доступа к внешним данным в SQL Server](polybase-configure-sql-server.md)

## <a name="select-a-subset-of-rows"></a>Выбор подмножества строк

Включение предиката позволяет повысить производительность для запроса, отбирающего подмножество строк из внешней таблицы.

В этом примере SQL Server 2016 инициирует задание map-reduce для получения строк, соответствующих предикату `customer.account_balance < 200000` в Hadoop. Так как запрос можно выполнить и без сканирования всех строк в таблице, в SQL Server копируются только строки, удовлетворяющие условиям предиката. Это существенно экономит время и место для временного хранения данных, если число клиентов с балансом < 200 000 меньше числа клиентов с балансом >= 200 000.

```sql
SELECT * FROM customer WHERE customer.account_balance < 200000
SELECT * FROM SensorData WHERE Speed > 65;  
```

### <a name="select-a-subset-of-columns"></a>Выбор подмножества столбцов

Включение предиката позволяет повысить производительность для запроса, отбирающего подмножество столбцов из внешней таблицы.

В этом запросе SQL Server запускает задание map-reduce, предназначенное для предварительной обработки текстового файла Hadoop, разделенного запятыми, при которой в SQL Server копируются данные только для двух столбцов — customer.name и customer.zip_code.

```sql
SELECT customer.name, customer.zip_code
FROM customer
WHERE customer.account_balance < 200000
```

### <a name="pushdown-for-basic-expressions-and-operators"></a>Включение основных выражений и операторов

SQL Server позволяет использовать для включения предикатов следующие основные выражения и операторы:

- Операторы двоичного сравнения (`<`, `>`, `=`, `!=`, `<>`, `>=`, `<=`) для чисел, значений дат и времени.
- Арифметические операторы (`+`, `-`, `*`, `/`, `%`).
- Логические операторы (`AND`, `OR`).
- Унарные операторы (`NOT`, `IS NULL`, `IS NOT NULL`).

Операторы `BETWEEN`, `NOT`, `IN` и `LIKE` поддерживают принудительную отправку. Фактическое поведение зависит от того, каким образом оптимизатор запросов перезаписывает выражения операторов как последовательности инструкций с использованием основных операторов отношения.

В этом примере запрос содержит несколько предикатов, которые могут быть переданы в Hadoop. SQL Server может отправлять в Hadoop задания map-reduce для выполнения предиката `customer.account_balance <= 200000`. Выражение `BETWEEN 92656 AND 92677` также состоит из двоичных и логических операций, которые могут быть переданы в Hadoop. Логический оператор **AND** в столбцах `customer.account_balance AND customer.zipcode` является конечным выражением.

С учетом этого сочетания предикатов задания map-reduce могут выполнять все условия, указанные в предложении WHERE. В SQL Server копируются только те данные, которые соответствуют условиям `SELECT`.

```sql
SELECT * FROM customer 
WHERE customer.account_balance <= 200000 
    AND customer.zipcode BETWEEN 92656 AND 92677
```

## <a name="examples"></a>Примеры

### <a name="force-pushdown"></a>Принудительное включение

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (FORCE EXTERNALPUSHDOWN);
```

### <a name="disable-pushdown"></a>Отключить включение

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (DISABLE EXTERNALPUSHDOWN);
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о PolyBase см. в [этом руководстве](polybase-guide.md).
