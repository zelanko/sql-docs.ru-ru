---
title: "Функция TRIM (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TRIM
- TRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 88ba00513a8f76ae560ed717801150aa9b80046e
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="trim-transact-sql"></a>Функция TRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Удаляет символ пробела `char(32)` или другие указанные символы из начала и конца строки.  
 
## <a name="syntax"></a>Синтаксис   
```
TRIM ( [ characters FROM ] string ) 
```
[//]: # "[ОБА | НАЧАЛЬНЫЕ | В КОНЦЕ] не еще доступны."

## <a name="arguments"></a>Аргументы   

Символы   
Литерал, переменной или вызов функции любого типа не LOB (`nvarchar`, `varchar`, `nchar`, или `char`) содержит символы, которые должны быть удалены. `nvarchar(max)`и `varchar(max)` типами не допускается.

строка   
Выражение любого типа (`nvarchar`, `varchar`, `nchar`, или `char`) где необходимо удалить символы.

## <a name="return-types"></a>Типы возвращаемых значений   
Возвращает символьное выражение с типом аргумента-строки, где символ пробела `char(32)` или другие указанные символы удаляются из обеих сторон. Возвращает `NULL` Если входная строка `NULL`.

## <a name="remarks"></a>Remarks   
По умолчанию `TRIM` функция удаляет символ пробела `char(32)` с обеих сторон. Это равносильно `LTRIM(RTRIM(@string))`. Поведение `TRIM ` функцию с указанные символы идентична поведение `REPLACE` функции, где символов из начала или конца заменяются пустые строки.


## <a name="examples"></a>Примеры
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Удаляет символ пробела с обеих сторон строки   
Следующий пример удаляет пробелы до и после слова `test`.   
```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>Б.  Удаляет указанные символы с обеих сторон строки   
В следующем примере удаляется конечные точки и конечные пробелы.
```sql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>См. также
 [Левый &#40; Transact-SQL &#41;](../../t-sql/functions/left-transact-sql.md)  
 [Функция LTRIM &#40; Transact-SQL &#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [ПРАВО &#40; Transact-SQL &#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40; Transact-SQL &#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40; Transact-SQL &#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [ПОДСТРОКА &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
