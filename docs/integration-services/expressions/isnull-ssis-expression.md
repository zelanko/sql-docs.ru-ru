---
title: ISNULL (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 15392de2f7a77edd0a4f43f2edc1346a52cd1a5e
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914554"
---
# <a name="isnull-ssis-expression"></a>ISNULL (выражение служб SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


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
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE (Transact-SQL)](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  
