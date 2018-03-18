---
title: "$PARTITION (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- $partition_TSQL
- $partition
dev_langs:
- TSQL
helpviewer_keywords:
- $PARTITION function
- partitions [SQL Server], numbers
ms.assetid: abc865d0-57a8-49da-8821-29457c808d2a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7fb60ef43ba359bef366a113704a784ce0f73902
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="partition-transact-sql"></a>$PARTITION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает номер секции, с которой будет сопоставлен набор значений столбцов секционирования для любой указанной функции секционирования в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
[ database_name. ] $PARTITION.partition_function_name(expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, которая содержит функцию секционирования.  
  
 *partition_function_name*  
 Имя существующей функции секционирования, которая применяется к набору значений столбцов секционирования.  
  
 *expression*  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md), тип данных которого должен совпадать или иметь возможность неявного преобразования в тип данных соответствующего столбца секционирования. Аргумент *expression* также может быть именем столбца секционирования, который в настоящее время используется в *partition_function_name*.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Remarks  
 $PARTITION возвращает значение типа **int** в диапазоне от 1 до числа секций функции секционирования.  
  
 $PARTITION возвращает номер секции для любого допустимого значения вне зависимости от того, существует ли данное значение в секционированной таблице или индексе, который пользуется функцией секционирования.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-getting-the-partition-number-for-a-set-of-partitioning-column-values"></a>A. Получение номера секции для набора значений столбцов секционирования  
 Следующий пример создает функцию секционирования `RangePF1` для разделения таблицы или индекса на четыре секции. $PARTITION используется для определения того, что значение `10`, представляющее столбец секционирования `RangePF1`, попадет в секцию 1 таблицы.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE PARTITION FUNCTION RangePF1 ( int )  
AS RANGE FOR VALUES (10, 100, 1000) ;  
GO  
SELECT $PARTITION.RangePF1 (10) ;  
GO  
```  
  
### <a name="b-getting-the-number-of-rows-in-each-nonempty-partition-of-a-partitioned-table-or-index"></a>Б. Получение количества строк в каждой непустой секции секционированной таблицы или представления  
 Следующий пример иллюстрирует получение числа строк в каждой секции таблицы `TransactionHistory`, которая содержит данные. Таблица `TransactionHistory` использует функцию секционирования `TransactionRangePF1`, которая разбивает ее по столбцу `TransactionDate`.  
  
 Для выполнения этого примера требуется запустить скрипт PartitionAW.sql для образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Дополнительные сведения см. в разделе [PartitioningScript](http://go.microsoft.com/fwlink/?LinkId=201015).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT $PARTITION.TransactionRangePF1(TransactionDate) AS Partition,   
COUNT(*) AS [COUNT] FROM Production.TransactionHistory   
GROUP BY $PARTITION.TransactionRangePF1(TransactionDate)  
ORDER BY Partition ;  
GO  
```  
  
### <a name="c-returning-all-rows-from-one-partition-of-a-partitioned-table-or-index"></a>В. Получение всех строк из одной секции секционированной таблицы или индекса  
 Следующий пример иллюстрирует получение всех строк, которые содержит секция `5` таблицы `TransactionHistory`.  
  
> [!NOTE]  
>  Для выполнения этого примера требуется запустить скрипт PartitionAW.sql для образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Дополнительные сведения см. в разделе [PartitioningScript](http://go.microsoft.com/fwlink/?LinkId=201015).  
  
```  
SELECT * FROM Production.TransactionHistory  
WHERE $PARTITION.TransactionRangePF1(TransactionDate) = 5 ;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/create-partition-function-transact-sql.md)  
  
  
