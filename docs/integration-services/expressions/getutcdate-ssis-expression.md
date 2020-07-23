---
title: GETUTCDATE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2ca0a021560dd99ec2ebdcd82c40255905cc0784
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86916998"
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (выражение служб SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Возвращает текущую дату системы в формате времени UTC (универсальное время, или время по Гринвичу), используя формат DT_DBTIMESTAMP. Функция GETUTCDATE не имеет аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>Аргументы  
 None  
  
## <a name="result-types"></a>Типы результата  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает год текущей даты времени в формате UTC.  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 Этот пример возвращает количество дней между датой в столбце **ModifiedDate** и текущей датой в формате UTC.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 Этот пример добавляет три месяца к текущей дате в формате UTC.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>См. также:  
 [GETDATE (выражение служб SSIS)](../../integration-services/expressions/getdate-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
