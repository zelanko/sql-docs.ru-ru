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
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- operators [Transact-SQL], bitwise
- bitwise operators
- bit manipulations
ms.assetid: 2b994cf5-2daa-438a-b8c7-4bd8d451ac8d
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: b0706080c0a878987fab8d2cc5f0c1677f43309b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
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
* [& &#40; Побитовое и &#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md)  
* [& = &#40; Присваивание побитового и &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
* [&#124; &#40; Побитовый оператор или &#41;](../../t-sql/language-elements/bitwise-or-transact-sql.md)  
* [&#124; = &#40; Побитовый оператор или назначения &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
* [^ &#40; Побитовое исключающее или &#41;](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md)  
* [^ = &#40; Побитовое исключающее или назначения &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)  
* [~ &#40; Побитовый оператор не &#41;](../../t-sql/language-elements/bitwise-not-transact-sql.md)  
  
 Операнды побитовых операторов могут быть любым типом данных integer или двоичная строка категории типов данных (за исключением **изображения** тип данных), за исключением того, что оба операнда не может быть любым типом данных двоичной строки категории типов данных. Следующая таблица показывает поддерживаемые типы данных операндов.  
  
|Левый операнд|Правый операнд|  
|------------------|-------------------|  
|[binary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint**, или **tinyint**|  
|[бит](../../t-sql/data-types/bit-transact-sql.md)|**int**, **smallint**, **tinyint**, или **бит**|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **двоичных**, или **varbinary**|  
|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **двоичных**, или **varbinary**|  
|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **двоичных**, или **varbinary**|  
|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint**, или **tinyint**|  
  
## <a name="see-also"></a>См. также  
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
  
