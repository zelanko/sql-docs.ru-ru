---
title: "[] (Шаблон — символ(ы) для сопоставления) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/06/2016
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
- Match
- wildcard
- '[ ]'
- '[_]_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[ ] (wildcard - character(s) to match)'
ms.assetid: 57817576-0bf1-49ed-b05d-fac27e8fed7a
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e6de8f9b9a1ed36135915e5985312a02c02fba6d
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="--wildcard---characters-to-match-transact-sql"></a>\[\] (Подстановочный знак — знаков для совпадения) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Соответствует любому одиночному символу в пределах указанного диапазона или набора, указывается в квадратных скобках `[ ]`. Эти символы-шаблоны можно использовать при сравнении строк, которые задействуют соответствие шаблону, таких как `LIKE` и `PATINDEX`.  
  
## <a name="examples"></a>Примеры  
### <a name="a-simple-example"></a>А. простой пример   
Следующий пример возвращает имена, начинающиеся с буквы `m`. `[n-z]`Указывает, что вторая буква должен быть где-нибудь в диапазоне от `n` для `z`. Шаблон процента `%` позволяет ни один не символов, начиная с 3. `model` И `msdb` базы данных соответствуют этому критерию. `master` База данных не поддерживает и исключается из результирующего набора.
 
```sql
SELECT name FROM sys.databases
WHERE name LIKE 'm[n-z]%';
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]  

```
name
-----
model
msdb
```   
 Вы можете иметь дополнительные соответствующие базы данных установлен.


### <a name="b-more-complex-example"></a>Б. более сложный пример   
 В следующем примере оператор [] используется для поиска идентификаторов и имен всех сотрудников из базы данных [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], имеющих адреса с четырехзначным почтовым индексом.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT e.BusinessEntityID, p.FirstName, p.LastName, a.PostalCode  
FROM HumanResources.Employee AS e  
INNER JOIN Person.Person AS p ON e.BusinessEntityID = p.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
INNER JOIN Person.Address AS a ON a.AddressID = ea.AddressID  
WHERE a.PostalCode LIKE '[0-9][0-9][0-9][0-9]';  
```  
  
 Результирующий набор:  
  
```  
EmployeeID      FirstName      LastName      PostalCode  
----------      ---------      ---------     ----------  
290             Lynn           Tsoflias      3000  
```  



  
## <a name="see-also"></a>См. также:  
 [КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Функция PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
  [% &#40; Подстановочный знак — символ &#40; s &#41; для соответствия &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
 [&#91; ^ &#93; &#40; Подстановочный знак — символ &#40; s &#41; Не для соответствия &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [\_&#40; Шаблон — совпадение одного символа &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  
