---
title: COMPRESS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 51324f00da71597a8a2dd37d8f0077c4b3bc8b55
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="compress-transact-sql"></a>COMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Сжимает входное выражение с использованием алгоритма GZIP. Результатом сжатия является массив байтов типа **varbinary(max)**.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*expression*  
Выражение типа **nvarchar(***n***)**, **nvarchar(max)**, **varchar(***n***)**, **varchar(max)**, **varbinary(***n***)**, **varbinary(max)**, **char(***n***)**, **nchar(***n***)** или **binary(***n***)**. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="return-types"></a>Типы возвращаемых данных
Возвращает сжатое содержимое входного выражения, которое имеет тип данных **varbinary(max)**.
  
## <a name="remarks"></a>Remarks  
Сжатые данные невозможно индексировать.
  
Функция COMPRESS сжимает данные, предоставленные во входном выражении, и должна вызываться для каждого раздела сжимаемых данных. Сведения об автоматическом сжатии хранимых данных на уровне строк или страниц см. в статье [Сжатие данных](../../relational-databases/data-compression/data-compression.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. Сжатие данных во время вставки в таблицу  
В приведенном ниже примере показано, как сжать данные, вставляемые в таблицу.
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>Б. Архивация сжатой версии удаленных строк  
Приведенная ниже инструкция удаляет старые записи игроков из таблицы `player` и сохраняет их в таблице `inactivePlayer` в сжатой форме для экономии места.
  
```sql
DELETE player  
WHERE datemodified < @startOfYear  
OUTPUT id, name, surname datemodifier, COMPRESS(info)   
INTO dbo.inactivePlayers ;  
```  
  
## <a name="see-also"></a>См. также раздел
[Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[DECOMPRESS (Transact-SQL)](../../t-sql/functions/decompress-transact-sql.md)
  
  
