---
title: '[ ] (символы-шаблоны для сопоставления) (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Match
- wildcard
- '[ ]'
- '[_]_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[ ] (wildcard - character(s) to match)'
ms.assetid: 57817576-0bf1-49ed-b05d-fac27e8fed7a
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4f9dd3de156ee0c3c8f916a7282fae4d8a5d7da3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982496"
---
# <a name="--wildcard---characters-to-match-transact-sql"></a>\[ \] (символы-шаблоны для сопоставления) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Соответствуют какому-либо одиночному символу в пределах указанного диапазона или набора, заданного в квадратных скобках `[ ]`. Эти символы-шаблоны могут использоваться в тех операциях сравнения строк, которые задействуют соответствие шаблону, например `LIKE` или `PATINDEX`.  
  
## <a name="examples"></a>Примеры  
### <a name="a-simple-example"></a>A. Простой пример   
В следующем примере возвращаются имена, начинающиеся с буквы `m`. `[n-z]` указывает, что вторая буква должна находиться в диапазоне от `n` до `z`. Символ-шаблон процента `%` разрешает любые символы, начинающиеся с символа 3, или не разрешает ни одного. Этому условию удовлетворяют базы данных `model` и `msdb`. База данных `master` не соответствует условию и исключается из результирующего набора.
 
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
 У вас могут быть установлены дополнительные соответствующие базы данных.


### <a name="b-more-complex-example"></a>Б. Более сложный пример   
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
  
 Ниже приведен результирующий набор.  
  
```  
EmployeeID      FirstName      LastName      PostalCode  
----------      ---------      ---------     ----------  
290             Lynn           Tsoflias      3000  
```  



  
## <a name="see-also"></a>См. также:  
 [LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX (Transact-SQL)](../../t-sql/functions/patindex-transact-sql.md)   
  [% (символ-шаблон для сопоставления) (Transact-SQL)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
 [&#91;^&#93; (символ-шаблон — совпадение не найдено) (Transact-SQL)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [\_ (символ-шаблон — совпадение одного символа) (Transact-SQL)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  
