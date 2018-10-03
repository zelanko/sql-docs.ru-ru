---
title: PERCENTILE_CONT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/20/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PERCENTILE_CONT_TSQL
- PERCENTILE_CONT
dev_langs:
- TSQL
helpviewer_keywords:
- analytic functions, PERCENTILE_CONT
- PERCENTILE_CONT function
ms.assetid: d019419e-5297-4994-97d5-e9c8fc61bbf4
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f7e82e8577269a206e0172f170a66e1b1250c5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674868"
---
# <a name="percentilecont-transact-sql"></a>PERCENTILE_CONT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Вычисляет процентиль на основе постоянного распределения значения столбца в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Результат интерполируется и может отличаться от всех конкретных значений из этого столбца.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
PERCENTILE_CONT ( numeric_literal )   
    WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_literal*  
 Процентиль, который необходимо вычислить. Значение должно находиться в диапазоне от 0.0 до 1,0.  
  
 WITHIN GROUP **(** ORDER BY *order_by_expression* [ **ASC** | DESC ]**)**  
 Указывает список числовых значений, который следует отсортировать и по которому будет вычисляться процентиль. Разрешен только один аргумент *order_by_expression*. Результатом вычисления выражения должен быть точный числовой тип (**int**, **bigint**, **smallint**, **tinyint**, **numeric**, **bit**, **decimal**, **smallmoney**, **money**) или приблизительный числовой тип (**float**, **real**). Другие типы данных не допускаются. По умолчанию задан порядок сортировки по возрастанию.  
  
 OVER **(** \<partition_by_clause> **)**  
 Делит результирующий набор, полученный с помощью предложения FROM, на секции, к которым применяется функция вычисления процентиля. Дополнительные сведения см. в статье [Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md). В функции PERCENTILE_CONT нельзя указывать \<предложение ORDER BY>, а также \<строки или предложение диапазона> синтаксиса OVER.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **float(53)**  
  
## <a name="compatibility-support"></a>Поддержка совместимости  
 При уровне совместимости 110 и выше WITHIN GROUP является зарезервированным ключевым словом. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="general-remarks"></a>Общие замечания  
 Все значения NULL, имеющиеся в наборе данных, игнорируются.  
  
 Функция PERCENTILE_CONT не детерминирована. Дополнительные сведения см. в разделе [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
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
Shipping and Receiving 9.250000      9.0000
```  
  
## <a name="see-also"></a>См. также:  
 [PERCENTILE_DISC (Transact-SQL)](../../t-sql/functions/percentile-disc-transact-sql.md)  
  
  


