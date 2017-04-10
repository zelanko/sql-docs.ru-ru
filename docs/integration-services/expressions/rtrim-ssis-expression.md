---
title: "RTRIM (выражение служб SSIS) | Microsoft Docs"
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
  - "RTRIM, функция"
  - "конечные пробелы"
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# RTRIM (выражение служб SSIS)
  Возвращает символьное выражение после удаления конечных пробелов.  
  
> [!NOTE]  
>  RTRIM не удаляет пробельные символы, такие как символы табуляции и символы перехода на новую строку. Юникод обеспечивает элементы кода для множества различных типов пробелов, однако данная функция распознает только элемент кода 0x0020 в Юникоде. Если строки двухбайтовой кодировки (DBCS) преобразованы в Юникод, они могут включать пробелы, отличные от 0x0020. Тогда функция не в состоянии удалить такие пробелы. Для удаления всех видов пробелов можно использовать метод Microsoft Visual Basic .NET RTrim в скрипте, выполняемом из компонента скриптов.  
  
## Синтаксис  
  
```  
  
RTRIM(character expression)  
```  
  
## Аргументы  
 *character_expression*  
 Символьное выражение, из которого удаляются пробелы.  
  
## Типы результата  
 DT_WSTR  
  
## Замечания  
 Метод RTRIM работает только с типом данных DT_WSTR. Аргумент *character_expression*, являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции RTRIM. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../../integration-services/data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Метод RTRIM возвращает значение NULL, если значением аргумента является NULL.  
  
## Примеры выражений  
 В этом примере удаляются конечные пробелы из строкового литерала. Возвращаемый результат — «Hello».  
  
```  
RTRIM("Hello   ")  
```  
  
 В этом примере удаляются конечные пробелы из объединения столбцов **FirstName** и **LastName** .  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 В этом примере удаляются конечные пробелы из переменной **FirstName** .  
  
```  
RTRIM(@FirstName)  
```  
  
## См. также  
 [LTRIM (выражение служб SSIS)](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [TRIM (выражение служб SSIS)](../../integration-services/expressions/trim-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  