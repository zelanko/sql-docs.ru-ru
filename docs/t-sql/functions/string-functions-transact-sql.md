---
title: Строковые функции (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/15/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], strings
- strings [SQL Server], functions
- string functions
- strings [SQL Server]
ms.assetid: 6940a83d-5374-4af3-bb27-5d89c8af83ac
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 562db45e1edfee521bed91b7a4137cd0bf6fa7b0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67906846"
---
# <a name="string-functions-transact-sql"></a>Строковые функции (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Следующие скалярные функции выполняют операции над входным строковым значением и возвращают строковое или числовое значение:  
  
||||  
|-|-|-| 
|[ASCII](../../t-sql/functions/ascii-transact-sql.md)|[CHAR](../../t-sql/functions/char-transact-sql.md)|[CHARINDEX](../../t-sql/functions/charindex-transact-sql.md)|
|[CONCAT](../../t-sql/functions/concat-transact-sql.md)|[CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md)|[DIFFERENCE](../../t-sql/functions/difference-transact-sql.md) |
|[FORMAT](../../t-sql/functions/format-transact-sql.md)|[LEFT](../../t-sql/functions/left-transact-sql.md)|[LEN](../../t-sql/functions/len-transact-sql.md) |
|[LOWER](../../t-sql/functions/lower-transact-sql.md)|[LTRIM](../../t-sql/functions/ltrim-transact-sql.md)|[NCHAR](../../t-sql/functions/nchar-transact-sql.md) |
|[PATINDEX](../../t-sql/functions/patindex-transact-sql.md)|[QUOTENAME](../../t-sql/functions/quotename-transact-sql.md)|[REPLACE](../../t-sql/functions/replace-transact-sql.md) |
|[REPLICATE](../../t-sql/functions/replicate-transact-sql.md)|[REVERSE](../../t-sql/functions/reverse-transact-sql.md) |[RIGHT](../../t-sql/functions/right-transact-sql.md) |
|[RTRIM](../../t-sql/functions/rtrim-transact-sql.md)|[SOUNDEX](../../t-sql/functions/soundex-transact-sql.md) |[SPACE](../../t-sql/functions/space-transact-sql.md) |
|[STR](../../t-sql/functions/str-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|[STRING_ESCAPE](../../t-sql/functions/string-escape-transact-sql.md) |
|[STRING_SPLIT](../../t-sql/functions/string-split-transact-sql.md)|[STUFF](../../t-sql/functions/stuff-transact-sql.md)|[SUBSTRING](../../t-sql/functions/substring-transact-sql.md) |
|[TRANSLATE](../../t-sql/functions/translate-transact-sql.md)|[TRIM](../../t-sql/functions/trim-transact-sql.md)|[UNICODE](../../t-sql/functions/unicode-transact-sql.md) |
|[UPPER](../../t-sql/functions/upper-transact-sql.md) | | |


  
 Все встроенные строковые функции, кроме `FORMAT`, являются детерминированными. Это значит, что они каждый раз возвращают одинаковое значение для одинакового набора входных параметров. Дополнительные сведения о детерминированности функций см. в статье [Детерминированные и недетерминированные функции](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
 При передаче в строковые функции аргументов, которые не являются строковыми значениями, входной тип неявно преобразуется в текстовый тип данных. Дополнительные сведения см. в статье [Преобразование типов данных (ядро СУБД)](../../t-sql/data-types/data-type-conversion-database-engine.md).  
  
## <a name="see-also"></a>См. также:  
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  

