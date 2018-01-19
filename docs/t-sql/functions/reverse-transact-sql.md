---
title: "REVERSE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERSE_TSQL
- REVERSE
dev_langs: TSQL
helpviewer_keywords:
- expressions [SQL Server], reverse
- REVERSE function
- reverse character expressions
ms.assetid: 555d8877-7cc7-4955-ae2c-6215aca313b7
caps.latest.revision: "46"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: c14fb9f1e0f6e7b3f0cb224036af37e6a7b19e23
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="reverse-transact-sql"></a>REVERSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строковое значение, где символы переставлены в обратном порядке справа налево.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
REVERSE ( string_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *string_expression*  
 *String_Expression* — [выражение](../../t-sql/language-elements/expressions-transact-sql.md) строкового или двоичного типа данных. *String_Expression* может быть константой, переменной или столбцом символьных или двоичных данных.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varchar** или **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 *String_Expression* должен иметь тип данных, который неявно преобразуется в **varchar**. В противном случае используйте [ПРИВЕДЕНИЯ](../../t-sql/functions/cast-and-convert-transact-sql.md) для явного преобразования *string_expression*.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 При использовании параметров сортировки SC функция REVERSE не изменит порядок расположения символов суррогатной пары на обратный.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все имена из записной книжки (без фамилий), записанные в обратном порядке. В этом примере используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT FirstName, REVERSE(FirstName) AS Reverse  
FROM Person.Person  
WHERE BusinessEntityID < 5  
ORDER BY FirstName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FirstName      Reverse
-------------- --------------
Ken            neK
Rob            boR
Roberto        otreboR
Terri          irreT

(4 row(s) affected)
```  
  
 В следующем примере символы в переменной переставляются в обратном порядке.  
  
```  
DECLARE @myvar varchar(10);  
SET @myvar = 'sdrawkcaB';  
SELECT REVERSE(@myvar) AS Reversed ;  
GO  
```  
  
 В следующем примере происходит неявное преобразование из **int** в тип данных **varchar** тип данных и перестановка результата.  
  
```  
SELECT REVERSE(1234) AS Reversed ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере возвращаются имена всех баз данных и отменить имена с символами.  
  
```  
SELECT name, REVERSE(name) FROM sys.databases;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [CONCAT &#40; Transact-SQL &#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [Функция FORMATMESSAGE &#40; Transact-SQL &#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40; Transact-SQL &#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [Заменить &#40; Transact-SQL &#41;](../../t-sql/functions/replace-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40; Transact-SQL &#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40; Transact-SQL &#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [ПРЕОБРАЗОВАТЬ &#40; Transact-SQL &#41;](../../t-sql/functions/translate-transact-sql.md)  
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

