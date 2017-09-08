---
title: "Оператор присваивания (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- operators [Transact-SQL], assignment
- assignment operators [Transact-SQL]
- headings [SQL Server columns]
- relationships [SQL Server], assignment operators
- column headings [SQL Server]
ms.assetid: c3040db6-21d6-40ac-a783-82c98ec006cc
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d10872712d1b7114655b5d95ab9b871709c55b14
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="assignment-operator-transact-sql"></a>Операторы присваивания (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Знак равенства (=) является единственным оператором присваивания в языке [!INCLUDE[tsql](../../includes/tsql-md.md)]. В следующем примере создается переменная `@MyCounter`, а затем оператор присваивания устанавливает `@MyCounter` в значение выражения.  
  
```  
DECLARE @MyCounter INT;  
SET @MyCounter = 1;  
```  
  
 Оператор присваивания может также использоваться для установления связи между заголовком столбца и выражением, которое определяет значение для столбца. Следующий пример отображает заголовки столбцов `FirstColumnHeading` и `SecondColumnHeading`. Строка `xyz` выводится в заголовке столбца `FirstColumnHeading` для всех строк. Затем все коды продуктов из таблицы `Product` перечисляются в заголовке столбца `SecondColumnHeading`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstColumnHeading = 'xyz',  
       SecondColumnHeading = ProductID  
FROM Production.Product;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
