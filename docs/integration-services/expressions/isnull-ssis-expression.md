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
ms.openlocfilehash: c5248919a2944ad81b06883b1a0aa01a64676b98
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71297533"
---
# <a name="isnull-ssis-expression"></a>ISNULL (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
  
