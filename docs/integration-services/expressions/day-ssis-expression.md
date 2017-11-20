---
title: "DAY (выражение служб SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5e297f7021239ded4aa76ad61e75fddba528ccf6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="day-ssis-expression"></a>DAY (выражение служб SSIS)
  Возвращает целое число, представляющее день указанной даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a>Аргументы  
 *date*  
 Выражение, возвращающее допустимую дату или строку в формате даты.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Замечания  
 Функция DAY возвращает значение NULL, если значение аргумента NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  Проверка выражения завершается ошибкой при явном приведении литерала даты к одному из следующих типов данных: DT_DBTIMESTAMPOFFSET и DT_DBTIMESTAMP2.  
  
 Использование функции DAY более компактно, но эквивалентно использованию функции DATEPART("Day", date).  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере возвращается номер дня из литерала даты. Если дата имеет формат «мм/дд/гггг», будет возвращено значение 23.  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 Этот пример возвращает целое число, представляющее день в столбце **ModifiedDate** .  
  
```  
DAY(ModifiedDate)  
```  
  
 В этом примере возвращается целое число, представляющее день текущей даты.  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a>См. также  
 [Функция DATEADD &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [Функция DATEDIFF &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [МЕСЯЦ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [ГОД &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Функции &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

