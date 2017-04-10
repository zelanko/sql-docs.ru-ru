---
title: "Пример. Задание корневого элемента для XML-документа, сформированного предложением FOR XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "режим RAW, пример указания корневого элемента"
  - "режим RAW, пример FOR XML"
ms.assetid: bcc54b11-0713-4e43-8dbe-d6f3ad1993b5
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Пример. Задание корневого элемента для XML-документа, сформированного предложением FOR XML
  Путем определения параметра `ROOT` в запросе `FOR XML` можно выполнить запрос одного элемента высшего уровня для итогового XML-документа, как показано в этом запросе. Данный аргумент, определенный для директивы `ROOT`, задает имя корневого элемента.  
  
## Пример  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119 or ProductModelID=115  
FOR XML RAW, ROOT('MyRoot')  
go  
```  
  
 Результат:  
  
```  
<MyRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
  <row ProductModelID="115" Name="Cable Lock" />  
</MyRoot>  
```  
  
## См. также:  
 [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  