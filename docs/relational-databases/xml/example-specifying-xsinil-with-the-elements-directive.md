---
title: "Пример. Указание XSINIL с директивой ELEMENTS | Microsoft Docs"
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
  - "режим RAW, пример указания XSINIL"
ms.assetid: 07c873ff-1f9d-480e-8536-862c39eb8249
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Пример. Указание XSINIL с директивой ELEMENTS
  В этом запросе задается директива `ELEMENTS` для создания из результата запроса элементного XML-документа.  
  
## Пример  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 Частичный результат.  
  
```  
<row>  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
 Так как элементы столбца `Color` для некоторых продуктов имеют значения NULL, то в этих случаях в итоговом XML-документе не будет создаваться соответствующий элемент <`Color`>. Путем добавления к директиве `XSINIL` директивы `ELEMENTS` можно создать элемент <`Color`> даже для значений столбца Color результирующего набора, равных NULL.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS XSINIL ;  
```  
  
 Частичный результат:  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
  <Color xsi:nil="true" />  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
## См. также:  
 [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  