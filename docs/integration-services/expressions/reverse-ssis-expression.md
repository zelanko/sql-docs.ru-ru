---
title: "REVERSE (выражение служб SSIS) | Microsoft Docs"
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
  - "REVERSE, функция"
  - "обратный порядок символов в выражении"
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# REVERSE (выражение служб SSIS)
  Возвращает символьное выражение в обратном порядке.  
  
## Синтаксис  
  
```  
  
REVERSE(character_expression)  
```  
  
## Аргументы  
 *character_expression*  
 Символьное выражение, в котором требуется поменять порядок символов на обратный.  
  
## Типы результата  
 DT_WSTR  
  
## Замечания  
 Аргумент *character_expression* должен иметь тип данных DT_WSTR.  
  
 Функция TOKEN возвращает значение NULL, если строка *character_expression* имеет значение NULL.  
  
## Примеры выражений  
 В данном примере используется строковый литерал. Возвращаемый результат: «ekiB niatnuoM».  
  
```  
REVERSE("Mountain Bike")  
```  
  
 В данном примере используется переменная. Если переменная **Name** содержит выражение «Touring Bike», будет возвращен результат «ekiB gniruoT».  
  
```  
REVERSE(@Name)  
```  
  
## См. также  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  