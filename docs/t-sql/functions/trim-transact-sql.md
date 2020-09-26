---
description: TRIM (Transact-SQL)
title: TRIM (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- TRIM
- TRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
author: julieMSFT
ms.author: jrasnick
monikerRange: = azure-sqldw-latest||=azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2c2110b541ad06770b1218e3e48e77056085eaeb
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2020
ms.locfileid: "91379529"
---
# <a name="trim-transact-sql"></a>TRIM (Transact-SQL)

[!INCLUDE [sqlserver2017-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2017-asdb-asdbmi-asa.md)]

Удаляет символ пробела `char(32)` или другие заданные символы в начале и конце строки.  

## <a name="syntax"></a>Синтаксис

```syntaxsql
-- Syntax for SQL Server and Azure SQL Database
TRIM ( [ characters FROM ] string )
```

```syntaxsql
-- Syntax for Azure Synapse Analytics
TRIM ( string )
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы

characters — литерал, переменная или вызов функции любого типа данных, отличного от типа большого объекта (`nvarchar`, `varchar`, `nchar` или `char`), которые содержат удаляемые символы. Типы `nvarchar(max)` и `varchar(max)` не допускаются.

string — выражение любого символьного типа (`nvarchar`, `varchar`, `nchar` или `char`), из которого следует удалить символы.

## <a name="return-types"></a>Типы возвращаемых данных

Возвращает символьное выражение с типом аргумента string, в котором символ пробела `char(32)` или другие заданные символы удалены с обеих сторон. Возвращает `NULL`, если входная строка равна `NULL`.

## <a name="remarks"></a>Комментарии

По умолчанию функция `TRIM` удаляет символ пробела как в начале, так и в конце строки. Такая реакция на событие эквивалентна `LTRIM(RTRIM(@string))`.

## <a name="examples"></a>Примеры

### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Удаление символа пробела с обеих сторон строки

В приведенном ниже примере удаляются пробелы перед словом `test` и после него.

```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

```
test
```

### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>Б.  Удаление указанных символов с обеих сторон строки

В приведенном ниже примере удаляется конечная точка, а также пробелы перед символом `#` и после слова `test`.

```sql
SELECT TRIM( '.,! ' FROM  '     #     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
#     test
```

## <a name="see-also"></a>См. также:

- [LEFT (Transact-SQL)](../../t-sql/functions/left-transact-sql.md)  
- [LTRIM (Transact-SQL)](../../t-sql/functions/ltrim-transact-sql.md)  
- [RIGHT (Transact-SQL)](../../t-sql/functions/right-transact-sql.md)  
- [RTRIM (Transact-SQL)](../../t-sql/functions/rtrim-transact-sql.md)  
- [STRING_SPLIT (Transact-SQL)](../../t-sql/functions/string-split-transact-sql.md)  
- [SUBSTRING (Transact-SQL)](../../t-sql/functions/substring-transact-sql.md)  
- [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)
