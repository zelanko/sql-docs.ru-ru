---
title: "QUOTENAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- QUOTENAME_TSQL
- QUOTENAME
dev_langs: TSQL
helpviewer_keywords:
- delimited identifiers [SQL Server]
- input strings [SQL Server]
- Unicode [SQL Server], delimited identifiers
- QUOTENAME function
- valid identifiers [SQL Server]
ms.assetid: 34d47f1e-2ac7-4890-8c9c-5f60f115e076
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 701d229ae745cee4a237f35b69cd00e899d5c6a5
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="quotename-transact-sql"></a>QUOTENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает Юникод-строку с разделителями, образуя из строки ввода правильный идентификатор с разделителем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
QUOTENAME ( 'character_string' [ , 'quote_character' ] )   
```  
  
## <a name="arguments"></a>Аргументы  
 '*character_string*'  
 Строка символьных данных в Юникоде. *character_string* — **sysname** и не должна превышать 128 символов. Если ввести более 128 символов, будет возвращено значение NULL.  
  
 "*значение аргумента quote_character*"  
 Односимвольная строка, используемая в качестве разделителя. Может быть одинарной кавычки ( **"** ), левую или правую скобку ( **[]** ), или двойной кавычкой ( **»** ). Если *значение аргумента quote_character* не указан, используются скобки.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(258)**  
  
## <a name="examples"></a>Примеры  
 В следующем примере из строки `abc[]def` и символов `[` и `]` создается правильный идентификатор с разделителем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT QUOTENAME('abc[]def');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc[]]def]  
  
(1 row(s) affected)  
```  
  
 Обратите внимание, что закрывающая квадратная скобка в строке `abc[]def` удвоена, чтобы указать на escape-символ.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере из строки `abc def` и символов `[` и `]` создается правильный идентификатор с разделителем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT QUOTENAME('abc def');   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc def]  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также  
 [PARSENAME &#40; Transact-SQL &#41;](../../t-sql/functions/parsename-transact-sql.md)  
 [CONCAT &#40; Transact-SQL &#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [Функция FORMATMESSAGE &#40; Transact-SQL &#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [Заменить &#40; Transact-SQL &#41;](../../t-sql/functions/replace-transact-sql.md)  
 [ОБРАТИТЬ &#40; Transact-SQL &#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40; Transact-SQL &#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40; Transact-SQL &#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [ПРЕОБРАЗОВАТЬ &#40; Transact-SQL &#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

