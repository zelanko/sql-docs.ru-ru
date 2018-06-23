---
title: CODEPOINT (выражение служб SSIS) | Документы Майкрософт
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
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e038fc2856bacbcf69ad06091157198dfe3dbd6c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087899"
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
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  