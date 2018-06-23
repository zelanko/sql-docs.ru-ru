---
title: CEILING (выражение служб SSIS) | Документы Майкрософт
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
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6b7b6afd3879805c0badc1c15e6113971dcb776a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098443"
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
  
## <a name="remarks"></a>Примечания  
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
 [Функция FLOOR &#40;выражение служб SSIS&#41;](floor-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  