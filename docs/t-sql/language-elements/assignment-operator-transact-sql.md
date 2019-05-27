---
title: = (оператор присваивания) (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 144185dfc0ce2a4318b29b2526bdba51ceb046ab
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980597"
---
# <a name="-assignment-operator-transact-sql"></a>= (оператор присваивания) (Transact-SQL)
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
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [Составные операторы (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
