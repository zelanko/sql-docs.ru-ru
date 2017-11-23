---
title: "РАСПАКОВКА (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/30/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords: DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2988959b7ec3f9eccad74b752e7643f1e6675590
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="decompress-transact-sql"></a>РАСПАКОВКА (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Распакуйте входное выражение с помощью алгоритма GZIP. Результат сжатия — массив байтов (тип VARBINARY(MAX)).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DECOMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 — **Varbinary (***n***)**, **varbinary(max)**, или **двоичный (** *n***)**. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает тип данных **varbinary(max)** типа. Входной аргумент сжата с помощью алгоритма ZIP. Пользователь должен явно приведен результат для типа целевого объекта, при необходимости.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-decompress-data-at-query-time"></a>A. Распаковка данных во время выполнения запроса  
 Приведенный ниже показан способ отображения сжатие данных из таблицы.  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>Б. Отображение сжатых данных, с помощью вычисляемого столбца  
 Следующий пример показывает создание таблицы для хранения распакованных данных:  
  
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
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [СЖАТИЕ &#40; Transact-SQL &#41;](../../t-sql/functions/compress-transact-sql.md)  
  
  
