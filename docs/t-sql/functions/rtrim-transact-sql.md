---
title: "RTRIM (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/05/2017
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
- RTRIM_TSQL
- RTRIM
dev_langs: TSQL
helpviewer_keywords:
- RTRIM function
- character strings [SQL Server], trailing blanks
- blank characters [SQL Server]
- trailing blanks
ms.assetid: 52fd6e8d-650c-4f66-abcf-67765aa5aa83
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: f2b2725ce59ea577180732bdbd44a1a7a1ed5089
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="rtrim-transact-sql"></a>RTRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает символьную строку, удаляя все завершающие пробелы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
RTRIM ( character_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных данных. *character_expression* может быть константой, переменной или столбцом символьных или двоичных данных.  
  
 *character_expression* должен иметь тип данных, который неявно преобразуется в **varchar**. В противном случае используйте [ПРИВЕДЕНИЯ](../../t-sql/functions/cast-and-convert-transact-sql.md) для явного преобразования *character_expression*.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varchar** или **nvarchar**  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example"></a>A. Простой пример  
 Следующий пример получает строку символов с пробелами в конце предложения и возвращает текст без пробелов в конце предложения.  
  
```  
SELECT RTRIM('Removes trailing spaces.   ');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
  `Removes trailing spaces.`  
  
### <a name="b-simple-example"></a>Б. простой пример  
 В следующем примере демонстрируется использование `RTRIM` для удаления конечных пробелов. Существует в настоящее время является другой строкой, объединенные в конец первой строки для отображения удалены пробелы.  
  
```  
SELECT RTRIM('Four spaces are after the period in this sentence.    ') + 'Next string.';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
`Four spaces are after the period in this sentence.Next string.`  

### <a name="c-using-rtrim-with-a-variable"></a>В. Использование RTRIM с переменной  
 Следующий пример демонстрирует, как использовать `RTRIM` для удаления конечных пробелов из символьной переменной.  
  
```  
DECLARE @string_to_trim varchar(60);  
SET @string_to_trim = 'Four spaces are after the period in this sentence.    ';  
SELECT @string_to_trim + ' Next string.';  
SELECT RTRIM(@string_to_trim) + ' Next string.';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```sql   
 -------------------------------------------------------------------------  
 Four spaces are after the period in this sentence.     Next string.  
 
 (1 row(s) affected)`  
 
 -------------------------------------------------------------------------  
 Four spaces are after the period in this sentence. Next string.  
 
 (1 row(s) affected)
 ```  
  

  
## <a name="see-also"></a>См. также  
 [Левый &#40; Transact-SQL &#41;](../../t-sql/functions/left-transact-sql.md)  
 [Функция LTRIM &#40; Transact-SQL &#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [ПРАВО &#40; Transact-SQL &#41;](../../t-sql/functions/right-transact-sql.md)  
 [STRING_SPLIT &#40; Transact-SQL &#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [ПОДСТРОКА &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
 [Функция TRIM &#40; Transact-SQL &#41;](../../t-sql/functions/trim-transact-sql.md)  
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


