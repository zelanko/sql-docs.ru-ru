---
title: SQRT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e9e871242572df1f66faa1cbf19c948e0be6f1c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271490"
---
# <a name="sqrt-ssis-expression"></a>SQRT (выражение служб SSIS)
  Возвращает квадратный корень числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Числовое выражение любого типа числовых данных. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Примечания  
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
>  В выражениях имена переменных всегда содержат префикс @.  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  
