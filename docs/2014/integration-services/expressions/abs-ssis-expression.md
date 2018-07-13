---
title: ABS (выражение служб SSIS) | Документы Майкрософт
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
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a13bb07db4dd258c63eb28b01219309c70224fa6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37184711"
---
# <a name="abs-ssis-expression"></a>ABS (выражение служб SSIS)
  Возвращает абсолютное положительное значение числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Является числовым выражением со знаком или без знака.  
  
## <a name="result-types"></a>Типы результата  
 Тип данных числового выражения, переданного функции.  
  
## <a name="remarks"></a>Примечания  
 Функция ABS возвращает NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этих примерах функция ABS применяется к положительному и отрицательному числам. В обоих случаях возвращается 1,23.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 В этом примере функция ABS применяется к разности значений переменных **HighTemperature** и **LowTempature**.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  
