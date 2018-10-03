---
title: ABS (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: c787a67c1c3a65b695e3fc7af79f2eda7c86f3be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852152"
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
  
## <a name="remarks"></a>Remarks  
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
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
