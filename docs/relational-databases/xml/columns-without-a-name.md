---
title: "Столбцы без имени | Microsoft Docs"
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
  - "имена [SQL Server], столбцы без"
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Столбцы без имени
  Любой столбец, не имеющий имени, будет встроенным. Например, вычисляемые столбцы или вложенные скалярные запросы, в которых не задан псевдоним столбца, формируют столбцы без имени. Если столбец имеет тип данных **xml** , в него помещается содержимое экземпляра этого типа данных. В противном случае содержимое столбца вставляется как текстовый узел.  
  
```  
SELECT 2+2  
FOR XML PATH  
```  
  
 Создание этого XML. По умолчанию для каждой строки в наборе строк в итоговом XML-документе формируется элемент <`row`>. То же самое происходит в режиме RAW.  
  
 `<row>4</row>`  
  
 Следующий запрос возвращает набор строк с тремя столбцами. Третий столбец, без названия, содержит XML-данные. Режим PATH вставляет экземпляр типа xml.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 Частичный результат:  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location ...LocationID="10" ...></MI:Location>`  
  
 `<MI:Location ...LocationID="20" ...></MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## См. также:  
 [Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  