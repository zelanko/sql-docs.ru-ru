---
title: "CEILING (выражение служб SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 971c7038c0b144ac4073162e0d14b519e263328f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="ceiling-ssis-expression"></a>CEILING (выражение служб SSIS)
  Возвращает наименьшее целое число, большее или равное данному числовому выражению.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Допустимое числовое выражение.  
  
## <a name="result-types"></a>Типы результата  
 Тип данных числового выражения, переданного функции.  
  
## <a name="remarks"></a>Замечания  
 Функция CEILING возвращает NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этих примерах функция CEILING применяется к положительным, отрицательным значениям и к нулю.  
  
```  
CEILING(123.74)  
```  
  
 Возвращает значение 124,00  
  
```  
CEILING(-124.27)  
```  
  
 Возвращает значение −124,00  
  
```  
CEILING(0.00)  
```  
  
 Возвращает значение 0,00  
  
## <a name="see-also"></a>См. также  
 [FLOOR (выражение служб SSIS)](../../integration-services/expressions/floor-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
