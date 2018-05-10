---
title: ISNULL (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1c2a5d1aba0c43da67be572e0981d75add581642
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE (Transact-SQL)](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  
