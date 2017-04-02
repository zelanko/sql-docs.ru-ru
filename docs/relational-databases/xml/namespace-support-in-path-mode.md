---
title: "Поддержка пространства имен в режиме PATH | Microsoft Docs"
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
  - "Режим PATH FOR XML, поддержка пространства имен"
  - "пространства имен [XML в SQL Server]"
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Поддержка пространства имен в режиме PATH
  Поддержка пространства имен в режиме PATH осуществляется с помощью предложения WITH NAMESPACES. Например, в следующем запросе синтаксис WITH NAMESPACES применяется для объявления пространства имен («a:»), которое затем можно использовать в последующей инструкции SELECT.  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## Примеры  
 В этих примерах показано использование режима PATH при формировании XML-документа из запроса SELECT. Многие из этих запросов являются запросами к XML-документам с инструкциями по производству велосипедов, хранящимся в столбце Instructions таблицы ProductModel.  
  
## См. также:  
 [Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  