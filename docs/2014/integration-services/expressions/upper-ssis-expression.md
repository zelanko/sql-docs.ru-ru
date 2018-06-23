---
title: UPPER (выражение служб SSIS) | Документы Майкрософт
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
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fc7b01b83ad0fac1f5da68fcd99ab082cebe89ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192272"
---
# <a name="upper-ssis-expression"></a>UPPER (выражение служб SSIS)
  Возвращает символьное выражение после преобразования символов в нижнем регистре в символы верхнего регистра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение для преобразования в верхний регистр.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Примечания  
 Функция UPPER работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции UPPER. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
 Функция UPPER возвращает значение NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример преобразует строковый литерал в верхний регистр. Возвращаемый результат — «HELLO».  
  
```  
UPPER("hello")  
```  
  
 Этот пример преобразует первый символ столбца **FirstName** в символ верхнего регистра. Если значение **FirstName** — «anna», возвращается результат «A». Дополнительные сведения см. в разделе [SUBSTRING (выражение служб SSIS)](substring-ssis-expression.md).  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 Этот пример преобразует значение переменной **PostalCode** в верхний регистр. Если значение **PostalCode** — «k4b1s2», возвращается результат «K4B1S2».  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a>См. также  
 [НИЖЕ &#40;выражение служб SSIS&#41;](lower-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  