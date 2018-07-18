---
title: EXCEPT и INTERSECT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- INTERSECT_TSQL
- EXCEPT_TSQL
- INTERSECT
- EXCEPT
dev_langs:
- TSQL
helpviewer_keywords:
- EXCEPT operator [Transact-SQL]
- queries [SQL Server], comparing
- comparing queries
- INTERSECT operator
ms.assetid: b1019300-171a-4a1a-854f-e1e751de3565
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ed56afe00af1dc153815c92e95eb25e4e449fb8b
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36257206"
---
# <a name="set-operators---except-and-intersect-transact-sql"></a>Операторы Set — EXCEPT и INTERSECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Эти операторы возвращают различные строки, сравнивая результаты двух запросов.  
  
 Оператор EXCEPT возвращает уникальные строки из левого входного запроса, которые не выводятся правым входным запросом.  
  
 Оператор INTERSECT возвращает уникальные строки, выводимые левым и правым входными запросами.  
  
 Основные правила объединения результирующих наборов двух запросов с оператором EXCEPT или INTERSECT таковы:  
  
-   количество и порядок столбцов должны быть одинаковыми во всех запросах;  
  
-   типы данных должны быть совместимыми.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
{ <query_specification> | ( <query_expression> ) }   
{ EXCEPT | INTERSECT }  
{ <query_specification> | ( <query_expression> ) }  
```  
  
## <a name="arguments"></a>Аргументы  
 \<*query_specification*> | ( \<*query_expression*> )  
 Спецификация запроса или выражение запроса, возвращающее данные для сравнения с данными, возвращенными другой спецификацией запроса или выражением запроса. Определения столбцов, обрабатываемых при операции EXCEPT или INTERSECT, могут быть разными, но они должны поддерживать возможность сравнения путем неявного преобразования типов. Если типы данных различаются, тип, используемый при выполнении сравнения и возврате результатов, определяется на основе правил [приоритета типов данных](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
 Если типы одинаковы, но различаются по точности, масштабу или длине, результат определяется на основе тех же самых правил, которые действуют при объединении выражений. Дополнительные сведения см. в разделе [Точность, масштаб и длина (Transact-SQL)](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 Спецификация или выражение запроса не может возвращать столбцы типа **xml**, **text**, **ntext**, **image** или недвоичного пользовательского типа данных CLR, потому что эти типы данных не поддерживают сравнение.  
  
 EXCEPT  
 Возвращает все различные значения, возвращенные запросом, указанным слева от оператора EXCEPT, но отсутствующие в результатах выполнения правого запроса.  
  
 INTERSECT  
 Возвращает все различные значения, входящие в результаты выполнения запросов, указанных как слева, так и справа от оператора INTERSECT.  
  
## <a name="remarks"></a>Примечания  
 Если типы данных сравниваемых столбцов, возвращенных запросами, указанными слева и справа от оператора EXCEPT или INTERSECT, являются символьными типами с разными режимами сопоставления, сравнение выполняется в соответствии с правилами [очередности параметров сортировки](../../t-sql/statements/collation-precedence-transact-sql.md). Если нужное преобразование выполнить не удается, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] возвращает ошибку.  
  
 Если сравниваются значения столбцов с целью определения различных строк, два значения NULL считаются равными.  
  
 Имена столбцов в результирующем наборе, возвращаемом оператором EXCEPT или INTERSECT, совпадают с именами, возвращаемыми запросом, который указан слева от оператора.  
  
 Имена столбцов или псевдонимы в предложениях ORDER BY должны ссылаться на имена столбцов, возвращаемых запросом, указанным слева от оператора.  
  
 Возможность хранения пустых значений в каком-либо столбце результирующего набора, возвращаемого оператором EXCEPT или INTERSECT, зависит от того, поддерживает ли это соответствующий столбец, возвращаемый запросом, указанным слева от оператора.  
  
 Если оператор EXCEPT или INTERSECT используется в выражении вместе с другими операторами, оно обрабатывается в следующем порядке:  
  
1.  Выражения в скобках  
  
2.  Оператор INTERSECT  
  
3.  Операторы EXCEPT и UNION обрабатываются слева направо в соответствии с их позицией в выражении.  
  
 Если оператор EXCEPT или INTERSECT используется для сравнения более двух наборов запросов, преобразование типов данных выполняется на основе сравнения двух запросов сразу с соблюдением вышеупомянутых правил обработки выражений.  
  
 Операторы EXCEPT и INTERSECT нельзя использовать в определениях распределенных секционированных представлений и уведомлениях о запросах.  
  
 Операторы EXCEPT и INTERSECT можно применять в распределенных запросах, но они будут выполнены только на локальном сервере и не будут распространены на связанный сервер. Таким образом, использование операторов EXCEPT и INTERSECT в распределенных запросах может сказаться на производительности.  
  
 При использовании в операции EXCEPT или INTERSECT в результирующем наборе полностью поддерживаются быстрые однонаправленные и статические курсоры. Если в операции EXCEPT или INTERSECT применяется курсор, управляемый набором ключей, или динамический курсор, то курсор результирующего набора преобразуется в статический курсор.  
  
 При выводе данных об операции EXCEPT с помощью средства графического отображения плана в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] операция представляется как [left anti semi join](../../relational-databases/showplan-logical-and-physical-operators-reference.md), а операция INTERSECT — как [left semi join](../../relational-databases/showplan-logical-and-physical-operators-reference.md).  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется использование операторов `INTERSECT` и `EXCEPT`. Первый запрос возвращает все значения из таблицы `Production.Product` для сравнения с результатами, полученными с операндами `INTERSECT` и `EXCEPT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product ;  
