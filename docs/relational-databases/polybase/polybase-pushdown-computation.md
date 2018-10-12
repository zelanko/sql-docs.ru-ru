---
title: Вычисления pushdown в PolyBase | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 571b75284aeaf711245a2f96407df173e37a7649
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780932"
---
# <a name="pushdown-computations-in-polybase"></a>Вычисления pushdown в PolyBase


##<a name="dmv"></a>DMV

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Вычисление pushdown повышает производительность запросов в кластере Hadoop.

## <a name="enable-pushdown"></a>Активация вычислений pushdown

Шаги активации вычислений pushdown приведены в следующем разделе:

[Enable pushdown computation](polybase-configure-hadoop.md#pushdown) (Активация вычислений pushdown)

## <a name="select-a-subset-of-rows"></a>Выбор подмножества строк

Включение предиката позволяет повысить производительность для запроса, отбирающего подмножество строк из внешней таблицы.

В этом примере SQL Server 2016 инициирует задание map-reduce для получения строк, соответствующих предикату `customer.account_balance < 200000` в Hadoop. Так как запрос можно выполнить и без сканирования всех строк в таблице, в SQL Server копируются только строки, удовлетворяющие условиям предиката. Это существенно экономит время и место для временного хранения данных, если число клиентов с балансом < 200 000 меньше числа клиентов с балансом >= 200 000.

```sql
SELECT * FROM customer WHERE customer.account_balance < 200000
SELECT * FROM SensorData WHERE Speed > 65;  
```

### <a name="select-a-subset-of-columns"></a>Выбор подмножества столбцов

Включение предиката позволяет повысить производительность для запроса, отбирающего подмножество столбцов из внешней таблицы.

В этом запросе SQL Server запускает задание map-reduce, предназначенное для предварительной обработки текстового файла Hadoop, разделенного запятыми, при которой в параллельное хранилище данных SQL Server попадают данные только для двух столбцов — customer.name и customer.zip_code.

```sql
SELECT customer.name, customer.zip_code FROM customer WHERE customer.account_balance < 200000
```

### <a name="pushdown-for-basic-expressions-and-operators"></a>Включение основных выражений и операторов

SQL Server позволяет использовать для включения предикатов следующие основные выражения и операторы:

+ Операторы двоичного сравнения (\<, >, =,! =, <>, > =, < =) для чисел, дат и значений времени.

+ Арифметические операторы (+, -, *, /, %).

+ Логические операторы (AND, OR).

+ Унарные операторы (NOT, IS NULL, IS NOT NULL).

Операторы BETWEEN, NOT, IN и LIKE можно включить. Фактическое поведение зависит от того, каким образом оптимизатор запросов перезаписывает выражения операторов как последовательности инструкций с использованием основных операторов отношения.

В этом примере запрос содержит несколько предикатов, которые могут быть переданы в Hadoop. SQL Server может отправлять в Hadoop задания map-reduce для выполнения предиката `customer.account_balance <= 200000`. Выражение `BETWEEN 92656 and 92677` также состоит из двоичных и логических операций, которые могут быть переданы в Hadoop. Логический оператор **AND** в столбцах `customer.account_balance and customer.zipcode` является конечным выражением.

С учетом этого сочетания предикатов задания map-reduce могут выполнять все условия, указанные в предложении WHERE. В хранилище SQL Server PDW копируются только те данные, которые соответствуют условиям отбора.

```sql
SELECT * FROM customer WHERE customer.account_balance <= 200000 AND customer.zipcode BETWEEN 92656 AND 92677
```

## <a name="force-pushdown"></a>Принудительное включение

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (FORCE EXTERNALPUSHDOWN);
```

## <a name="disable-pushdown"></a>Отключить включение

```sql
SELECT * FROM [dbo].[SensorData]
WHERE Speed > 65
OPTION (DISABLE EXTERNALPUSHDOWN);
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в [этом руководстве](polybase-guide.md).
