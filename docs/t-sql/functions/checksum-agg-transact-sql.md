---
title: "CHECKSUM_AGG (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKSUM_AGG
- CHECKSUM_AGG_TSQL
dev_langs: TSQL
helpviewer_keywords:
- checksum values
- CHECKSUM_AGG function
- groups [SQL Server], checksum values
ms.assetid: cdede70c-4eb5-4c92-98ab-b07787ab7222
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3499cd8fb118d12fdbf450c23f2919fd0003cee7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="checksumagg-transact-sql"></a>CHECKSUM_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает контрольную сумму значений в группе. Значения NULL пропускаются. Может следовать [предложение OVER](../../t-sql/queries/select-over-clause-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CHECKSUM_AGG ( [ ALL | DISTINCT ] expression )  
```  
  
## <a name="arguments"></a>Аргументы  
**ALL**  
Применяет агрегатную функцию ко всем значениям. ALL является параметром по умолчанию.
  
DISTINCT  
Указывает, что CHECKSUM_AGG возвращает контрольную сумму уникальных значений.
  
*expression*  
Должно быть целым числом [выражение](../../t-sql/language-elements/expressions-transact-sql.md). Агрегатные функции и вложенные запросы недопустимы.
  
## <a name="return-types"></a>Возвращаемые типы
Возвращает контрольную сумму всех *выражение* значений в виде **int**.
  
## <a name="remarks"></a>Замечания  
Функция CHECKSUM_AGG может использоваться для обнаружения изменений в таблице.
  
Порядок строк в таблице не влияет на результат функции CHECKSUM_AGG. Кроме того, функции CHECKSUM_AGG могут использоваться с ключевым словом DISTINCT и предложением GROUP BY.
  
Если одно из значений в списке выражений меняется, то обычно меняется и контрольная сумма этого списка. Однако существует небольшая вероятность того, что контрольная сумма не изменится.
  
Действие функции CHECKSUM_AGG аналогично действию других агрегатных функций. Дополнительные сведения см. в разделе [агрегатные функции &#40; Transact-SQL &#41; ](../../t-sql/functions/aggregate-functions-transact-sql.md).
  
## <a name="examples"></a>Примеры  
В следующем примере функция `CHECKSUM_AGG` используется для обнаружения изменений в столбце `Quantity` таблицы `ProductInventory` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
--Get the checksum value before the column value is changed.  
SELECT CHECKSUM_AGG(CAST(Quantity AS int))  
FROM Production.ProductInventory;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
------------------------  
262  
```  
  
```sql
UPDATE Production.ProductInventory   
SET Quantity=125  
WHERE Quantity=100;  
GO  
--Get the checksum of the modified column.  
SELECT CHECKSUM_AGG(CAST(Quantity AS int))  
FROM Production.ProductInventory;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
------------------------  
287  
```  
  
## <a name="see-also"></a>См. также:
[Контрольная сумма &#40; Transact-SQL &#41;](../../t-sql/functions/checksum-transact-sql.md)  
[ЧЕРЕЗ предложение &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
