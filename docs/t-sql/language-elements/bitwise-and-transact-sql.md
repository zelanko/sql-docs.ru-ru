---
title: "&amp;(Побитовое и) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bitwise
- '&'
- '&_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 20275755-4fa7-47b1-a9be-ac85606d63b0
caps.latest.revision: "42"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0f81606a64480990a2f511a9820672c2cf1bb5c8
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="amp-bitwise-and-transact-sql"></a>&amp;(Побитовое и) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Выполняет побитовую логическую операцию «И» между двумя целочисленными значениями.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression & expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных из категории целочисленных типов данных или **бит**, или **двоичных** или **varbinary** данных типы. *выражение* рассматривается как двоичное число для побитовой операции.  
  
> [!NOTE]  
>  В побитовой операции только одно *выражение* может иметь **двоичных** или **varbinary** тип данных.  
  
## <a name="result-types"></a>Типы результата  
 **int** Если входные значения имеют **int**.  
  
 **smallint** Если входные значения имеют **smallint**.  
  
 **tinyint** Если входные значения имеют **tinyint** или **бит**.  
  
## <a name="remarks"></a>Remarks  
  **&**  Побитовый оператор выполняет побитовую логическую операцию и между двумя выражениями, последовательно обрабатывая соответствующие биты для двух выражений. Значение результирующих битов устанавливается равным 1 только в том случае, если оба бита (для текущего разрешаемого бита) в переданных выражениях имеют значение 1; в остальных случаях значение результирующего бита устанавливается равным 0.  
  
 Если левое и правое выражения имеют разные целочисленные типы данных (например, влево *выражение* — **smallint** и правом *выражение* —  **int**), аргумент более короткого типа данных преобразуется в тип данных большего размера. В этом случае **smallint *** выражение* преобразуется в **int**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается таблица, использующая **int** тип для хранения значений данных и два значения вставляются в одну строку.  
  
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
  
 В этом запросе побитовое И выполняется на столбцах `a_int_value` и `b_int_value`.  
  
```  
SELECT a_int_value & b_int_value  
FROM bitwise;  
GO  
```  
  
 Результирующий набор:  
  
```  
-----------   
10            
  
(1 row(s) affected)  
```  
  
 Двоичное представление числа 170 (`a_int_value` или `A`) является `0000 0000 1010 1010`. Двоичное представление числа 75 (`b_int_value` или `B`) — `0000 0000 0100 1011`. Выполнение побитовой операции И в отношении этих двух значений дает двоичный результат `0000 0000 0000 1010`, который имеет десятичное значение 10.  
  
```  
(A & B)  
0000 0000 1010 1010  
0000 0000 0100 1011  
-------------------  
0000 0000 0000 1010  
```  
  
  
## <a name="see-also"></a>См. также  
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Побитовые операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [& = &#40; Присваивание побитового и &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


