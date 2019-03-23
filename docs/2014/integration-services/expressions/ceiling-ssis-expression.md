---
title: CEILING (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a8306fa98194fbf314796b199fea98ddd53cb1fb
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58375603"
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
 [FLOOR (выражение служб SSIS)](floor-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
