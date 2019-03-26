---
title: SQRT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d0104fbb4c2778b5913b4409d69d8902d83a8e14
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290400"
---
# <a name="sqrt-ssis-expression"></a>SQRT (выражение служб SSIS)
  Возвращает квадратный корень числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Числовое выражение любого типа числовых данных. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Remarks  
 Функция SQRT возвращает значение NULL, если аргумент равен NULL.  
  
 Если аргумент имеет отрицательное значение, то функция SQRT завершается неудачей.  
  
 Перед вычислением квадратного корня аргумент приводится к типу данных DT_R8.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере вычисляется квадратный корень из числа. Возвращается значение 12.  
  
```  
SQRT(144)  
```  
  
 В этом примере вычисляется квадратный корень из выражения, которое составлено из разности значений в столбцах **Value1** и **Value2** .  
  
```  
SQRT(Value1 - Value2)  
```  
  
 В этом примере вычисляется гипотенуза прямоугольного треугольника путем вычисления квадратов двух переменных с помощью функции SQUARE и последующего вычисления квадратного корня их суммы. Если **Side1** содержит 3, а **Side2** содержит 4, функция SQRT возвращает 5.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  В выражениях имена переменных всегда содержат префикс \@.  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
