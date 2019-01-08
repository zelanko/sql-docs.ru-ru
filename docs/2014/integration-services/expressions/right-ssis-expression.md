---
title: RIGHT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RIGHT function
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0e8d1cfdda299c786aa926aad26f724009a683ec
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796116"
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
  
## <a name="remarks"></a>Примечания  
 Если *integer_expression* длиннее, чем *character_expression*, функция возвращает *character_expression*.  
  
 Если *integer_expression* равно нулю, функция возвращает строку нулевой длины.  
  
 Если *integer_expression* является отрицательным числом, функция возвращает ошибку.  
  
 Аргумент *integer_expression* может принимать переменные и столбцы.  
  
 Функция RIGHT работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции RIGHT. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
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
 [LEFT (выражение SSIS)](left-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
