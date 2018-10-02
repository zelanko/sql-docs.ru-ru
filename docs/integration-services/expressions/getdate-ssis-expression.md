---
title: GETDATE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: afbbc80ce19c2820d24d65a9caa0736d00e7f8b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833162"
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
  
  
