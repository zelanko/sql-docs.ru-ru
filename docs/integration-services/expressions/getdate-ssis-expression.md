---
title: "GETDATE (выражение служб SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e792dc04b4bb115dc3e9dff840da1690395862e9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

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
 Нет  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [GETUTCDATE &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/getutcdate-ssis-expression.md)   
 [Функции &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
