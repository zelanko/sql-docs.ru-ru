---
title: REPLICATE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- REPLICATE function
ms.assetid: e7a37b93-6d1d-42d5-9a65-de1790abf6a5
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 06026b418fac119f45868425e0a75d53fb514144
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="replicate-ssis-expression"></a>REPLICATE (выражение служб SSIS)
  Возвращает символьное выражение, которое было реплицировано, заданное количество раз. Аргумент *times* должен выдавать целое число.  
  
> [!NOTE]  
>  Функция REPLICATE часто использует длинные строки, поэтому лучше ввести ограничение на длину выражения — 4 000 символов. Если результат вычисления выражения имеет тип данных служб Integration Services DT_WSTR или DT_STR, выражение будет усечено до 4000 символов. Если тип результата вложенного выражения — DT_STR или DT_WSTR, это выражение также будет усечено до 4000 символов, независимо от типа результата всего выражения. Последствия усечения могут быть корректно обработаны или могут вызвать предупреждение или ошибку. Дополнительные сведения см. в разделе [Синтаксис (службы SSIS)](../../integration-services/expressions/syntax-ssis.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REPLICATE(character_expression,times)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение для репликации.  
  
 *times*  
 Целочисленное выражение, которое определяет, сколько раз *character_expression* будет реплицировано.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Если *times* равно нулю, функция возвратит строку нулевой длины.  
  
 Если *times* является отрицательным числом, то функция возвратит ошибку.  
  
 Аргумент *times* также может использовать переменные и столбцы.  
  
 Функция REPLICATE работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции REPLICATE. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Функция REPLICATE возвращает NULL, если значение любого из аргументов равно NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример реплицирует строковый литерал три раза. Результат — «Mountain BikeMountain BikeMountain Bike».  
  
```  
REPLICATE("Mountain Bike", 3)  
```  
  
 Этот пример реплицирует значения в столбце **Name** значением из переменной **Times** . Если **Times** равно 3 и **Name** равно «Touring Front Wheel», то результат будет — «Touring Front WheelTouring Front WheelTouring Front Wheel».  
  
```  
REPLICATE(Name, @Times)  
```  
  
 Этот пример реплицирует значение в переменной **Name** значением из столбца **Times** . **Times** имеет нецелочисленный тип данных и выражение включает явное приведение к целочисленному типу данных. Если **Name** содержит «Helmet» и **Times** равно 2, то результат будет — «HelmetHelmet».  
  
```  
REPLICATE(@Name, (DT_I4(Times))  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
