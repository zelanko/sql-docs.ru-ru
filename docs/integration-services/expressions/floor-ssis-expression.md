---
title: FLOOR (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3a79328a87c3b28f814c70c394b8a3e92aeaa6c7
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411396"
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
 [CEILING (выражение служб SSIS)](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
