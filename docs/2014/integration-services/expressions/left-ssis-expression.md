---
title: LEFT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 41aef87375e50d40ccdec3b6d80782ab028bbf1f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103684"
---
# <a name="left-ssis-expression"></a>LEFT (выражение служб SSIS)
  Возвращает указанное количество символов из крайней левой части заданного символьного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, из которого извлекаются символы.  
  
 *number*  
 Является целочисленным выражением, которое указывает количество возвращаемых символов.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Примечания  
 Если *number* длиннее, чем *character_expression*, функция возвращает *character_expression*.  
  
 Если *number* равен нулю, функция возвращает строку нулевой длины.  
  
 Если *number* является отрицательным числом, то функция возвратит ошибку.  
  
 Аргумент *number* может принимать переменные и столбцы.  
  
 Функция LEFT работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции LEFT. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
 LEFT возвращает результат NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В следующем примере используется строковый литерал. Возвращаемым результатом является `"Mountain"`.  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a>См. также  
 [СПРАВА &#40;выражение служб SSIS&#41;](right-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  
