---
title: DATEADD (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2285a23325b91a78759d1dac26725e0e570b23fb
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923468"
---
# <a name="dateadd-ssis-expression"></a>DATEADD (выражение служб SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Возвращает новое значение DT_DBTIMESTAMP после добавления числа, представляющего дату или интервал времени, к указанной части даты. Числовой параметр должен выражаться целым числом, а параметр даты — допустимой датой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a>Аргументы  
 *datepart*  
 Параметр, задающий, к какому разделу даты следует прибавить число.  
  
 *number*  
 Значение, используемое для увеличения *datepart*. Оно должно быть целочисленным, т.е. известным при синтаксическом анализе выражения.  
  
 *date*  
 Выражение, возвращающее допустимую дату или строку в формате даты.  
  
## <a name="result-types"></a>Типы результата  
 DT_DBTIMESTAMP  
  
## <a name="remarks"></a>Remarks  
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
|Секунда|ss, s|  
|Миллисекунда|Ms|  
  
 Аргумент *number* должен быть доступен при синтаксическом анализе выражения. Он может быть константой или переменной. Нельзя использовать значения столбцов, поскольку они неизвестны при синтаксическом анализе выражения.  
  
 Аргумент *datepart* необходимо заключать в кавычки.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [DATEDIFF (выражение служб SSIS)](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART (выражение служб SSIS)](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY (выражение служб SSIS)](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH (выражение служб SSIS)](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](../../integration-services/expressions/year-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
