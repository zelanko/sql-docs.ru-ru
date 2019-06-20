---
title: CODEPOINT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 10d2eeb6991c0c75e8dbe8102f94148f60f0a361
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62769381"
---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (выражение служб SSIS)
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
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
