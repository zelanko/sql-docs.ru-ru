---
title: "Функция TRIM (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 4
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 64cef84a613d71e65b33bed1c1e740dc59eeed9d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="trim-transact-sql"></a>Функция TRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

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

## <a name="remarks"></a>Замечания   
По умолчанию `TRIM` функция удаляет символ пробела `char(32)` с обеих сторон. Это равносильно `LTRIM(RTRIM(@string))`. Поведение `TRIM ` функцию с указанные символы идентична поведение `REPLACE` функции, где символов из начала или конца заменяются пустые строки.


## <a name="examples"></a>Примеры
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Удаляет символ пробела с обеих сторон строки   
Следующий пример удаляет пробелы до и после слова `test`.   
```tsql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>Б.  Удаляет указанные символы с обеих сторон строки   
В следующем примере удаляется конечные точки и конечные пробелы.
```tsql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>См. также:
[Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
[LTRIM (Transact-SQL)](../../t-sql/functions/ltrim-transact-sql.md)   
[RTRIM (Transact-SQL)](../../t-sql/functions/rtrim-transact-sql.md)   
[REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)   

