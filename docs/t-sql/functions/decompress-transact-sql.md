---
title: DECOMPRESS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords:
- DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a4c4309a12f3db14af0d38f9e98e73b7e8c4e6b1
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396703"
---
# <a name="decompress-transact-sql"></a>DECOMPRESS (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

Эта функция распаковывает значение входного выражения с использованием алгоритма GZIP. `DECOMPRESS` возвращает массив байтов (тип VARBINARY(MAX)).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DECOMPRESS ( expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *expression*  
Значение **varbinary(** _n_ **)** , **varbinary(max)** или **binary(** _n_ **)** . Дополнительные сведения см. в статье [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых данных  
Значение типа данных **varbinary(max)** . Для распаковки входного аргумента `DECOMPRESS` использует алгоритм ZIP. При необходимости пользователю следует явно привести результат к требуемому конечному типу.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-decompress-data-at-query-time"></a>A. Распаковка данных во время выполнения запроса  
В этом примере показано возвращение сжатых данных таблицы.  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>Б. Отображение сжатых данных с помощью вычисляемого столбца  
В этом примере показано создание таблицы для хранения распакованных данных.  
  
```  
CREATE TABLE example_table (  
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
  
  
