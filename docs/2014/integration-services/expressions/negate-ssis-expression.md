---
title: '- (инверсия) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6d2a015bd0b2f8ee2f72a50557a848a1f73335fb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215814"
---
# <a name="--negate-ssis-expression"></a>- (инверсия) (выражение служб SSIS)
  Инвертирует числовое выражение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Любое допустимое выражение любого числового типа данных. Поддерживаются только типы данных со знаком. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных *numeric_expression*.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере знак переменной **Counter** изменяется на противоположный, и к ней прибавляется число 50.  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>См. также  
 [Приоритет и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы &#40;выражение служб SSIS&#41;](operators-ssis-expression.md)  
  
  
