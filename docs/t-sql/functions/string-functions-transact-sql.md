---
title: "Строковые функции (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/15/2016
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
- functions [SQL Server], strings
- strings [SQL Server], functions
- string functions
- strings [SQL Server]
ms.assetid: 6940a83d-5374-4af3-bb27-5d89c8af83ac
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 33df9a7082ee7e637b60e3a1ca7911e127040a08
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="string-functions-transact-sql"></a>Строковые функции (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Следующие скалярные функции выполняют операции над входным строковым значением и возвращают строковое или числовое значение:  
  
||||  
|-|-|-| 
|[ASCII](../../t-sql/functions/ascii-transact-sql.md)|[CHAR](../../t-sql/functions/char-transact-sql.md)|[CHARINDEX](../../t-sql/functions/charindex-transact-sql.md)|
|[CONCAT](../../t-sql/functions/concat-transact-sql.md)|[CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md)|[РАЗЛИЧИЕ](../../t-sql/functions/difference-transact-sql.md) |
|[ФОРМАТ](../../t-sql/functions/format-transact-sql.md)|[LEFT](../../t-sql/functions/left-transact-sql.md)|[LEN](../../t-sql/functions/len-transact-sql.md) |
|[НИЖЕ](../../t-sql/functions/lower-transact-sql.md)|[ФУНКЦИЯ LTRIM](../../t-sql/functions/ltrim-transact-sql.md)|[NCHAR](../../t-sql/functions/nchar-transact-sql.md) |
|[PATINDEX](../../t-sql/functions/patindex-transact-sql.md)|[QUOTENAME](../../t-sql/functions/quotename-transact-sql.md)|[REPLACE](../../t-sql/functions/replace-transact-sql.md) |
|[РЕПЛИЦИРОВАТЬ](../../t-sql/functions/replicate-transact-sql.md)|[REVERSE](../../t-sql/functions/reverse-transact-sql.md) |[RIGHT](../../t-sql/functions/right-transact-sql.md) |
|[RTRIM](../../t-sql/functions/rtrim-transact-sql.md)|[ФУНКЦИЯ SOUNDEX](../../t-sql/functions/soundex-transact-sql.md) |[ПРОБЕЛ](../../t-sql/functions/space-transact-sql.md) |
|[STR](../../t-sql/functions/str-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|[STRING_ESCAPE](../../t-sql/functions/string-escape-transact-sql.md) |
|[STRING_SPLIT](../../t-sql/functions/string-split-transact-sql.md)|[STUFF](../../t-sql/functions/stuff-transact-sql.md)|[SUBSTRING](../../t-sql/functions/substring-transact-sql.md) |
|[ПЕРЕВЕСТИ](../../t-sql/functions/translate-transact-sql.md)|[ФУНКЦИЯ TRIM](../../t-sql/functions/trim-transact-sql.md)|[UNICODE](../../t-sql/functions/unicode-transact-sql.md) |
|[ВЕРХНИЙ](../../t-sql/functions/upper-transact-sql.md) | | |


  
 Все встроенные строковые функции, за исключением `FORMAT` являются детерминированными. Это значит, что они каждый раз возвращают одинаковое значение для одинакового набора входных параметров. Дополнительные сведения о детерминизме функций см. в разделе [функций](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
 При передаче в строковые функции аргументов, которые не являются строковыми значениями, входной тип неявно преобразуется в текстовый тип данных. Дополнительные сведения см. в разделе [преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md).  
  
## <a name="see-also"></a>См. также:  
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  


