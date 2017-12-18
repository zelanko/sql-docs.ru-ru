---
title: "GETUTCDATE (выражение служб SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
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
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
caps.latest.revision: "32"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 626ac3a41c17ad5dd7c0458d728d6b21a1c70741
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (выражение служб SSIS)
  Возвращает текущую дату системы в формате времени UTC (универсальное время, или время по Гринвичу), используя формат DT_DBTIMESTAMP. Функция GETUTCDATE не имеет аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>Аргументы  
 Нет  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [GETDATE (выражение служб SSIS)](../../integration-services/expressions/getdate-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
