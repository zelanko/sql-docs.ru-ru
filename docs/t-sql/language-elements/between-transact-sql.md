---
title: "МЕЖДУ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/28/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BETWEEN
- BETWEEN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- inclusive ranges
- testing range
- exclusive ranges
- NOT BETWEEN operator
- BETWEEN operator
- range to test [SQL Server]
ms.assetid: a5d5b050-203e-4355-ac85-e08ef5ca7823
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 05971c739eec2137e8a4acd213a322a37d60d054
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="between-transact-sql"></a>Оператор BETWEEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Определяет диапазон для проверки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
test_expression [ NOT ] BETWEEN begin_expression AND end_expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *test_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) для проверки в диапазоне, определяемом *begin_expression*и *end_expression*. *test_expression* должен быть один и тот же тип данных, как *begin_expression* и *end_expression*.  
  
 NOT  
 Указывает, что результат предиката должен быть инвертирован.  
  
 *begin_expression*  
 Любое допустимое выражение. *begin_expression* должен быть один и тот же тип данных, как *test_expression* и *end_expression*.  
  
 *end_expression*  
 Любое допустимое выражение. *end_expression* должен быть один и тот же тип данных, как *test_expression*и *begin_expression*.  
  
 и  
 Действует как заполнитель, указывающий *test_expression* должно находиться в пределах заданных значений аргументов *begin_expression* и *end_expression*.  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="result-value"></a>Значение результата  
 BETWEEN возвращает **TRUE** Если значение *test_expression* больше или равно значению *begin_expression* и меньше или равно значению *end_expression*.  
  
 NOT BETWEEN возвращает **TRUE** Если значение *test_expression* меньше, чем значение *begin_expression* или больше, чем значение *end_expression* .  
  
## <a name="remarks"></a>Remarks  
 Для задания исключающего диапазона используйте операторы «больше» (>) и «меньше» (<). Если любой параметр предиката BETWEEN или NOT BETWEEN имеет значение NULL, результат не определен (UNKNOWN).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-between"></a>A. Использование оператора BETWEEN  
 Следующий пример возвращает сведения о ролях баз данных в базе данных. Первый запрос возвращает все роли. Во втором примере `BETWEEN` предложение для ограничения ролей в указанном `database_id` значения.  
  
```sql  
SELECT principal_id, name 
FROM sys.database_principals
WHERE type = 'R';

SELECT principal_id, name 
FROM sys.database_principals
WHERE type = 'R'
AND principal_id BETWEEN 16385 AND 16390;
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]   
```  
principal_id    name
------------  ---- 
0               public
16384           db_owner
16385           db_accessadmin
16386           db_securityadmin
16387           db_ddladmin
16389           db_backupoperator
16390           db_datareader
16391           db_datawriter
16392           db_denydatareader
16393           db_denydatawriter
```  
```  
principal_id    name
------------  ---- 
16385           db_accessadmin
16386           db_securityadmin
16387           db_ddladmin
16389           db_backupoperator
16390           db_datareader
```  
  
### <a name="b-using--and--instead-of-between"></a>Б. Использование операторов > и < вместо BETWEEN  
 В следующем примере используются операторы «больше» (`>`) и «меньше» (`<`); так как они позволяют задавать исключающий диапазон, здесь выводятся только девять строк вместо десяти из предыдущего примера.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT e.FirstName, e.LastName, ep.Rate  
FROM HumanResources.vEmployee e   
JOIN HumanResources.EmployeePayHistory ep   
    ON e.BusinessEntityID = ep.BusinessEntityID  
WHERE ep.Rate > 27 AND ep.Rate < 30  
ORDER BY ep.Rate;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 FirstName   LastName             Rate  
 ---------   -------------------  ---------  
 Paula       Barreto de Mattos    27.1394  
 Janaina     Bueno                27.4038  
 Dan         Bacon                27.4038  
 Ramesh      Meyyappan            27.4038  
 Karen       Berg                 27.4038  
 David       Bradley              28.7500  
 Hazem       Abolrous             28.8462  
 Ovidiu      Cracium              28.8462  
 Rob         Walters              29.8462  
 ```    
  
### <a name="c-using-not-between"></a>В. Использование оператора NOT BETWEEN  
 В следующем примере выводятся все строки вне указанного диапазона от `27` до `30`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT e.FirstName, e.LastName, ep.Rate  
FROM HumanResources.vEmployee e   
JOIN HumanResources.EmployeePayHistory ep   
    ON e.BusinessEntityID = ep.BusinessEntityID  
WHERE ep.Rate NOT BETWEEN 27 AND 30  
ORDER BY ep.Rate;  
GO  
```  
  
### <a name="d-using-between-with-datetime-values"></a>Г. Использование оператора BETWEEN со значениями типа datetime  
 Следующий пример извлекает строки, в которой **datetime** значения — от `'20011212'` и `'20020105'`включительно.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT BusinessEntityID, RateChangeDate  
FROM HumanResources.EmployeePayHistory  
WHERE RateChangeDate BETWEEN '20011212' AND '20020105';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 BusinessEntityID RateChangeDate  
 ----------- -----------------------  
 3           2001-12-12 00:00:00.000  
 4           2002-01-05 00:00:00.000  
 ```  
 
 Запрос извлекает ожидаемые строки, так как значения даты в запросе и **datetime** значения, хранящиеся в `RateChangeDate` были заданы без указания времени даты. Если время не указано, по умолчанию оно принимается равным 0:00. Обратите внимание, что строка, время в которой позднее 12:00. 05.01.2002, не будет возвращена данным запросом, так как она находится за пределами диапазона.  
  
  
## <a name="see-also"></a>См. также  
 [&#62; &#40; Больше &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/greater-than-transact-sql.md)   
 [&#60; &#40; Меньше, чем &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/less-than-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


