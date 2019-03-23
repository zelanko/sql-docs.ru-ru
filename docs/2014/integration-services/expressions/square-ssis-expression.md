---
title: SQUARE (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8e457601eafcdd8e363d931d53dfea673254b29f
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385428"
---
# <a name="square-ssis-expression"></a>SQUARE (выражение служб SSIS)
  Возвращает квадрат числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Числовое выражение любого типа числовых данных. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Примечания  
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
>  В выражениях имена переменных всегда содержат префикс \@.  
  
## <a name="see-also"></a>См. также  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
