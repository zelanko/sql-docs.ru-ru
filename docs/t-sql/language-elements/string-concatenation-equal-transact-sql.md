---
title: "+= (Объединение строк) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/07/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- concatenate strings
- string concatenation
- += (concatenate operator)
ms.assetid: 4aaeaab7-9b2b-48e0-8487-04ed672ebcb1
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7c557bcc1d3c2f314ce57e93701b11833f5a6fc6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="string-concatenation---equal-transact-sql"></a>Объединение строк — равно (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Объединяет две строки и присваивает строке результат этой операции. Например, если переменная @x равно 'Adventure', затем @x += 'Works' принимает исходное значение @x, добавляет в строку 'Works' и задает @x новое значение «AdventureWorks».  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
expression += expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого из символьных типов данных.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных, определенный для переменной.  
  
## <a name="remarks"></a>Замечания  
 ЗАДАТЬ @v1 += 'expression' эквивалентно SET @v1 = @v1 + ('expression'). Кроме того, ЗАДАТЬ @v1 = @v2 + @v3 + @v4 аналогичен НАБОРУ @v1 = (@v2 + @v3) + @v4.  
  
 Оператор += нельзя использовать без переменной. Например, следующий код вызывает ошибку:  
  
```  
SELECT 'Adventure' += 'Works'  
```  
  
## <a name="examples"></a>Примеры  
### <a name="a-concatenation-using--operator"></a>A. Объединение с помощью оператора +=
 В следующем примере выполняется объединение строк с помощью оператора `+=`.  
  
```  
DECLARE @v1 varchar(40);  
SET @v1 = 'This is the original.';  
SET @v1 += ' More text.';  
PRINT @v1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `This is the original. More text.`  
  
### <a name="b-order-of-evaluation-while-concatenating-using--operator"></a>Б. Порядок вычисления во время объединения с помощью оператора +=
Следующий пример Сцепляет несколько строк в одну длинную строку, а затем пытается вычислить длину окончательную строку. В этом примере демонстрируются правила заказа и усечение оценки, при использовании оператора объединения. 

```
DECLARE @x varchar(4000) = replicate('x', 4000)
DECLARE @z varchar(8000) = replicate('z',8000)
DECLARE @y varchar(max);
 
SET @y = '';
SET @y += @x + @z;
SELECT LEN(@y) AS Y; -- 8000
 
SET @y = '';
SET @y = @y + @x + @z;
SELECT LEN(@y) AS Y; -- 12000
 
SET @y = '';
SET @y = @y +(@x + @z);
SELECT LEN(@y) AS Y; -- 8000
-- or
SET @y = '';
SET @y = @x + @z + @y;
SELECT LEN(@y) AS Y; -- 8000
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Y       
 ------- 
 8000 
  
 (1 row(s) affected) 
  
    
 Y       
 ------- 
 12000 
  
 (1 row(s) affected) 

 Y       
 ------- 
 8000 
  
 (1 row(s) affected) 
  
 Y       
 ------- 
 8000 
  
 (1 row(s) affected)
  ```   
   
## <a name="see-also"></a>См. также:  
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [+= &#40; Добавить равно &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/add-equals-transact-sql.md)   
 [+ &#40; Объединение строк &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
  
  

