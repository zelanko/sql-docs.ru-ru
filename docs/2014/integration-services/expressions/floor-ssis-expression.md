---
title: FLOOR (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cae43e01a262258fa2fce824797b3d20682c3829
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098936"
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
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Верхний ПРЕДЕЛ &#40;выражение служб SSIS&#41;](ceiling-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  