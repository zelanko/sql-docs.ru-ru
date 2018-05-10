---
title: EXP (выражение служб SSIS) | Документы Майкрософт
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
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e570d60f4f6765b38d4c34d8fa92d2944b34d6da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="exp-ssis-expression"></a>EXP (выражение служб SSIS)
  Возвращает значение экспоненты основания е числового выражения. Функция EXP дополняет действие функции LN и иногда называется обратным логарифмом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Допустимое числовое выражение.  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Remarks  
 Перед вычислением степени числовое выражение приводится к типу данных DT_R8. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Возвращаемый результат всегда является положительным числом.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этих примерах функция EXP применяется к положительным значениям, отрицательным значениям и к нулю.  
  
```  
EXP(74)  
```  
  
 Возвращает 1.373382979540176E+32.  
  
```  
EXP(-27)  
```  
  
 Возвращает 1.879528816539083E-12.  
  
```  
EXP(0)  
```  
  
 Возвращает значение 1.  
  
## <a name="see-also"></a>См. также:  
 [LOG (выражение служб SSIS)](../../integration-services/expressions/log-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
