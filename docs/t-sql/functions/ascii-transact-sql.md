---
title: "ASCII (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
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
- ASCII_TSQL
- ASCII
dev_langs: TSQL
helpviewer_keywords:
- ASCII function
- characters [SQL Server], ASCII
- code [SQL Server], ASCII
- leftmost character of expression
ms.assetid: 45c2044a-0593-4805-8bae-0fad4bde2e6b
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b933f33b8eb6b3909eaf7cb0afcd8bfe19862dee
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="ascii-transact-sql"></a>ASCII (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает код ASCII первого символа указанного символьного выражения.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ASCII ( character_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*character_expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа **char** или **varchar**.
  
## <a name="return-types"></a>Возвращаемые типы
 **int**  
  
## <a name="remarks"></a>Remarks
ASCII-это сокращение для американский стандартный код для обмена сведения. Это кодировка — это стандарт, используемый компьютерами. Список символов ASCII, в разделе **печатаемые символы** раздел [ASCII](https://www.wikipedia.org/wiki/ASCII).

## <a name="examples"></a>Примеры  
В следующем примере предполагается набор символов ASCII и возвращает `ASCII` значение 6 символов.
  
```sql
SELECT ASCII('A') AS A, ASCII('B') AS B,   
ASCII('a') AS a, ASCII('b') AS b,  
ASCII(1) AS [1], ASCII(2) AS [2];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
A           B           a           b           1           2  
----------- ----------- ----------- ----------- ----------- -----------  
65          66          97          98          49          50  
```  
  
## <a name="see-also"></a>См. также:
 [ДИА &#40; Transact-SQL &#41;](../../t-sql/functions/char-transact-sql.md)  
 [NCHAR &#40; Transact-SQL &#41;](../../t-sql/functions/nchar-transact-sql.md)  
 [Юникод &#40; Transact-SQL &#41;](../../t-sql/functions/unicode-transact-sql.md)  
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)
  
  


