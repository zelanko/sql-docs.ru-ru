---
title: "LOWER (выражение служб SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
caps.latest.revision: "33"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7dae07861849917d59935aeef20ef91f8d65408e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="lower-ssis-expression"></a>LOWER (выражение служб SSIS)
  Возвращает символьное выражение после преобразования всех символов верхнего регистра в нижний.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение для преобразования символов в нижний регистр.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Замечания  
 Функция LOWER работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции LOWER. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Функция LOWER возвращает NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример преобразует символы строкового литерала в символы нижнего регистра. Возвращенный результат — «new york».  
  
```  
LOWER("New York")  
```  
  
 Этот пример преобразует все символы из входного столбца **Color** , кроме первого символа, в символы нижнего регистра. Если значение Color равно «YELLOW», возвращенный результат будет «Yellow». Дополнительные сведения см. в разделе [SUBSTRING (выражение служб SSIS)](../../integration-services/expressions/substring-ssis-expression.md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 Пример преобразует значение переменной **CityName** в символы нижнего регистра.  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a>См. также  
 [UPPER (выражение служб SSIS)](../../integration-services/expressions/upper-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
