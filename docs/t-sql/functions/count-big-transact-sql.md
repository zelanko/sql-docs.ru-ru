---
title: "COUNT_BIG (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COUNT_BIG_TSQL
- COUNT_BIG
dev_langs:
- TSQL
helpviewer_keywords:
- totals [SQL Server], COUNT_BIG function
- counting items in group
- groups [SQL Server], number of items in
- number of group items
- COUNT_BIG function
ms.assetid: f2e3601f-487e-4917-bb01-47b1047908cd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ad2b7e5343547bb65c6d81de8c6586ef5209e52a
ms.sourcegitcommit: 0e305dce04dcd1aa83c39328397524b352c96386
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="countbig--sql"></a>COUNT_BIG (-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает количество элементов в группе. Функция COUNT_BIG работает подобно функции COUNT. Единственное различие между двумя функциями — возвращаемые значения. Функция COUNT_BIG всегда возвращает значение типа данных **bigint**. Функция COUNT всегда возвращает значение типа данных **int**.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Syntax for SQL Server and Azure SQL Database  
  
COUNT_BIG ( { [ ALL | DISTINCT ] expression } | * )  
   [ OVER ( [ partition_by_clause ] [ order_by_clause ] ) ]  
```  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Aggregation Function Syntax  
COUNT_BIG ( { [ [ ALL | DISTINCT ] expression ] | * } )  
  
-- Analytic Function Syntax  
COUNT_BIG ( { expression | * } ) OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Аргументы  
ALL  
Применяет агрегатную функцию ко всем значениям. ALL является параметром по умолчанию.
  
DISTINCT  
Указывает, что функция COUNT_BIG возвращает количество уникальных значений, не равных NULL.
  
*expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных. Агрегатные функции и вложенные запросы не допускаются.
  
*\**  
Указывает, что все строки должны быть подсчитаны для возврата общего числа строк в таблице. Функция COUNT_BIG(*\**) не имеет параметров и не может использоваться с аргументом DISTINCT. Функция COUNT_BIG(*\**) не требует параметра *expression*, так как по определению она не использует сведения о конкретном столбце. Функция COUNT_BIG(*\**) возвращает количество строк в заданной таблице, не отбрасывая дубликаты. Она подсчитывает каждую строку отдельно. При этом учитываются и строки, содержащие значения NULL.
  
ALL  
Применяет агрегатную функцию ко всем значениям. ALL является параметром по умолчанию.
  
DISTINCT  
Указывает на то, что функция AVG будет выполнена только для одного экземпляра каждого уникального значения, независимо от того, сколько раз встречается это значение.
  
*expression*  
[Выражение](../../t-sql/language-elements/expressions-transact-sql.md) категории точного числового или приблизительного числового типа данных, за исключением типа данных **bit**. Агрегатные функции и вложенные запросы не допускаются.
  
OVER **(** [ *partition_by_clause* ] [ *order_by_clause* ] **)**  
*partition_by_clause* делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция. Если этот параметр не указан, функция обрабатывает все строки результирующего набора запроса как отдельные группы. *order_by_clause* определяет логический порядок, в котором выполняется операция. Дополнительные сведения см. в статье [Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Типы возвращаемых данных
**bigint**
  
## <a name="remarks"></a>Remarks  
Функция COUNT_BIG(*) возвращает количество элементов в группе. Сюда входят значения NULL и повторяющиеся значения.
  
Функция COUNT_BIG (ALL *expression*) вычисляет *expression* для каждой строки в группе и возвращает количество значений, не равных NULL.
  
Функция COUNT_BIG (DISTINCT *expression*) вычисляет *expression* для каждой строки в группе и возвращает количество уникальных значений, не равных NULL.
  
COUNT_BIG — это детерминированная функция, если она используется без предложений OVER и ORDER BY. Она не детерминирована при использовании с предложениями OVER и ORDER BY. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Примеры  
Примеры см. в статье [COUNT (Transact-SQL)](../../t-sql/functions/count-transact-sql.md).
  
## <a name="see-also"></a>См. также раздел
[Агрегатные функции (Transact-SQL)](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[COUNT (Transact-SQL)](../../t-sql/functions/count-transact-sql.md)  
[int, bigint, smallint и tinyint (Transact-SQL)](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
[Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
