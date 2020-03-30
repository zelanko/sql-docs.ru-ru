---
title: CODEPOINT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 06c015c2f96bf2f7206a3e802d44a65871828d2c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71290262"
---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Возвращает кодовую точку в Юникоде крайнего левого символа указанного символьного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, чей крайний левый символ будет вычислен.  
  
## <a name="result-types"></a>Типы результата  
 DT_UI2  
  
## <a name="remarks"></a>Remarks  
 Параметр*character_expression* должен иметь тип данных DT_WSTR.  
  
 Функция CODEPOINT возвращает результат NULL, если параметр *character_expression* выражен значением NULL или пустой строкой.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В данном примере используется строковый литерал. Возвращенный результат 77 — кодовая точка Юникод для M.  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 В данном примере используется переменная. Если **Name** — «Touring Front Wheel», то возвращается результат 84 — код Юникод для T.  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
