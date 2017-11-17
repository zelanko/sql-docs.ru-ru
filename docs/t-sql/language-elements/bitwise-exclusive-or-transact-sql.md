---
title: "^ (Побитовое исключающее или) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ^_TSQL
- Bitwise Exclusive OR
- Exclusive
- ^
- bitwise
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- OR operator
- exclusive OR mathematical operations
- bitwise exclusive OR (^)
ms.assetid: f38f0ad4-46d0-40ea-9851-0f928fda5293
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 635cdf87939b15fad65ba4cc103166bff2ba04d2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="-bitwise-exclusive-or-transact-sql"></a>^ (побитовое исключающее ИЛИ) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Выполняет побитовую операцию исключающего ИЛИ между двумя целочисленными значениями.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression ^ expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) одного из типов данных из категории целочисленных типов данных или **бит**, или **двоичных** или **varbinary** типы данных. *выражение* рассматривается как двоичное число для побитовой операции.  
  
> [!NOTE]  
>  Только один *выражение* может иметь **двоичных** или **varbinary** тип данных в побитовой операции.  
  
## <a name="result-types"></a>Типы результата  
 **int** Если входные значения имеют **int**.  
  
 **smallint** Если входные значения имеют **smallint**.  
  
 **tinyint** Если входные значения имеют **tinyint**.  
  
## <a name="remarks"></a>Замечания  
  **^**  Побитовый оператор выполняет операцию побитового логического исключающего или между двумя выражениями, последовательно обрабатывая соответствующие биты для двух выражений. Значение результирующих битов устанавливается равным 1, если для текущего разрешаемого бита один из битов (но не оба) во входных выражениях имеет значение 1. Если оба бита имеют равные значения, результирующий бит принимает значение 0.  
  
 Если левое и правое выражения имеют разные целочисленные типы данных (например, влево *выражение* — **smallint** и правом *выражение* —  **int**), аргумент более короткого типа данных преобразуется в тип данных большего размера. В этом случае **smallint***выражение* преобразуется в **int**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается таблица, использующая **int** тип для хранения оригинальных значений данных и два значения вставляются в одну строку.  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 В следующем запросе выполняется операция побитового исключающего ИЛИ над столбцами `a_int_value` и `b_int_value`.  
  
```  
SELECT a_int_value ^ b_int_value  
FROM bitwise;  
GO  
```  
  
 Результирующий набор:  
  
```  
-----------   
225           
  
(1 row(s) affected)  
```  
  
 Двоичное представление числа 170 (`a_int_value` или `A`) является `0000 0000 1010 1010`. Двоичное представление числа 75 (`b_int_value` или `B`) — `0000 0000 0100 1011`. При выполнении операции побитового исключающего ИЛИ над этими двумя значениями получается двоичный результат `0000 0000 1110 0001`, который является десятичным числом 225.  
  
```  
(A ^ B)     
         0000 0000 1010 1010  
         0000 0000 0100 1011  
         -------------------  
         0000 0000 1110 0001  
```  
  

  
## <a name="see-also"></a>См. также:  
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Побитовые операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [^ = &#40; Побитовое исключающее или равно &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)   
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  



