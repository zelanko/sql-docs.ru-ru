---
title: "SQUARE (выражение служб SSIS) | Документы Microsoft"
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
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 18be83801a35d9b3512d85f69c91256147fb81a9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="square-ssis-expression"></a>SQUARE (выражение служб SSIS)
  Возвращает квадрат числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Числовое выражение любого типа числовых данных. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Замечания  
 Функция SQUARE возвращает значение NULL, если аргумент принимает значение NULL.  
  
 Перед операцией возведения в квадрат аргумент приводится к типу данных DT_R8.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает квадрат числа 12. Возвращается результат 144.  
  
```  
SQUARE(12)  
```  
  
 Этот пример возвращает квадрат результата вычитания значений в двух столбцах. Если **Value1** содержит число 12, а **Value2** содержит число 4, функция SQUARE возвращает 64.  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 Этот пример возвращает длину третьей стороны прямоугольного треугольника путем применения функции SQUARE к двум переменным, а затем вычисления квадратного корня из суммы получившихся значений. Если **Side1** содержит 3, а **Side2** содержит 4, функция SQRT возвращает 5.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  В выражениях имена переменных всегда содержат префикс @.  
  
## <a name="see-also"></a>См. также  
 [Функции &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

