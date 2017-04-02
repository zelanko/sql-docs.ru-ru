---
title: "NULL (выражение служб SSIS) | Microsoft Docs"
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
  - "NULL, функция"
  - "значения NULL [службы Integration Services]"
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# NULL (выражение служб SSIS)
  Возвращает значение NULL запрошенного типа данных.  
  
## Синтаксис  
  
```  
  
NULL(typespec)  
```  
  
## Аргументы  
 *typespec*  
 Допустимый тип данных. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Типы результата  
 Любой допустимый тип данных со значением NULL.  
  
## Замечания  
 Функция NULL возвращает NULL, если аргумент NULL.  
  
 Для некоторых типов данных чтобы запросить значения NULL, необходимы параметры. В следующей таблице приведены эти типы данных и их параметры.  
  
|Тип данных|Параметр|Пример|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|(DT_STR,30,1252) приводит 30 символов к типу данных DT_STR, используя кодовую страницу 1252.|  
|DT_WSTR|*charcount*|(DT_WSTR,20) приводит 20 символов к типу данных DT_WSTR.|  
|DT_BYTES|*bytecount*|(DT_BYTES,50) приводит 50 байт к типу данных DT_BYTES.|  
|DT_DECIMAL|*масштаб*|(DT_DECIMAL,2) приводит числовое значение к типу данных DT_DECIMAL, используя масштаб 2.|  
|DT_NUMERIC|*precision*<br /><br /> *масштаб*|(DT_NUMERIC,10,3) приводит числовое значение к типу данных DT_NUMERIC, используя точность 10 и масштаб 3.|  
|DT_TEXT|*codepage*|(DT_TEXT,1252) приводит значение к типу данных DT_TEXT, используя кодовую страницу 1252.|  
  
## Примеры выражений  
 Эти примеры возвращают значение NULL следующих типов данных: DT_STR, DT_DATE и DT_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## См. также  
 [ISNULL (выражение служб SSIS)](../../integration-services/expressions/isnull-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  