---
title: DECOMPRESS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/30/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords:
- DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2d2b965d3177be06b46bb51b8f5238f5a4b21dee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="decompress-transact-sql"></a>DECOMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Распаковывает входное выражение с использованием алгоритма GZIP. Результатом сжатия является массив байтов (типа VARBINARY(MAX)).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DECOMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Выражение типа **varbinary(***n***)**, **varbinary(max)** или **binary(***n***)**. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает тип данных **varbinary(max)**. Входной аргумент распаковывается с использованием алгоритма ZIP. Пользователю необходимо явно привести результат к требуемому конечному типу.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-decompress-data-at-query-time"></a>A. Распаковка данных во время выполнения запроса  
 В приведенном ниже примере показано, как сжать данные в таблице.  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>Б. Отображение сжатых данных с помощью вычисляемого столбца  
 В приведенном ниже примере показано создание таблицы для хранения распакованных данных.  
  
```  
CREATE TABLE (  
    _id int primary key identity,  
    name nvarchar(max),  
    surname nvarchar(max),  
    info varbinary(max),  
    info_json as CAST(decompress(info) as nvarchar(max))  
);  
```  
  
## <a name="see-also"></a>См. также:  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
 [COMPRESS (Transact-SQL)](../../t-sql/functions/compress-transact-sql.md)  
  
  
