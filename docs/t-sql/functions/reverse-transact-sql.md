---
title: "REVERSE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERSE_TSQL
- REVERSE
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], reverse
- REVERSE function
- reverse character expressions
ms.assetid: 555d8877-7cc7-4955-ae2c-6215aca313b7
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 86c7d027057c851ae52d3627aa5ff2591f95bf8a
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="reverse-transact-sql"></a>REVERSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строковое значение, где символы переставлены в обратном порядке справа налево.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
REVERSE ( string_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *String_Expression*  
 *String_Expression* — [выражение](../../t-sql/language-elements/expressions-transact-sql.md) строкового или двоичного типа данных. *String_Expression* может быть константой, переменной или столбцом символьных или двоичных данных.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varchar** или **nvarchar**  
  
## <a name="remarks"></a>Замечания  
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
  
## <a name="see-also"></a>См. также:  
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


