---
title: "Составные операторы (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators
- compound operators, described
ms.assetid: 5072fe91-02d3-42a7-831f-756eff714a17
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 38aa65b196288c120dea5766fe29c64d58af0216
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="compound-operators-transact-sql"></a>Составные операторы (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Составные операторы выполняют определенные операции и задают исходной величине значение результата операции. Например, если переменная @x равно 35, @x += 2 принимает исходное значение @x, добавить 2 и задает @x новое значение (37).  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] поддерживает следующие составные операторы.  
  
|Оператор|Ссылка на дополнительные сведения|Действие|  
|--------------|------------------------------|------------|  
|+=|[+= &#40; Добавление назначения &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/add-equals-transact-sql.md)|Добавляет некоторое значение к исходному значению и задает исходной величине значение результата.|  
|-=|[-= &#40; Вычитание назначения &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/subtract-equals-transact-sql.md)|Вычитает определенное значение из исходного значения и задает исходной величине значение результата.|  
|*=|[&#42; = &#40; Умножьте назначения &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/multiply-equals-transact-sql.md)|Умножает исходное значение на определенное значение и задает исходной величине значение результата.|  
|/=|[&#40; присваивания деления &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)|Делит исходное значение на определенное значение и задает исходной величине значение результата.|  
|%=|[Назначение модуля &#40; Transact-SQL &#41;](../../t-sql/language-elements/modulo-equals-transact-sql.md)|Делит исходное значение на определенное значение и задает исходной величине значение остатка от деления.|  
|&=|[& = &#40; Присваивание побитового и &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)|Выполняет операцию побитового И и задает исходной величине значение результата.|  
|^=|[^ = &#40; Побитовое исключающее или назначения &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)|Выполняет операцию побитового исключающего ИЛИ и задает исходной величине значение результата.|  
|&#124;=|[&#124; = &#40; Побитовый оператор или назначения &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)|Выполняет операцию побитового исключающего И и задает исходной величине значение результата.|  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
expression operator expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) какой-либо один из данных типов в категории числовых данных.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает результат типа данных аргумента с более высоким приоритетом. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения см. в разделах, посвященных соответствующим операторам.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется использование составных операторов.  
  
```  
DECLARE @x1 int = 27;  
SET @x1 += 2 ;  
SELECT @x1 AS Added_2;  
  
DECLARE @x2 int = 27;  
SET @x2 -= 2 ;  
SELECT @x2 AS Subtracted_2;  
  
DECLARE @x3 int = 27;  
SET @x3 *= 2 ;  
SELECT @x3 AS Multiplied_by_2;  
  
DECLARE @x4 int = 27;  
SET @x4 /= 2 ;  
SELECT @x4 AS Divided_by_2;  
  
DECLARE @x5 int = 27;  
SET @x5 %= 2 ;  
SELECT @x5 AS Modulo_of_27_divided_by_2;  
  
DECLARE @x6 int = 9;  
SET @x6 &= 13 ;  
SELECT @x6 AS Bitwise_AND;  
  
DECLARE @x7 int = 27;  
SET @x7 ^= 2 ;  
SELECT @x7 AS Bitwise_Exclusive_OR;  
  
DECLARE @x8 int = 27;  
SET @x8 |= 2 ;  
SELECT @x8 AS Bitwise_OR;  
  
```  
  
## <a name="see-also"></a>См. также  
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Побитовые операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
