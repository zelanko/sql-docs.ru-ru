---
title: SIGN (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b77aaffe4e6f0f0163978ba346abdd31cdc61ce8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62897310"
---
# <a name="sign-ssis-expression"></a>SIGN (выражение служб SSIS)
  Возвращает знак числового выражения в виде положительного (+1), нулевого (0) или отрицательного (-1) числа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Является допустимым числовым выражением со знаком. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 Функция SIGN возвращает результат NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает знак числового литерала. Возвращается результат -1.  
  
```  
SIGN(-123.45)  
```  
  
 Этот пример возвращает знак результата вычитания значения столбца **StandardCost** из значения столбца **DealerPrice** .  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
