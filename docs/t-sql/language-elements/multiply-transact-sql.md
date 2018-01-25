---
title: "* (Умножение) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
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
- '*_TSQL'
- '*'
dev_langs: TSQL
helpviewer_keywords:
- '* (multiply operator)'
- multiplication [SQL Server]
- multiply operator (*)
ms.assetid: 34beb660-db19-46ca-ac90-2218471457bf
caps.latest.revision: "43"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 09bb6ed9095c7dd37aa73bdd165e78c83362fb4c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="-multiplication-transact-sql"></a>* (Умножение) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Умножает два выражения (арифметический оператор умножения).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) одного из типов данных числового типа данных, за исключением **datetime** и **smalldatetime** типов данных.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает результат типа данных аргумента с более высоким приоритетом. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере запрашивается идентификационный номер продукта, название, стоимость по прейскуранту и стоимость по новому прейскуранту для всех горных велосипедов из таблицы `Product`. Новая стоимость по прейскуранту вычисляется с помощью арифметического оператора `*` для умножения `ListPrice` на `1.15`.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID, Name, ListPrice, ListPrice * 1.15 AS NewPrice  
FROM Production.Product  
WHERE Name LIKE 'Mountain-%'  
ORDER BY ProductID ASC;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере извлекается имя и Фамилия сотрудников в `dimEmployee` таблицы, а затем вычисляет оплаты по `VacationHours` для каждого...  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, BaseRate * VacationHours AS VacationPay  
FROM DimEmployee  
ORDER BY lastName ASC;  
```  
  
## <a name="see-also"></a>См. также  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [&#42; = &#40; Присваивание умножения &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/multiply-equals-transact-sql.md)   
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


