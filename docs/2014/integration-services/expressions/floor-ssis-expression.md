---
title: FLOOR (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8624354ff5b29430a58f0393047c9a875cf984c2
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428681"
---
# <a name="floor-ssis-expression"></a>FLOOR (выражение службы SSIS)
  Возвращает наибольшее целое число, меньшее или равное числовому выражению.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Допустимое числовое выражение.  
  
## <a name="result-types"></a>Типы результата  
 Числовой тип данных выражения аргумента. Результат представляет собой целую часть вычисляемого значения и имеет тот же тип данных, что и *numeric_expression.*  
  
## <a name="remarks"></a>Remarks  
 Функция FLOOR возвращает NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этих примерах функция FLOOR применяется к положительному, отрицательному и нулевому значениям.  
  
```  
FLOOR(123.45)  
```  
  
 Возвращает значение 123,00  
  
```  
FLOOR(-123.45)  
```  
  
 Возвращает значение −124,00  
  
```  
FLOOR(0.00)  
```  
  
 Возвращает значение 0,00  
  
## <a name="see-also"></a>См. также:  
 [CEILING (выражение служб SSIS)](ceiling-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
