---
title: "Операторы сравнения (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], testing
- operators [Transact-SQL], comparison
- testing expressions
- Boolean data type
- Boolean expressions
- comparing expressions
- comparison operators [SQL Server]
ms.assetid: b0cc68ef-3029-484c-a917-0c15dcbc230d
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 08cdeecc9dc7da123ae94623a30913ed358de93b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="comparison-operators-transact-sql"></a>Операторы сравнения (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Операторы сравнения позволяют проверить, одинаковы ли два выражения. Операторы сравнения можно использовать для всех выражений, за исключением выражений типов **текст**, **ntext**, или **изображение** типов данных. Операторы сравнения [!INCLUDE[tsql](../../includes/tsql-md.md)] приведены в следующей таблице:  
  
|Оператор|Значение|  
|--------------|-------------|  
|[= (Равно)](../../t-sql/language-elements/equals-transact-sql.md)|Равно|  
|[> (больше)](../../t-sql/language-elements/greater-than-transact-sql.md)|Больше чем|  
|[< (меньше)](../../t-sql/language-elements/less-than-transact-sql.md)|Меньше чем|  
|[>= (больше или равно)](../../t-sql/language-elements/greater-than-or-equal-to-transact-sql.md)|Больше или равно|  
|[<= (меньше или равно)](../../t-sql/language-elements/less-than-or-equal-to-transact-sql.md)|Меньше или равно|  
|[<> (не равно)](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)|Не равно|  
|[!= (Не равно)](../../t-sql/language-elements/not-equal-to-transact-sql-exclamation.md)|Не равно (не определено стандартом ISO)|  
|[!< (Не меньше чем)](../../t-sql/language-elements/not-less-than-transact-sql.md)|Не меньше (не определено стандартом ISO)|  
|[!> (Не больше чем)](../../t-sql/language-elements/not-greater-than-transact-sql.md)|Не больше (не определено стандартом ISO)|  
  
## <a name="boolean-data-type"></a>Тип данных Boolean  
 Результат выполнения оператора сравнения имеет **логическое** тип данных. Это имеет три значения: TRUE, FALSE и UNKNOWN. Выражения, возвращающие **логическое** тип данных, называются логических выражений.  
  
 В отличие от других [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных **логическое** тип данных не может быть указан как тип данных столбца или переменной и не может быть возвращен в результирующем наборе.  
  
 Если параметр SET ANSI_NULLS имеет значение ON, оператор, в число операндов которого входит хотя бы одно выражение NULL, возвращает UNKNOWN. Когда параметр SET ANSI_NULLS имеет значение OFF, действуют те же правила, однако если оба выражения равны NULL, то оператор равенства (=) возвращает TRUE. Например, если параметр SET ANSI_NULLS имеет значение OFF, при обработке выражения NULL = NULL будет возвращено TRUE.  
  
 Выражения с **логическое** типы данных используются в предложении WHERE для фильтрации строк, удовлетворяющих условиям поиска и в инструкциях языка управления потоком таких как IF и WHILE, например:  
  
```  
-- Uses AdventureWorks  
  
DECLARE @MyProduct int;  
SET @MyProduct = 750;  
IF (@MyProduct <> 0)  
   SELECT ProductID, Name, ProductNumber  
   FROM Production.Product  
   WHERE ProductID = @MyProduct;  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  

