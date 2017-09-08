---
title: "COMPRESS (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c30cb5f351d9a84beec608483380edb94b8c7844
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="compress-transact-sql"></a>COMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Сжимает входное выражение с применением алгоритма GZIP. Результат сжатия — массив байтов типа **varbinary(max)**.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*expression*  
— **Nvarchar (***n***)**, **nvarchar(max)**, **varchar (**  *n*  **)**, **varchar(max)**, **varbinary (**  *n*  **)**, **varbinary(max)**, **char (***n***)**, **nchar ()**   *n*  **)**, или **двоичный (***n***)** выражение. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="return-types"></a>Возвращаемые типы
Возвращает тип данных **varbinary(max)** , представляющий сжатое содержимое входных данных.
  
## <a name="remarks"></a>Замечания  
Невозможно индексировать сжатых данных.
  
Этой функции COMPRESS сжимает данные, предоставленные в качестве входного выражения и должен быть вызван для каждого раздела данных будет сжат. Автоматическое сжатие на уровне строк или страниц во время хранения в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. Сжатие данных во время вставки таблицы  
В следующем примере показано, как для сжатия данных, вставляемых в таблицу:
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>Б. Сжатая версия архив удаленных строк  
Следующая инструкция удаляет старые записи проигрывателя из `player` таблицы и сохраняет записи в `inactivePlayer` таблицы в сжатом формате для экономии места.
  
```sql
DELETE player  
WHERE datemodified < @startOfYear  
OUTPUT id, name, surname datemodifier, COMPRESS(info)   
INTO dbo.inactivePlayers ;  
```  
  
## <a name="see-also"></a>См. также:
[Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
[РАСПАКОВКА &#40; Transact-SQL &#41;](../../t-sql/functions/decompress-transact-sql.md)
  
  

