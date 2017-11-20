---
title: "RIGHT (выражение служб SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RIGHT function
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b81ead33054642391dcd95d56746a90cf347dcc9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="right-ssis-expression"></a>RIGHT (выражение служб SSIS)
  Возвращает указанное количество символов из крайней правой части заданного символьного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RIGHT(character_expression,integer_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, из которого извлекаются символы.  
  
 *integer_expression*  
 Является целочисленным выражением, которое указывает количество возвращаемых символов.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Замечания  
 Если *integer_expression* длиннее, чем *character_expression*, функция возвращает *character_expression*.  
  
 Если *integer_expression* равно нулю, функция возвращает строку нулевой длины.  
  
 Если *integer_expression* является отрицательным числом, функция возвращает ошибку.  
  
 Аргумент *integer_expression* может принимать переменные и столбцы.  
  
 Функция RIGHT работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции RIGHT. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
 RIGHT возвращает результат NULL, если любой из аргументов имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В следующем примере используется строковый литерал. Возвращаемым результатом является `"Bike"`.  
  
```  
RIGHT("Mountain Bike", 4)  
```  
  
 В следующем примере возвращается количество крайних правых символов, указанное в переменной `Times` из столбца `Name` . Если `Name` имеет значение `Touring Front Wheel` , а `Times` равно 5, возвращается результат `"Wheel"`.  
  
```  
RIGHT(Name, @Times)  
```  
  
 В следующем примере возвращается количество крайних правых символов, указанное в переменной `Times` из столбца `Name` . `Times` имеет нецелочисленный тип данных, и выражение включает явное приведение к типу данных DT_I2. Если `Name` имеет значение `Touring Front Wheel` , а `Times` имеет значение `4.32`, возвращается результат `"heel"` , поскольку функция RIGHT округляет значение 4.32 до 4 и возвращает четыре крайних правых символа.  
  
```  
RIGHT(Name, (DT_I2)@Times))  
```  
  
## <a name="see-also"></a>См. также  
 [Левый &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/left-ssis-expression.md)   
 [Функции &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

