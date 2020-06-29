---
title: ROUND (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5edad70330a5745f9d150cf8a0ad0d540132c029
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437111"
---
# <a name="round-ssis-expression"></a>ROUND (выражение служб SSIS)
  Возвращает числовое выражение, округленное до указанной длины или точности. Параметр длины должен иметь целочисленное значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Является выражением допустимого числового типа. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 *length*  
 Является целочисленным выражением. Это точность, до которой должно быть округлено значение *numeric_expression* .  
  
## <a name="result-types"></a>Типы результата  
 Того же типа, что и *numeric*_*expression.*  
  
## <a name="remarks"></a>Remarks  
 Аргумент *length* должен иметь положительное целочисленное значение либо ноль.  
  
 ROUND возвращает результат NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Эти примеры округляют числовые величины до трех знаков. Первый возвращенный результат — 137.1570, второй — 137.1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
