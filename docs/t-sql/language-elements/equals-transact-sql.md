---
title: "= (Равно) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- =
- = (Equals)
- Equals
- =_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- equals operator (=)
- = (equals operator)
ms.assetid: 18885245-5f55-4831-8f0b-7f2a3e82e246
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bf23c40678950000b65a66dc29bdba8b4615c7b1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="-equals-transact-sql"></a>= (равно) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Проверяет равенство двух выражений (оператор сравнения) в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression = expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md). Если выражения не того же типа данных, необходимо неявно преобразовываться в тип данных другого типа данных одного выражения. Преобразование основано на правилах [приоритетов типов данных](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Типы результата  
 Логическое значение  
  
## <a name="remarks"></a>Замечания  
 При сравнении двух выражений со значениями NULL результат зависит от `ANSI_NULLS` параметр:  
  
-   Если `ANSI_NULLS` имеет значение ON, результатом является значение NULL, в соответствии со стандартом ANSI NULL (или неизвестное) значение не равно другому значению NULL или unknown.  
  
-   Если `ANSI_NULLS` имеет значение OFF, результат NULL, по сравнению с NULL имеет значение TRUE.  

Дополнительные сведения см. в разделе [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md).
  
 Каких-либо сравнения значения NULL (unknown), отличное от NULL значение всегда дает результат FALSE.  
  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using--in-a-simple-query"></a>A. Использование = в простом запросе  
 В следующем примере оператор равенства используется, чтобы возвратить все строки таблицы `HumanResources.Department`, в которых значение столбца `GroupName` равно слову «Manufacturing».  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE GroupName = 'Manufacturing';  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
DepartmentID Name  
------------ --------------------------------------------------  
7            Production  
8            Production Control  
  
(2 row(s) affected)  
  
```  
  
### <a name="b-comparing-null-and-non-null-values"></a>Б. Сравнение значений NULL и значений, отличных от NULL  
 Следующий пример иллюстрирует использование операторов «равно» (`=`) и «не равно» (`<>`) для сравнения со значениями `NULL` и не NULL в таблице. Этот пример также демонстрирует, что использование конструкции `IS NULL` не зависит от значения параметра `SET ANSI`_`NULLS`.  
  
```  
-- Create table t1 and insert 3 rows.  
CREATE TABLE dbo.t1 (a INT NULL);  
INSERT INTO dbo.t1 VALUES (NULL),(0),(1);  
GO  
  
-- Print message and perform SELECT statements.  
PRINT 'Testing default setting';  
DECLARE @varname int;   
SET @varname = NULL;  
  
SELECT a  
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to ON and test.  
PRINT 'Testing ANSI_NULLS ON';  
SET ANSI_NULLS ON;  
GO  
DECLARE @varname int;  
SET @varname = NULL  
  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to OFF and test.  
PRINT 'Testing SET ANSI_NULLS OFF';  
SET ANSI_NULLS OFF;  
GO  
DECLARE @varname int;  
SET @varname = NULL;  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- Drop table t1.  
DROP TABLE dbo.t1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Testing default setting  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
a  
-----------  
0  
1  
  
(2 row(s) affected)  
  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
Testing ANSI_NULLS ON  
a  
-----------  
  
(0 row(s) affected)  
  
a  
-----------  
  
(0 row(s) affected)  
  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
Testing SET ANSI_NULLS OFF  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
a  
-----------  
0  
1  
  
(2 row(s) affected)  
  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

