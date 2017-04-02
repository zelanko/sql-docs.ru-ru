---
title: "LOWER (выражение служб SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "преобразование верхнего регистра в нижний"
  - "LOWER, функция"
  - "символы в верхнем регистре [службы Integration Services]"
  - "символы в нижнем регистре"
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LOWER (выражение служб SSIS)
  Возвращает символьное выражение после преобразования всех символов верхнего регистра в нижний.  
  
## Синтаксис  
  
```  
  
LOWER(character_expression)  
```  
  
## Аргументы  
 *character_expression*  
 Символьное выражение для преобразования символов в нижний регистр.  
  
## Типы результата  
 DT_WSTR  
  
## Замечания  
 Функция LOWER работает только с типом данных DT_WSTR. Аргумент *character_expression*, являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции LOWER. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Функция LOWER возвращает NULL, если аргумент имеет значение NULL.  
  
## Примеры выражений  
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
  
## См. также  
 [UPPER (выражение служб SSIS)](../../integration-services/expressions/upper-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  