--Result: 504 Rows  
```  
  
 Следующий запрос возвращает все различные значения, входящие в результаты выполнения, как левого, так и правого запроса оператора `INTERSECT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product  
INTERSECT  
SELECT ProductID   
FROM Production.WorkOrder ;  
--Result: 238 Rows (products that have work orders)  
```  
  
 Следующий запрос возвращает все уникальные значения, возвращенные запросом, указанным слева от оператора `EXCEPT`, но отсутствующие в результатах выполнения правого запроса.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.Product  
EXCEPT  
SELECT ProductID   
FROM Production.WorkOrder ;  
--Result: 266 Rows (products without work orders)  
```  
  
 Следующий запрос возвращает все уникальные значения, возвращенные запросом, указанным слева от оператора `EXCEPT`, но отсутствующие в результатах выполнения правого запроса. Таблицы расположены в порядке, обратном предыдущему примеру.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID   
FROM Production.WorkOrder  
EXCEPT  
SELECT ProductID   
FROM Production.Product ;  
--Result: 0 Rows (work orders without products)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример демонстрирует использование операторов `INTERSECT` и `EXCEPT`. Первый запрос возвращает все значения из таблицы `FactInternetSales` для сравнения с результатами, полученными с операндами `INTERSECT` и `EXCEPT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales;  
--Result: 60398 Rows  
```  
  
 Следующий запрос возвращает все различные значения, входящие в результаты выполнения, как левого, так и правого запроса оператора `INTERSECT`.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
INTERSECT   
SELECT CustomerKey   
FROM DimCustomer   
WHERE DimCustomer.Gender = 'F'  
ORDER BY CustomerKey;  
--Result: 9133 Rows (Sales to customers that are female.)  
```  
  
 Следующий запрос возвращает все уникальные значения, возвращенные запросом, указанным слева от оператора `EXCEPT`, но отсутствующие в результатах выполнения правого запроса.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
EXCEPT   
SELECT CustomerKey   
FROM DimCustomer   
WHERE DimCustomer.Gender = 'F'  
ORDER BY CustomerKey;  
--Result: 9351 Rows (Sales to customers that are not female.)  
```  
  
  

