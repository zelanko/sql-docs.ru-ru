---
title: '[^] Подстановочный знак для исключения символов'
description: Подстановочный знак T-SQL для несовпадающих символов
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- wildcard
- '[^]_TSQL'
- '[^]'
- Not Match
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[^] (wildcard - character(s) not to match)'
ms.assetid: b970038f-f4e7-4a5d-96f6-51e3248c6aef
author: rothja
ms.author: jroth
ms.openlocfilehash: e7291bc39092d4f65fd69f8c4050bb52a512ef04
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76831736"
---
# <a name="-wildcard---characters-not-to-match-transact-sql"></a>\[^\] (символы-шаблоны не для сопоставления) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Сопоставляется с любым отдельным символом, находящимся вне диапазона или набора, указанного в квадратных скобках `[^]`. Эти символы-шаблоны могут использоваться в тех операциях сравнения строк, которые задействуют соответствие шаблону, например `LIKE` или `PATINDEX`. 
  
## <a name="examples"></a>Примеры  
### <a name="a-simple-example"></a>A. Простой пример   
 В следующем примере оператор [^] используется для поиска первых пяти лиц в таблице `Contact`, имена которых начинаются с `Al`, а третья буква имени отличается от символа `a`.  
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP 5 FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Al[^a]%';  
```  
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]  

```
FirstName     LastName
---------     --------
Alex          Adams
Alexandra     Adams
Allison       Adams
Alisha        Alan
Alexandra     Alexander
```
### <a name="b-searching-for-ranges-of-characters"></a>Б. Поиск диапазонов символов

Набор подстановочных знаков может включать в себя отдельные символы или диапазоны символов, а также сочетания символов и диапазонов. В следующем примере оператор [^] используется для поиска строки, которая не начинается с буквы или цифры.

```sql
SELECT [object_id], OBJECT_NAME(object_id) AS [object_name], name, column_id 
FROM sys.columns 
WHERE name LIKE '[^0-9A-z]%';
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]  

```
object_id     object_name   name    column_id
---------     -----------   ----    ---------
1591676718    JunkTable     _xyz    1
```
  
## <a name="see-also"></a>См. также:  
 [LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX (Transact-SQL)](../../t-sql/functions/patindex-transact-sql.md)   
 [% (символ-шаблон для сопоставления) (Transact-SQL)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91; &#93; (символ-шаблон для сопоставления) (Transact-SQL)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [\_ (символ-шаблон — совпадение одного символа) (Transact-SQL)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
  
  
