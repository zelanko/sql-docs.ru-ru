---
title: "Функция NULLIF (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NULLIF
- NULLIF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], equivalent expressions
- expressions [SQL Server], null values
- NULLIF function
- equivalent expressions [SQL Server]
ms.assetid: 44c7b67e-74c7-4bb9-93a4-7a3016bd2feb
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fe8e4663688ce510d9600ebeba9d3c30703ee3aa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="nullif-transact-sql"></a>Функция NULLIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает значение NULL, если два указанных выражения равны. Например `SELECT NULLIF(4,4) AS Same, NULLIF(5,7) AS Different;` возвращает значение NULL для первого столбца (4 и 4), поскольку аналогичны двух входных значений. Во втором столбце возвращает первое значение (5), так как входные значения не совпадают. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
NULLIF ( expression , expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое скалярное [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает тот же тип, что и первый *выражение*.  
  
 Функция NULLIF возвращает первое *выражение* Если два выражения не равны. Если выражения равны, функция NULLIF возвращает значение null тип первого *выражение*.  
  
## <a name="remarks"></a>Замечания  
 Функция NULLIF аналогична поисковому выражению CASE, в котором два выражения равны, а результирующее выражение равно NULL.  
  
 В функции NULLIF не рекомендуется использовать такие зависимые от времени функции, как RAND(). Это может вызвать функцию вычисляемое дважды и возвращать разные результаты из вызовов.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-budget-amounts-that-have-not-changed"></a>A. Возвращение неизменившихся сумм бюджета  
 В следующем примере производится создание таблицы `budgets` для отображения отдела (`dept`), его текущего (`current_year`) и предыдущего бюджета (`previous_year`). Для текущего года для отдела, бюджет которого не изменился с предыдущего года, выводится значение `NULL`, а значение `0` указывается для указания того, что бюджет еще не определен. Для получения среднего значения только для тех отделов, которым уже назначен бюджет и включения значения прошлогоднего бюджета (используется значение `previous_year`, если `current_year` равен `NULL`), используются функции `NULLIF` и `COALESCE`.  
  
```sql  
CREATE TABLE dbo.budgets  
(  
   dept            tinyint   IDENTITY,  
   current_year      decimal   NULL,  
   previous_year   decimal   NULL  
);  
INSERT budgets VALUES(100000, 150000);  
INSERT budgets VALUES(NULL, 300000);  
INSERT budgets VALUES(0, 100000);  
INSERT budgets VALUES(NULL, 150000);  
INSERT budgets VALUES(300000, 250000);  
GO    
SET NOCOUNT OFF;  
SELECT AVG(NULLIF(COALESCE(current_year,  
   previous_year), 0.00)) AS 'Average Budget'  
FROM budgets;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Average Budget  
 --------------  
 212500.000000  
 (1 row(s) affected)
 ```  
  
### <a name="b-comparing-nullif-and-case"></a>Б. Сравнение функции NULLIF и выражения CASE  
 Для демонстрации схожести функции `NULLIF` и выражения `CASE` в следующих запросах вычисляется, равны ли значения столбцов `MakeFlag` и `FinishedGoodsFlag`. В первом запросе используется функция `NULLIF`. Во втором — выражение `CASE`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,   
   NULLIF(MakeFlag,FinishedGoodsFlag)AS 'Null if Equal'  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,'Null if Equal' =  
   CASE  
       WHEN MakeFlag = FinishedGoodsFlag THEN NULL  
       ELSE MakeFlag  
   END  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
```  

### <a name="c-returning-budget-amounts-that-contain-no-data"></a>C: возвращение сумм бюджета, которые не содержат данных  
 В следующем примере создается `budgets` таблицы, загружает данные и использует `NULLIF` , чтобы вернуть значение null, если ни одна из `current_year` , ни `previous_year` содержит данные.  
  
```sql  
CREATE TABLE budgets (  
   dept           tinyint,  
   current_year   decimal(10,2),  
   previous_year  decimal(10,2)  
);  
  
INSERT INTO budgets VALUES(1, 100000, 150000);  
INSERT INTO budgets VALUES(2, NULL, 300000);  
INSERT INTO budgets VALUES(3, 0, 100000);  
INSERT INTO budgets VALUES(4, NULL, 150000);  
INSERT INTO budgets VALUES(5, 300000, 300000);  
  
SELECT dept, NULLIF(current_year,  
   previous_year) AS LastBudget  
FROM budgets;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 dept   LastBudget  
 ----   -----------  
 1      100000.00  
 2      null 
 3      0.00  
 4      null  
 5      null
 ```  
  
## <a name="see-also"></a>См. также:  
 [РЕГИСТР &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Decimal и numeric &#40; Transact-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


