---
title: '- (инверсия) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ac803cb797644d47c6bc5ee4fcee99e14ba88a4c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969194"
---
# <a name="--negate-ssis-expression"></a>- (инверсия) (выражение служб SSIS)
  Инвертирует числовое выражение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Любое допустимое выражение любого числового типа данных. Поддерживаются только типы данных со знаком. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Возвращает тип данных *numeric_expression*.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере знак переменной **Counter** изменяется на противоположный, и к ней прибавляется число 50.  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](operators-ssis-expression.md)  
  
  
