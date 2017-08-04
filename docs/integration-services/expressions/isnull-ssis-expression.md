---
title: "ISNULL (выражение служб SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dd74ffbf491733826eef4cf61530e838033d7e3d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

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
 [Функции &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [ОБЪЕДИНЕННЫЙ &#40; Transact-SQL &#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  
