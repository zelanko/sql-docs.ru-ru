---
title: "| (Побитовый оператор или) (Transact-SQL) | Документы Microsoft"
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
- '|'
- '|_TSQL'
- Bitwise OR
- bitwise
- OR
dev_langs: TSQL
helpviewer_keywords:
- OR operator
- bitwise OR (|)
- '| (bitwise OR operator)'
ms.assetid: 86a3b87f-9688-4eaf-a552-29f1b01d880a
caps.latest.revision: "43"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 47d4b177e93d028ccf0afffec6a9480928e11cb0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="-bitwise-or-transact-sql"></a>| (Побитовое ИЛИ) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Выполняет побитовую логическую операцию OR для двух указанных целочисленных значений, которые преобразуются в двоичные выражения в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```   
expression | expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) из категории целочисленных типов данных или **бит**, **двоичных**, или **varbinary** типов данных. *выражение* рассматривается как двоичное число для побитовой операции.  
  
> [!NOTE]  
>  Только один *выражение* может иметь **двоичных** или **varbinary** тип данных в побитовой операции.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает **int** Если входные значения имеют **int**, **smallint** Если входные значения имеют **smallint**, или **tinyint** Если входные значения имеют **tinyint**.  
  
## <a name="remarks"></a>Замечания  
 Побитовый оператор «|» выполняет логическую операцию OR над двумя выражениями, получая из них результат поразрядно. Каждый бит результата устанавливаются в 1, если хотя бы один из исходных битов равен 1. Если оба исходных бита равны 0, бит результата будет равен нулю.  
  
 Если левое и правое выражения имеют разные целочисленные типы данных (например, влево *выражение* — **smallint** и правом *выражение* —  **int**), аргумент более короткого типа данных преобразуется в тип данных большего размера. В этом примере **smallint***выражение* преобразуется в **int**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается таблица с **int** типы для отображения исходные значения данных и заполнение в одну строку.  
  
```tsql  
CREATE TABLE bitwise  
(   
 a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 Следующий запрос выполняет битовую операцию OR **a_int_value** и **b_int_value** столбцов.  
  
```  
SELECT a_int_value | b_int_value  
FROM bitwise;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
235           
  
(1 row(s) affected)  
```  
  
 Двоичное представление числа 170 (**a_int_value** или `A`ниже) — `0000 0000 1010 1010`. Двоичное представление числа 75 (**b_int_value** или `B`ниже) — `0000 0000 0100 1011`. При выполнении побитовой операции OR над этими двумя значениями получается двоичный результат `0000 0000 1110 1011`, что соответствует десятичному значению 235.  
  
```  
(A | B)  
0000 0000 1010 1010  
0000 0000 0100 1011  
-------------------  
0000 0000 1110 1011  
```  
  
## <a name="see-also"></a>См. также:  
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Побитовые операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [&#124; = &#40; Побитовый оператор или назначения &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


