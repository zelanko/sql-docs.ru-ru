---
title: "~ (Побитовое не) (Transact-SQL) | Документы Microsoft"
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
- ~_TSQL
- bitwise
- NOT
- ~
- Bitwise NOT
dev_langs: TSQL
helpviewer_keywords:
- NOT keyword
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: 02da8016-f6c0-41ae-8d59-33eaa02bfc95
caps.latest.revision: "42"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5bd0f8234088fbb358740d5c9b4e753d9ecaa11d
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="-bitwise-not-transact-sql"></a>~ (побитовое НЕ) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Выполняет побитовую логическую операцию НЕ с целочисленным значением.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
~ expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) одного из типов данных из категории целочисленных типов данных, **бит**, или **двоичных** или **varbinary** данных типы. *выражение* рассматривается как двоичное число для побитовой операции.  
  
> [!NOTE]  
>  Только один *выражение* может иметь **двоичных** или **varbinary** тип данных в побитовой операции.  
  
## <a name="result-types"></a>Типы результата  
 **int** Если входные значения имеют **int**.  
  
 **smallint** Если входные значения имеют **smallint**.  
  
 **tinyint** Если входные значения имеют **tinyint**.  
  
 **бит** Если входные значения имеют **бит**.  
  
## <a name="remarks"></a>Remarks  
  **~**  Побитовый оператор выполняет побитовую логическую операцию не для *выражение*, обрабатывая последовательно каждый бит. Если *выражение* имеет значение 0, биты в результирующем наборе устанавливаются в 1; в противном случае в результате бит принимает значение 0. Другими словами, единицы меняются на нули, нули меняются на единицы.  
  
> [!IMPORTANT]  
>  При выполнении любого вида побитовой операции важна длина хранимого выражения, используемого в операции. Рекомендуется использование такого же количества битов при сохранении значений. Например, при сохранении десятичного значения 5 как **tinyint**, **smallint**, или **int** получаются значения, занимающие различное байтов: **tinyint** занимают 1 байт; **smallint** 2 байта и **int** 4 байта. Таким образом, выполняя битовую операцию на **int** десятичное значение может дать разные результаты по сравнению с помощью прямой двоичного или шестнадцатеричного представления, особенно в том случае, когда  **~**  () Побитовый оператор не) используется оператор. Побитовую операцию «НЕ» можно провести для более короткой переменной. В случае, когда переменная более короткого типа данных преобразуется в переменную более длинного типа данных, старшие 8 бит могут принять неожиданное значение. Рекомендуется явно преобразовать переменные более короткого типа данных в переменные более длинного типа, а затем выполнять операцию «НЕ».  
  
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
  
 В следующем запросе выполняется побитовая операция «НЕ» для столбцов `a_int_value` и `b_int_value`.  
  
```  
SELECT ~ a_int_value, ~ b_int_value  
FROM bitwise;  
```  
  
 Результирующий набор:  
  
```  
--- ---   
-171  -76   
  
(1 row(s) affected)  
```  
  
 Двоичное представление числа 170 (`a_int_value` или `A`) является `0000 0000 1010 1010`. Выполнение побитовой операции не на это значение дает двоичный результат `1111 1111 0101 0101`, который является десятичным числом -171. Двоичное представление числа 75: `0000 0000 0100 1011`. Выполнение побитовой операции «НЕ» дает результат `1111 1111 1011 0100`, который является десятичным числом -76.  
  
```  
 (~A)     
         0000 0000 1010 1010  
         -------------------  
         1111 1111 0101 0101  
(~B)     
         0000 0000 0100 1011  
         -------------------  
         1111 1111 1011 0100  
```  
  
 
## <a name="see-also"></a>См. также  
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Побитовые операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  


