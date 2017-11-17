---
title: "НЕКОТОРЫЕ | ВСЕ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- SOME
- SOME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- scalar values
- comparing scalar with single-column set
- ANY operator
- SOME | ANY keyword
- single-column set of values [SQL Server]
ms.assetid: 1f717ad6-f67b-4980-9397-577ecb0e5789
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a67801d62cb05cdb0b589548e8bd3f9676d5840a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="some--any-transact-sql"></a>SOME | ANY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Сравнивает скалярное значение с набором значений, состоящим из одного столбца. Ключевые слова SOME и ANY эквивалентны.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
scalar_expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
     { SOME | ANY } ( subquery )   
```  
  
## <a name="arguments"></a>Аргументы  
 *scalar_expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Любой допустимый оператор сравнения.  
  
 SOME | ANY  
 Указывает на необходимость сравнения.  
  
 *вложенный запрос*  
 Вложенный запрос, содержащий результирующий набор, состоящий из одного столбца. Тип данных возвращаемого столбца должен быть тот же тип данных, как *scalar_expression*.  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="result-value"></a>Значение результата  
 SOME или ANY возвращает **TRUE** Если указанное сравнение имеет значение TRUE для любой пары (*scalar_expression***,***x*) где *x* это значение в наборе один столбец; в противном случае возвращает **FALSE**.  
  
## <a name="remarks"></a>Замечания  
 SOME необходим *scalar_expression* для сравнения по крайней мере одного значения, возвращаемого вложенным запросом. Для инструкций, которые требуют *scalar_expression* сравнения каждого значения, возвращаемого вложенным запросом, перечислены в разделе [все &#40; Transact-SQL &#41; ](../../t-sql/language-elements/all-transact-sql.md). Например, если вложенный запрос возвращает значения 2 и 3, *scalar_expression* = SOME (вложенными запросами) будет возвращаться TRUE для *scalar_express* 2. Если вложенный запрос возвращает значения 2 и 3, *scalar_expression* = ALL (вложенными запросами) будет возвращаться FALSE, так как некоторые значения вложенного запроса (значение 3) не отвечают критериям этого выражения.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-running-a-simple-example"></a>A. Выполнение простого примера  
 Следующие инструкции создают простую таблицу и добавляют значения `1`, `2`, `3` и `4` в столбец `ID`.  
  
```  
CREATE TABLE T1  
(ID int) ;  
GO  
INSERT T1 VALUES (1) ;  
INSERT T1 VALUES (2) ;  
INSERT T1 VALUES (3) ;  
INSERT T1 VALUES (4) ;  
```  
  
 Следующий запрос возвращает значение `TRUE`, так как `3` меньше некоторых из значений в таблице.  
  
```  
IF 3 < SOME (SELECT ID FROM T1)  
PRINT 'TRUE'   
ELSE  
PRINT 'FALSE' ;  
```  
  
 Следующий запрос возвращает значение `FALSE`, так как `3` не меньше каждого из значений в таблице.  
  
```  
IF 3 < ALL (SELECT ID FROM T1)  
PRINT 'TRUE'   
ELSE  
PRINT 'FALSE' ;  
```  
  
### <a name="b-running-a-practical-example"></a>Б. Выполнение практического примера  
 В следующем примере создается хранимая процедура, которая определяет, является ли все компоненты указанного `SalesOrderID` в `AdventureWorks2012` базы данных может быть изготовлено за указанное число дней. В этом примере для создания списка количества значений `DaysToManufacture` для всех компонентов `SalesOrderID` используется вложенный запрос, а затем проводится проверка того, превышают ли все значения, возвращаемые вложенным запросом, указанное количество дней. Если каждое возвращаемое значение `DaysToManufacture` меньше заданного значения, то условие равно TRUE и печатается первое сообщение.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE ManyDaysToComplete @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays < SOME  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'At least one item for this order cannot be manufactured in specified number of days.'  
ELSE   
PRINT 'All items for this order can be manufactured in the specified number of days or less.' ;  
  
```  
  
 Для проверки этой процедуры выполните ее с помощью `SalesOrderID``49080`, имеющий один заказ, требующий `2` дня и два заказа, требующие немедленного. Первая инструкция отвечает этим критериям. Второй запрос этим критериям не отвечает.  
  
```  
EXECUTE ManyDaysToComplete 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in the specified number of days or less.`  
  
```  
EXECUTE ManyDaysToComplete 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `At least one item for this order cannot be manufactured in specified number of days.`  
  
## <a name="see-also"></a>См. также:  
 [ВСЕ &#40; Transact-SQL &#41;](../../t-sql/language-elements/all-transact-sql.md)   
 [РЕГИСТР &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [ИН &#40; Transact-SQL &#41;](../../t-sql/language-elements/in-transact-sql.md)  
  
  

