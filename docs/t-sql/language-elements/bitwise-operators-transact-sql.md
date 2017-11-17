---
title: "Побитовые операторы (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/07/2017
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
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], bitwise
- bitwise operators
- bit manipulations
ms.assetid: 2b994cf5-2daa-438a-b8c7-4bd8d451ac8d
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 05976158e43d7dfafaf02289462d1537f5beeb36
ms.openlocfilehash: 5d04924a82578040f801864bb68905feebc53e94
ms.contentlocale: ru-ru
ms.lasthandoff: 09/08/2017

---
# <a name="bitwise-operators-transact-sql"></a>побитовые операторы (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Побитовые операторы выполняют побитовые действия над двумя выражениями с любым типом данных, относящимся к категории типа данных integer.  
  Побитовые операторы преобразовать двух целочисленных значений в двоичных разрядов, выполнить и OR, или операцию не для каждого бита, формирование результата. Результат затем преобразуется в целое число.  
  
  Например 170 целое число преобразуется в двоичное 1010 1010.
75 целое число преобразуется в двоичное 0100 1011.

|оператор|Побитовое math|
|---- |---- |
|и <br> Если бит в любом месте равны 1, результат равен 1. |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 0000 1010 =  10 |
|или <br> Если в любом месте любой из битов равен 1, результат равен 1. |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 1110 1011 = 235|
|NOT  <br> Меняет значение бит в любом месте бит. |1010 1010 = 170 <br>----------------- <br>  0101 0101 =   85 |
  
В следующих разделах:   
* [& (Побитовое и)](../../t-sql/language-elements/bitwise-and-transact-sql.md)  
* [& = (побитовое и равно)](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
* [&#124; (Побитовый оператор или)](../../t-sql/language-elements/bitwise-or-transact-sql.md)  
* [&#124; = (равно с побитовым или)](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
* [^ (Побитовое исключающее или)](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md)  
* [^ = (Побитовое исключающее или равно)](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)  
* [~ (Побитовое не)](../../t-sql/language-elements/bitwise-not-transact-sql.md)  
  
 Операнды побитовых операторов могут быть любым типом данных integer или двоичная строка категории типов данных (за исключением **изображения** тип данных), за исключением того, что оба операнда не может быть любым типом данных двоичной строки категории типов данных. Следующая таблица показывает поддерживаемые типы данных операндов.  
  
|Левый операнд|Правый операнд|  
|------------------|-------------------|  
|[binary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint**, или **tinyint**|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|**int**, **smallint**, **tinyint**, или **бит**|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **двоичных**, или **varbinary**|  
|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **двоичных**, или **varbinary**|  
|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **двоичных**, или **varbinary**|  
|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint**, или **tinyint**|  
  
## <a name="see-also"></a>См. также:  
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

