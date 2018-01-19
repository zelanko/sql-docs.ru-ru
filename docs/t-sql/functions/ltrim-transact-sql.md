---
title: "LTRIM (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 02/27/2017
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
- LTRIM
- LTRIM_TSQL
dev_langs: TSQL
helpviewer_keywords:
- leading blanks
- deleting blank spaces
- characters [SQL Server], blanks
- removing blank spaces
- LTRIM function
- blank characters [SQL Server]
ms.assetid: 369ed340-1a09-4597-a9eb-6720156cd39a
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 1f73f29131ad94037c5dce500d3877567dedef8f
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="ltrim-transact-sql"></a>LTRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает символьное выражение после удаления начальных пробелов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
LTRIM ( character_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных или двоичных данных. *character_expression* может быть константой, переменной или столбцом. *character_expression* должен иметь тип данных, за исключением **текст**, **ntext**, и **изображения**, в котором могут быть неявно преобразованы **varchar** . В противном случае используйте [ПРИВЕДЕНИЯ](../../t-sql/functions/cast-and-convert-transact-sql.md) для явного преобразования *character_expression*.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **varchar** или **nvarchar**  
  
## <a name="examples"></a>Примеры  

### <a name="a-simple-example"></a>A. Простой пример   

 В следующем примере функция LTRIM используется для удаления начальных пробелов в символьное выражение.  
  
```sql  
SELECT LTRIM('     Five spaces are at the beginning of this string.') FROM sys.databases;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ---------------------------------------------------------------  
  Five spaces are at the beginning of this string.
  ```  

### <a name="b-example-using-a-variable"></a>Б. пример использования переменной   
  
 Следующий пример использует `LTRIM` для удаления начальных пробелов из символьной переменной.  
  
```  
DECLARE @string_to_trim varchar(60);  
SET @string_to_trim = '     5 spaces are at the beginning of this string.';  
SELECT 
    @string_to_trim AS 'Original string',
    LTRIM(@string_to_trim) AS 'Without spaces';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Original string Without spaces
--------------------------------------------------- ---------------------------------------------
     5 spaces are at the beginning of this string.  5 spaces are at the beginning of this string.
```  
  
## <a name="see-also"></a>См. также  
 [Левый &#40; Transact-SQL &#41;](../../t-sql/functions/left-transact-sql.md)  
 [ПРАВО &#40; Transact-SQL &#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40; Transact-SQL &#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40; Transact-SQL &#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [ПОДСТРОКА &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
 [Функция TRIM &#40; Transact-SQL &#41;](../../t-sql/functions/trim-transact-sql.md)  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


