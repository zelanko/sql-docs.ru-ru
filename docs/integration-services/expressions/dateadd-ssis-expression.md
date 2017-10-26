---
title: "Функция DATEADD (выражение служб SSIS) | Документы Microsoft"
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
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 77230956969fb2fd2d27a1dec42140dd91a5cbd5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="dateadd-ssis-expression"></a>DATEADD (выражение служб SSIS)
  Возвращает новое значение DT_DBTIMESTAMP после добавления числа, представляющего дату или интервал времени, к указанной части даты. Числовой параметр должен выражаться целым числом, а параметр даты — допустимой датой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a>Аргументы  
 *часть_даты*  
 Параметр, задающий, к какому разделу даты следует прибавить число.  
  
 *number*  
 Значение, используемое для увеличения *datepart*. Оно должно быть целочисленным, т.е. известным при синтаксическом анализе выражения.  
  
 *date*  
 Выражение, возвращающее допустимую дату или строку в формате даты.  
  
## <a name="result-types"></a>Типы результата  
 DT_DBTIMESTAMP  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице перечислены части дат и сокращения, распознаваемые средством оценки выражений. Имена частей даты обрабатываются без учета регистра.  
  
|часть_даты|Сокращения|  
|--------------|-------------------|  
|Год|yy, yyyy|  
|Квартал|qq, q|  
|Месяц|mm, m|  
|День года|dy, y|  
|День|dd, d|  
|Неделя|wk, ww|  
|День недели|dw, w|  
|Час|Hh|  
|Минута|mi, n|  
|Вторая|ss, s|  
|Миллисекунда|Ms|  
  
 Аргумент *number* должен быть доступен при синтаксическом анализе выражения. Он может быть константой или переменной. Нельзя использовать значения столбцов, поскольку они неизвестны при синтаксическом анализе выражения.  
  
 Аргумент *datepart* необходимо заключать в кавычки.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Функция DATEADD возвращает результат NULL, если значением аргумента является NULL.  
  
 Ошибки возникают в тех случаях, когда дата недопустима, единица даты и времени не является строкой или приращение не является статическим целым числом.  
  
## <a name="ssis-expression-examples"></a>Примеры выражений служб SSIS  
 В этом примере добавляется один месяц к текущей дате.  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 В этом примере добавляется 21 день к датам в столбце **ModifiedDate** .  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 В этом примере добавляются два года к литеральной дате.  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a>См. также  
 [Функция DATEDIFF &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [ДЕНЬ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [МЕСЯЦ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [ГОД &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Функции &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

