---
title: "ВСЕ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- ALL_TSQL
- ALL
dev_langs: TSQL
helpviewer_keywords:
- single-column set of values [SQL Server]
- ALL (Transact-SQL)
ms.assetid: 4b0c002e-1ffd-4425-a980-11fdc1f24af7
caps.latest.revision: "40"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 142fbd5b352a73e382f89a61f60fba6373902172
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="all-transact-sql"></a>ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Сравнивает скалярное значение с набором значений, состоящим из одного столбца.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
scalar_expression { = | <> | != | > | >= | !> | < | <= | !< } ALL ( subquery )  
```  
  
## <a name="arguments"></a>Аргументы  
 *scalar_expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Оператор сравнения.  
  
 *subquery*  
 Вложенный запрос, возвращающий результирующий набор, состоящий из одного столбца. Тип данных возвращаемого столбца должен быть тот же тип данных, как тип данных *scalar_expression*.  
  
 Ограниченная инструкция SELECT, в которой запрещено предложение ORDER BY, а также ключевое слово INTO.  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="result-value"></a>Значение результата  
 Возвращает значение TRUE, если указанное сравнение имеет значение TRUE для всех пар (*scalar_expression***,***x)*, когда *x* это значение в наборе один столбец; в противном случае возвращает FALSE.  
  
## <a name="remarks"></a>Remarks  
 ВСЕ требует *scalar_expression* для сравнения каждого значения, возвращаемого вложенным запросом. Например, если вложенный запрос возвращает значения 2 и 3, *scalar_expression* < = ALL (вложенными запросами) будет возвращаться TRUE для *scalar_expression* 2. Если вложенный запрос возвращает значения 2 и 3, *scalar_expression* = ALL (вложенными запросами) будет возвращаться FALSE, так как некоторые значения вложенного запроса (значение 3) не отвечают критериям этого выражения.  
  
 Для инструкций, которые требуют *scalar_expression* сравнения только одного значения, возвращаемого вложенным запросом, перечислены в разделе [НЕКОТОРЫЕ &#124; ВСЕ &#40; Transact-SQL &#41; ](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 В этом разделе имеются ссылки на выражение ALL при его использовании совместно с вложенными запросами. Все могут также использоваться с [ОБЪЕДИНЕНИЕ](../../t-sql/language-elements/set-operators-union-transact-sql.md) и [ВЫБЕРИТЕ](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается хранимая процедура, которая определяет, является ли все компоненты указанного `SalesOrderID` в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных может быть изготовлено за указанное число дней. В этом примере вложенный запрос используется для создания списка числовых значений `DaysToManufacture` для всех заказов с указанным идентификатором `SalesOrderID`, после чего происходит проверка того, что время производства всех заказов (`DaysToManufacture`) находится в пределах указанного числа дней.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE DaysToBuild @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays >= ALL  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'All items for this order can be manufactured in specified number of days or less.'  
ELSE   
PRINT 'Some items for this order cannot be manufactured in specified number of days or less.' ;  
  
```  
  
 Для проверки этой процедуры выполните ее, используя заказ `SalesOrderID 49080`. В него входит один компонент, производство которого занимает `2` дня, и два компонента, производство которых занимает 0 дней. Первая из нижеследующих инструкций отвечает этим критериям. Второй запрос этим критериям не отвечает.  
  
```  
EXECUTE DaysToBuild 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in specified number of days or less.`  
  
```  
EXECUTE DaysToBuild 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Some items for this order cannot be manufactured in specified number of days or less.`  
  
## <a name="see-also"></a>См. также  
 [РЕГИСТР &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [ИН &#40; Transact-SQL &#41;](../../t-sql/language-elements/in-transact-sql.md)  
  
  
