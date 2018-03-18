---
title: "TRIM (Transact-SQL) | Документы Майкрософт"
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
# <a name="trim-transact-sql"></a>TRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Удаляет символ пробела `char(32)` или другие заданные символы в начале или конце строки.  
 
## <a name="syntax"></a>Синтаксис   
```
TRIM ( [ characters FROM ] string ) 
```
[//]: # "[ BOTH | LEADING | TRAILING ] пока не доступно."

## <a name="arguments"></a>Аргументы   

characters   
Литерал, переменная или вызов функции любого типа данных, отличного от типа большого объекта (`nvarchar`, `varchar`, `nchar` или `char`), которые содержат удаляемые символы. Типы `nvarchar(max)` и `varchar(max)` не допускаются.

строка   
Выражение любого символьного типа (`nvarchar`, `varchar`, `nchar` или `char`), из которого следует удалить символы.

## <a name="return-types"></a>Типы возвращаемых значений   
Возвращает символьное выражение с типом аргумента string, в котором символ пробела `char(32)` или другие заданные символы удалены с обеих сторон. Возвращает `NULL`, если входная строка равна `NULL`.

## <a name="remarks"></a>Remarks   
По умолчанию функция `TRIM` удаляет символ пробела `char(32)` с обеих сторон. Это равносильно `LTRIM(RTRIM(@string))`. Поведение функции `TRIM ` с заданными символами идентично поведению функции `REPLACE`, которая заменяет символы в начале или конце строки пустыми строками.


## <a name="examples"></a>Примеры
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Удаление символа пробела с обеих сторон строки   
В приведенном ниже примере удаляются пробелы перед словом `test` и после него.   
```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>Б.  Удаление указанных символов с обеих сторон строки   
В приведенном ниже примере удаляются конечная точка и конечные пробелы.
```sql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>См. также:
 [LEFT (Transact-SQL)](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM (Transact-SQL)](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT (Transact-SQL)](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM (Transact-SQL)](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT (Transact-SQL)](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING (Transact-SQL)](../../t-sql/functions/substring-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
