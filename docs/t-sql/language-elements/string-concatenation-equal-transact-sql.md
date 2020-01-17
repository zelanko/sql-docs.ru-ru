---
title: += объединение строк
description: Объединяет две строки и присваивает строке результат этой операции.
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 12/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- concatenate strings
- string concatenation
- += (concatenate operator)
ms.assetid: 4aaeaab7-9b2b-48e0-8487-04ed672ebcb1
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dd21fb221076470d0c39194ea4c38d96af0f1056
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257052"
---
# <a name="-string-concatenation-assignment-transact-sql"></a>+= (присваивание объединения строк) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Объединяет две строки и присваивает строке результат этой операции. Например, если переменная @x имеет значение 'Adventure', то операция @x += 'Works' принимает исходное значение @x, добавляет к нему строку 'Works' и присваивает переменной @x новое значение ('AdventureWorks').  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
expression += expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого символьного типа данных.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных, определенный для переменной.  
  
## <a name="remarks"></a>Remarks  
 SET @v1 += 'expression' эквивалентно SET @v1 = @v1 + 'expression'. Кроме того, SET @v1 = @v2 + @v3 + @v4 эквивалентно SET @v1 = (@v2 + @v3) + @v4.  
  
 Оператор += нельзя использовать без переменной. Например, следующий код вызывает ошибку:  
  
```  
SELECT 'Adventure' += 'Works'  
```  
  
## <a name="examples"></a>Примеры  
### <a name="a-concatenation-using--operator"></a>A. Объединение с использованием оператора +=
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
В приведенном ниже примере выполняется объединение нескольких строк в одну длинную строку, а затем предпринимается попытка вычислить длину итоговой строки. В этом примере демонстрируются правила оценки и усечения при использовании оператора объединения. 

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
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [+= (присваивание сложения) (Transact-SQL)](../../t-sql/language-elements/add-equals-transact-sql.md)   
 [+ (объединение строк) (Transact-SQL)](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
  
  
