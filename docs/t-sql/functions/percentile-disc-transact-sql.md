---
title: "Функция PERCENTILE_DISC (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/20/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PERCENTILE_DISC
- PERCENTILE_DISC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PERCENTILE_DISC function
- analytic functions,PERCENTILE_DISC
ms.assetid: b545413d-c4f7-4c8e-8617-607599a26680
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a70610ecc826cda363cc0eea25baf090b24acc08
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="percentiledisc-transact-sql"></a>PERCENTILE_DISC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Вычисляет определенный процентиль для отсортированных значений из всего набора строк или в пределах определенных секций набора строк в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для данного значения процентиля *P*, функция PERCENTILE_DISC сортирует значения выражения в предложении ORDER BY и возвращает значение с наименьшим значением CUME_DIST (в отношении той же спецификации сортировки), больше или равно *P*. Например, функция PERCENTILE_DISC (0.5) вычислит 50-й процентиль (то есть медиану) выражения. Функция PERCENTILE_DISC вычисляет процентиль на основе дискретного распределения значений столбца. Результат вычисления равен определенному значению из столбца.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
PERCENTILE_DISC ( numeric_literal ) WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *литерал*  
 Процентиль, который необходимо вычислить. Значение должно находиться в диапазоне от 0.0 до 1,0.  
  
 В ГРУППЕ **(** ORDER BY *выражении order_by_expression* [ **ASC** | DESC]**)**  
 Задает список значений для сортировки и которому будет вычисляться процентиль. Только один *выражении order_by_expression* разрешено. По умолчанию задан порядок сортировки по возрастанию. Список значений может иметь любой из типов данных, которые являются допустимыми для данной операции сортировки.  
  
 НАД **(** \<partition_by_clause > **)**  
 Делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция вычисления процентиля. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md). \<Предложение ORDER BY > и \<строки или предложение диапазона > в функции PERCENTILE_DISC нельзя указывать.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип возвращаемого значения определяется *выражении order_by_expression* типа.  
  
## <a name="compatibility-support"></a>Поддержка совместимости  
 При уровне совместимости 110 и выше WITHIN GROUP является зарезервированным ключевым словом. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="general-remarks"></a>Общие замечания  
 Все значения NULL, имеющиеся в наборе данных, игнорируются.  
  
 Функция PERCENTILE_DISC не детерминирована. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-basic-syntax-example"></a>A. Пример простого синтаксиса  
 В следующем примере функции PERCENTILE_CONT и PERCENTILE_DISC используются для определения медианной заработной платы сотрудников в каждом отделе. Обратите внимание на то, что эти функции могут возвращать разные значения. Это происходит потому, что функция PERCENTILE_CONT интерполирует соответствующее значение независимо от того, существует ли оно в наборе данных, тогда как функция PERCENTILE_DISC всегда возвращает фактически существующее в наборе значение.  
  
```  
USE AdventureWorks2012;  
  
SELECT DISTINCT Name AS DepartmentName  
      ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianCont  
      ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY ph.Rate)   
                            OVER (PARTITION BY Name) AS MedianDisc  
FROM HumanResources.Department AS d  
INNER JOIN HumanResources.EmployeeDepartmentHistory AS dh   
    ON dh.DepartmentID = d.DepartmentID  
INNER JOIN HumanResources.EmployeePayHistory AS ph  
    ON ph.BusinessEntityID = dh.BusinessEntityID  
WHERE dh.EndDate IS NULL;  
```  
  
 Здесь приводится частичный результирующий набор.  
  
 ```
DepartmentName        MedianCont    MedianDisc
--------------------   ----------   ----------
Document Control       16.8269      16.8269
Engineering            34.375       32.6923
Executive              54.32695     48.5577
Human Resources        17.427850    16.5865
```
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-basic-syntax-example"></a>Б. Пример простого синтаксиса  
 В следующем примере функции PERCENTILE_CONT и PERCENTILE_DISC используются для определения медианной заработной платы сотрудников в каждом отделе. Обратите внимание на то, что эти функции могут возвращать разные значения. Это происходит потому, что функция PERCENTILE_CONT интерполирует соответствующее значение независимо от того, существует ли оно в наборе данных, тогда как функция PERCENTILE_DISC всегда возвращает фактически существующее в наборе значение.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT DepartmentName  
       ,PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianCont  
       ,PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY BaseRate)  
        OVER (PARTITION BY DepartmentName) AS MedianDisc  
FROM dbo.DimEmployee;  
  
```  
  
 Здесь приводится частичный результирующий набор.  
  
 ```
DepartmentName        MedianCont    MedianDisc  
--------------------   ----------   ----------  
Document Control       16.826900    16.8269  
Engineering            34.375000    32.6923  
Human Resources        17.427850    16.5865  
Shipping and Receiving  9.250000     9.0000
```  
  
## <a name="see-also"></a>См. также:  
 [PERCENTILE_CONT &#40; Transact-SQL &#41;](../../t-sql/functions/percentile-cont-transact-sql.md)  
  
  



