---
title: DATEDIFF (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 04bedeba150a98bbb0ecba04aad6f54f3dd1182d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069594"
---
# <a name="datediff-ssis-expression"></a>DATEDIFF (выражение служб SSIS)
  Возвращает числовое значение границ дат или времени между двумя указанными датами. Параметр *datepart* указывает границы даты и времени, которые необходимо сравнить.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a>Аргументы  
 *datepart*  
 Параметр, который указывает, какую часть даты сравнивать и для какой вернуть значение.  
  
 *startdate*  
 Начальная дата периода.  
  
 *endate*  
 Конечная дата периода.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Примечания  
 В следующей таблице перечислены части дат и сокращения, распознаваемые средством оценки выражений.  
  
|datepart|Сокращения|  
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
  
 DATEDIFF возвращает NULL, если хотя бы один аргумент имеет значение NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 Произойдет ошибка при передаче недопустимой даты, а также в случае, если единица времени или даты не является строкой или если дата начала либо конца не является датой.  
  
 Если конечная дата является более ранней, чем начальная, то функция возвращает отрицательное число. Если начальные и конечные даты равны друг другу или находятся в одном интервале, то функция возвращает ноль.  
  
## <a name="ssis-expression-examples"></a>Примеры выражений служб SSIS  
 Этот пример вычисляет количество дней между двумя литералами даты. Если дата имеет формат «мм/дд/гггг», то эта функция возвращает 7.  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 Этот пример возвращает количество месяцев между литералом даты и текущей датой.  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 Этот пример возвращает количество недель между датой в столбце **ModifiedDate** и переменной **YearEndDate** . Если **YearEndDate** имеет `date` тип данных, то явного приведения не требуется.  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a>См. также  
 [DATEADD &#40;выражение служб SSIS&#41;](dateadd-ssis-expression.md)   
 [DATEPART (выражение служб SSIS)](datepart-ssis-expression.md)   
 [DAY (выражение служб SSIS)](day-ssis-expression.md)   
 [MONTH (выражение служб SSIS)](month-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](year-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  
