---
title: "ИМЕЕТ значение NULL (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NULL_TSQL
- IS_[NOT]_NULL_TSQL
- IS_NULL_TSQL
- NULL
- '[NOT]_TSQL'
- IS
- IS_TSQL
- IS NULL
- IS [NOT] NULL
- '[NOT]'
dev_langs:
- TSQL
helpviewer_keywords:
- verifying nullability
- IS NOT NULL clause
- null values [SQL Server], verifying
- null values [SQL Server], IS [NOT] NULL
- IS [NOT] NULL clause
- testing nullability
- checking nullability
ms.assetid: cdc45cd8-e9b6-4648-8417-892fbeab15af
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 047e4fd57b91155485fddc2459e94247bb923c7e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="is-null-transact-sql"></a>ИМЕЕТ значение NULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Определяет, может ли указанное выражение быть NULL.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 NOT  
 Задает отрицание логического результата. Предикат меняет возвращаемые выражением значения на обратные, возвращая TRUE, если значение не равно NULL и FALSE, если значение равно NULL.  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Если значение *выражение* является NULL, IS NULL возвращает значение TRUE; в противном случае возвращается значение FALSE.  
  
 Если значение *выражение* является NULL, IS NOT NULL возвращает FALSE; в противном случае он возвращает значение TRUE.  
  
## <a name="remarks"></a>Замечания  
 Для определения, имеет ли выражение значение NULL, используйте IS NULL или IS NOT NULL вместо сравнения операторов (например = или !=). Сравнение операторов возвращает UNKNOWN, если хотя бы один аргумент или они оба равны NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается наименование и вес всех продуктов, для которых вес меньше `10` фунтов, или неизвестен цвет, либо `NULL`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name, Weight, Color  
FROM Production.Product  
WHERE Weight < 10.00 OR Color IS NULL  
ORDER BY Name;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере возвращается полных имен всех сотрудников среднего инициалы.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, MiddleName  
FROM DIMEmployee  
WHERE MiddleName IS NOT NULL  
ORDER BY LastName DESC;  
```  
  
## <a name="see-also"></a>См. также:  
 [РЕГИСТР &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Логические операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/logical-operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


