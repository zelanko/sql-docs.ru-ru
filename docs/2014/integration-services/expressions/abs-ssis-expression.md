---
title: ABS (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 445ced2ff3b8d8cb46a8f247d41d7757ba039767
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52766311"
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
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
