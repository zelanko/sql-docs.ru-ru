---
title: "Функции (выражение служб SSIS) | Документы Майкрософт"
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
- functions [Integration Services]
- expressions [Integration Services], functions
- string functions
- SQL Server Integration Services, functions
- SSIS, functions
ms.assetid: e9a41a31-94f4-46a4-b737-c707dd59ce48
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 836ecde7ff2cb458b2f93aeb239d0ab83c51cb6b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="functions-ssis-expression"></a>Функции (выражение служб SSIS)
  Язык выражений включает набор функций, которые можно использовать в выражениях. Выражение может использовать только одну функцию, но обычно в выражении используется комбинация операторов и нескольких функций.  
  
 Данные функции можно разделить на следующие группы:  
  
-   Математические функции, выполняющие вычисления на основании числовых значений, переданных как параметры, и возвращающие числовые значения.  
  
-   Строковые функции, выполняющие операции над строками или входными параметрами в шестнадцетиричном виде и возвращающие строку или число.  
  
-   Функции для работы с датой и временем, выполняющие операции над значениями даты и времени и возвращающие строку, число или значение даты и времени.  
  
-   Системные функции, возвращающие сведения о выражении.  
  
 Язык выражений содержит следующие математические функции.  
  
|Компонент|Description|  
|--------------|-----------------|  
|[ABS (выражение служб SSIS)](../../integration-services/expressions/abs-ssis-expression.md)|Возвращает абсолютное положительное значение числового выражения.|  
|[EXP (выражение служб SSIS)](../../integration-services/expressions/exp-ssis-expression.md)|Возвращает число «е» в степени, определяемой данным выражением.|  
|[CEILING (выражение служб SSIS)](../../integration-services/expressions/ceiling-ssis-expression.md)|Возвращает наименьшее целое число, большее или равное данному числовому выражению.|  
|[FLOOR (выражение служб SSIS)](../../integration-services/expressions/floor-ssis-expression.md)|Возвращает наибольшее целое число, меньшее или равное числовому выражению.|  
|[LN (выражение служб SSIS)](../../integration-services/expressions/ln-ssis-expression.md)|Возвращает натуральный логарифм числового выражения.|  
|[LOG (выражение служб SSIS)](../../integration-services/expressions/log-ssis-expression.md)|Возвращает десятичный логарифм числового выражения.|  
|[POWER (выражение служб SSIS)](../../integration-services/expressions/power-ssis-expression.md)|Возвращает результат возведения числового выражения в степень.|  
|[ROUND (выражение служб SSIS)](../../integration-services/expressions/round-ssis-expression.md)|Возвращает числовое выражение, округленное до указанной длины или точности. , и делает это по-другому.|  
|[SIGN (выражение служб SSIS)](../../integration-services/expressions/sign-ssis-expression.md)|Возвращает знак выражения: плюс (+), минус (-) или нуль (0).|  
|[SQUARE (выражение служб SSIS)](../../integration-services/expressions/square-ssis-expression.md)|Возвращает квадрат числового выражения.|  
|[SQRT (выражение служб SSIS)](../../integration-services/expressions/sqrt-ssis-expression.md)|Возвращает квадратный корень числового выражения.|  
  
 Средство оценки выражений содержит следующие строковые функции.  
  
