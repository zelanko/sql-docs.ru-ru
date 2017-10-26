---
title: "Функции (выражение служб SSIS) | Документы Microsoft"
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
- functions [Integration Services]
- expressions [Integration Services], functions
- string functions
- SQL Server Integration Services, functions
- SSIS, functions
ms.assetid: e9a41a31-94f4-46a4-b737-c707dd59ce48
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d147ad369495c4046e4387dca7abcec5e533c2af
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="functions-ssis-expression"></a>Функции (выражение служб SSIS)
  Язык выражений включает набор функций, которые можно использовать в выражениях. Выражение может использовать только одну функцию, но обычно в выражении используется комбинация операторов и нескольких функций.  
  
 Данные функции можно разделить на следующие группы:  
  
-   Математические функции, выполняющие вычисления на основании числовых значений, переданных как параметры, и возвращающие числовые значения.  
  
-   Строковые функции, выполняющие операции над строками или входными параметрами в шестнадцетиричном виде и возвращающие строку или число.  
  
-   Функции для работы с датой и временем, выполняющие операции над значениями даты и времени и возвращающие строку, число или значение даты и времени.  
  
-   Системные функции, возвращающие сведения о выражении.  
  
 Язык выражений содержит следующие математические функции.  
  
|Функция|Description|  
|--------------|-----------------|  
|[ABS &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/abs-ssis-expression.md)|Возвращает абсолютное положительное значение числового выражения.|  
|[EXP &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/exp-ssis-expression.md)|Возвращает число «е» в степени, определяемой данным выражением.|  
|[Функция CEILING &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/ceiling-ssis-expression.md)|Возвращает наименьшее целое число, большее или равное данному числовому выражению.|  
|[Функция FLOOR &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/floor-ssis-expression.md)|Возвращает наибольшее целое число, меньшее или равное числовому выражению.|  
|[LN &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/ln-ssis-expression.md)|Возвращает натуральный логарифм числового выражения.|  
|[ЖУРНАЛ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/log-ssis-expression.md)|Возвращает десятичный логарифм числового выражения.|  
|[POWER &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/power-ssis-expression.md)|Возвращает результат возведения числового выражения в степень.|  
|[ЦИКЛИЧЕСКИЙ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/round-ssis-expression.md)|Возвращает числовое выражение, округленное до указанной длины или точности. .|  
|[SIGN &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/sign-ssis-expression.md)|Возвращает знак выражения: плюс (+), минус (-) или нуль (0).|  
|[КВАДРАТ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/square-ssis-expression.md)|Возвращает квадрат числового выражения.|  
|[SQRT &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/sqrt-ssis-expression.md)|Возвращает квадратный корень числового выражения.|  
  
 Средство оценки выражений содержит следующие строковые функции.  
  
|Функция|Description|  
|--------------|-----------------|  
|[CODEPOINT &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/codepoint-ssis-expression.md)|Возвращает значение кода Юникод самого первого символа в символьном выражении.|  
|[FINDSTRING &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/findstring-ssis-expression.md)|Возвращает однократный индекс указанного вхождения символьной строки в выражение.|  
|[HEX &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/hex-ssis-expression.md)|Возвращает строку, представляющую собой шестнадцатеричное значение целого числа.|  
|[Функция LEN &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/len-ssis-expression.md)|Возвращает число символов в символьном выражении.|  
|[Левый &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/left-ssis-expression.md)|Возвращает указанное количество символов из крайней левой части заданного символьного выражения.|  
|[НИЖНЕГО &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/lower-ssis-expression.md)|Возвращает символьное выражение после преобразования всех символов верхнего регистра в нижний.|  
|[Функция LTRIM &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/ltrim-ssis-expression.md)|Возвращает символьное выражение после удаления начальных пробелов.|  
|[Заменить &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/replace-ssis-expression.md)|Возвращает символьное выражение после замены строки в этом выражении на другую строку или пустую строку.|  
|[REPLICATE &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/replicate-ssis-expression.md)|Возвращает символьное выражение, реплицированное указанное число раз.|  
|[ОБРАТИТЬ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/reverse-ssis-expression.md)|Возвращает символьное выражение в обратном порядке.|  
|[ПРАВО &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/right-ssis-expression.md)|Возвращает указанное количество символов из крайней правой части заданного символьного выражения.|  
|[RTRIM &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/rtrim-ssis-expression.md)|Возвращает символьное выражение после удаления конечных пробелов.|  
|[ПОДСТРОКА &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/substring-ssis-expression.md)|Возвращает фрагмент символьного выражения.|  
|[Функция TRIM &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/trim-ssis-expression.md)|Возвращает символьное выражение после удаления начальных и конечных пробелов.|  
|[ВЕРХНЯЯ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/upper-ssis-expression.md)|Возвращает символьное выражение после преобразования символов в нижнем регистре в символы верхнего регистра.|  
  
 Средство оценки выражений содержит следующие функции для работы с датой и временем.  
  
|Функция|Description|  
|--------------|-----------------|  
|[Функция DATEADD &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/dateadd-ssis-expression.md)|Возвращает новое значение типа DT_DBTIMESTAMP, образованное добавлением интервала времени или даты к указанной дате.|  
|[Функция DATEDIFF &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/datediff-ssis-expression.md)|Возвращает числовое значение границ дат или времени между двумя указанными датами.|  
|[DATEPART &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/datepart-ssis-expression.md)|Возвращает целое число, обозначающее раздел даты.|  
|[ДЕНЬ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/day-ssis-expression.md)|Возвращает целое число, представляющее число месяца указанной даты.|  
|[Функция GETDATE &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/getdate-ssis-expression.md)|Возвращает текущую системную дату.|  
|[GETUTCDATE &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/getutcdate-ssis-expression.md)|Возвращает текущую системную дату в формате UTC (универсальное время или время по Гринвичу).|  
|[МЕСЯЦ &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/month-ssis-expression.md)|Возвращает целое число, представляющее месяц указанной даты.|  
|[ГОД &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/year-ssis-expression.md)|Возвращает целое число, представляющее год указанной даты.|  
  
 Средство оценки выражений содержит следующие функции для значения NULL.  
  
|Функция|Description|  
|--------------|-----------------|  
|[Функция ISNULL &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/isnull-ssis-expression.md)|Возвращает результат в виде логического выражения, в зависимости от того, имеет ли выражение значение NULL.|  
|[NULL &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/null-ssis-expression.md)|Возвращает значение NULL запрошенного типа данных.|  
  
 Названия выражений указаны в верхнем регистре, но эти имена обрабатываются без учета регистра. Например, значение «null» равносильно использованию значения «NULL».  
  
## <a name="see-also"></a>См. также  
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)   
 [Примеры выражений служб интеграции](../../integration-services/expressions/examples-of-advanced-integration-services-expressions.md)   
 [Службы Integration Services &#40; Службы SSIS &#41; Выражения](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  

