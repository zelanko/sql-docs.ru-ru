---
description: CEILING (выражение служб SSIS)
title: CEILING (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 533cef6354c3dcea15146809a1f2466f342e60c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457293"
---
# <a name="ceiling-ssis-expression"></a>CEILING (выражение служб SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


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
  
## <a name="remarks"></a>Комментарии  
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
  
  
