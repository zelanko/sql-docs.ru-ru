---
title: FLOOR (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 56f69743e8bbfb8290e492613daeb07885f5ed7d
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71289617"
---
# <a name="floor-ssis-expression"></a>FLOOR (выражение службы SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
 [CEILING (выражение служб SSIS)](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
