---
title: "ISNULL (выражение служб SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e6ea60ae5d0c417b228619a3e177c3b9d0777369
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="isnull-ssis-expression"></a>ISNULL (выражение служб SSIS)
  Возвращает результат в виде логического выражения, в зависимости от того, имеет ли выражение значение NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Допустимое выражение любого типа данных.  
  
## <a name="result-types"></a>Типы результата  
 DT_BOOL  
  
## <a name="expression-examples"></a>Примеры выражений  
 Данный пример возвращает значение TRUE, если столбец **DiscontinuedDate** содержит значение NULL.  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 Данный пример возвращает «Unknown last name», если значение в столбце **LastName** равно NULL, в противном случае он возвращает значение из **LastName**.  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 Данный пример всегда возвращает значение TRUE, если столбец **DaysToManufacture** равен NULL, независимо от значения переменной в **AddDays**.  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a>См. также  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE (Transact-SQL)](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  