|Компонент|Description|  
|--------------|-----------------|  
|[CODEPOINT (выражение служб SSIS)](../../integration-services/expressions/codepoint-ssis-expression.md)|Возвращает значение кода Юникод самого первого символа в символьном выражении.|  
|[FINDSTRING (выражение служб SSIS)](../../integration-services/expressions/findstring-ssis-expression.md)|Возвращает однократный индекс указанного вхождения символьной строки в выражение.|  
|[HEX (выражение служб SSIS)](../../integration-services/expressions/hex-ssis-expression.md)|Возвращает строку, представляющую собой шестнадцатеричное значение целого числа.|  
|[LEN (выражение служб SSIS)](../../integration-services/expressions/len-ssis-expression.md)|Возвращает число символов в символьном выражении.|  
|[LEFT (выражение SSIS)](../../integration-services/expressions/left-ssis-expression.md)|Возвращает указанное количество символов из крайней левой части заданного символьного выражения.|  
|[LOWER (выражение служб SSIS)](../../integration-services/expressions/lower-ssis-expression.md)|Возвращает символьное выражение после преобразования всех символов верхнего регистра в нижний.|  
|[LTRIM (выражение служб SSIS)](../../integration-services/expressions/ltrim-ssis-expression.md)|Возвращает символьное выражение после удаления начальных пробелов.|  
|[REPLACE (выражение служб SSIS)](../../integration-services/expressions/replace-ssis-expression.md)|Возвращает символьное выражение после замены строки в этом выражении на другую строку или пустую строку.|  
|[REPLICATE (выражение служб SSIS)](../../integration-services/expressions/replicate-ssis-expression.md)|Возвращает символьное выражение, реплицированное указанное число раз.|  
|[REVERSE (выражение служб SSIS)](../../integration-services/expressions/reverse-ssis-expression.md)|Возвращает символьное выражение в обратном порядке.|  
|[RIGHT (выражение служб SSIS)](../../integration-services/expressions/right-ssis-expression.md)|Возвращает указанное количество символов из крайней правой части заданного символьного выражения.|  
|[RTRIM (выражение служб SSIS)](../../integration-services/expressions/rtrim-ssis-expression.md)|Возвращает символьное выражение после удаления конечных пробелов.|  
|[SUBSTRING (выражение служб SSIS)](../../integration-services/expressions/substring-ssis-expression.md)|Возвращает фрагмент символьного выражения.|  
|[TRIM (выражение служб SSIS)](../../integration-services/expressions/trim-ssis-expression.md)|Возвращает символьное выражение после удаления начальных и конечных пробелов.|  
|[UPPER (выражение служб SSIS)](../../integration-services/expressions/upper-ssis-expression.md)|Возвращает символьное выражение после преобразования символов в нижнем регистре в символы верхнего регистра.|  
  
 Средство оценки выражений содержит следующие функции для работы с датой и временем.  
  
|Функция|Description|  
|--------------|-----------------|  
|[DATEADD (выражение служб SSIS)](../../integration-services/expressions/dateadd-ssis-expression.md)|Возвращает новое значение типа DT_DBTIMESTAMP, образованное добавлением интервала времени или даты к указанной дате.|  
|[DATEDIFF (выражение служб SSIS)](../../integration-services/expressions/datediff-ssis-expression.md)|Возвращает числовое значение границ дат или времени между двумя указанными датами.|  
|[DATEPART (выражение служб SSIS)](../../integration-services/expressions/datepart-ssis-expression.md)|Возвращает целое число, обозначающее раздел даты.|  
|[DAY (выражение служб SSIS)](../../integration-services/expressions/day-ssis-expression.md)|Возвращает целое число, представляющее число месяца указанной даты.|  
|[GETDATE (выражение служб SSIS)](../../integration-services/expressions/getdate-ssis-expression.md)|Возвращает текущую системную дату.|  
|[GETUTCDATE (выражение служб SSIS)](../../integration-services/expressions/getutcdate-ssis-expression.md)|Возвращает текущую системную дату в формате UTC (универсальное время или время по Гринвичу).|  
|[MONTH (выражение служб SSIS)](../../integration-services/expressions/month-ssis-expression.md)|Возвращает целое число, представляющее месяц указанной даты.|  
|[YEAR (выражение служб SSIS)](../../integration-services/expressions/year-ssis-expression.md)|Возвращает целое число, представляющее год указанной даты.|  
  
 Средство оценки выражений содержит следующие функции для значения NULL.  
  
|Компонент|Description|  
|--------------|-----------------|  
|[ISNULL (выражение служб SSIS)](../../integration-services/expressions/isnull-ssis-expression.md)|Возвращает результат в виде логического выражения, в зависимости от того, имеет ли выражение значение NULL.|  
|[NULL (выражение служб SSIS)](../../integration-services/expressions/null-ssis-expression.md)|Возвращает значение NULL запрошенного типа данных.|  
  
 Названия выражений указаны в верхнем регистре, но эти имена обрабатываются без учета регистра. Например, значение «null» равносильно использованию значения «NULL».  
  
## <a name="see-also"></a>См. также:  
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)   
 [Примеры расширенных выражений служб Integration Services](../../integration-services/expressions/examples-of-advanced-integration-services-expressions.md)   
 [Выражения служб Integration Services (SSIS)](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  
