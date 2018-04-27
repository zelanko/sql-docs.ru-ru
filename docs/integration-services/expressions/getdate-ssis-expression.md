---
title: GETDATE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 29c3f28f3efa22a1691cc47e105300e7dd92543e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="getdate-ssis-expression"></a>GETDATE (выражение служб SSIS)
  Возвращает текущее системное время в формате DT_DBTIMESTAMP. Функция GETDATE не имеет аргументов.  
  
> [!NOTE]  
>  Длина строки результата, возвращаемой функцией GETDATE, равна 29 символам.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>Аргументы  
 None  
  
## <a name="result-types"></a>Типы результата  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает текущий год.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 Этот пример возвращает число дней от даты в столбце **ModifiedDate** до текущей даты.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 Этот пример добавляет три месяца к текущей дате.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>См. также:  
 [GETUTCDATE (выражение служб SSIS)](../../integration-services/expressions/getutcdate-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
