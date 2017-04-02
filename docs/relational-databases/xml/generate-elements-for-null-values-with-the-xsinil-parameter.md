---
title: "Создание элементов для значений NULL с помощью параметра XSINIL | Microsoft Docs"
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
  - "предложение FOR XML, значения NULL"
  - "значения NULL [SQL Server], XML"
  - "ELEMENTS, директива"
  - "XSINIL, параметр"
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Создание элементов для значений NULL с помощью параметра XSINIL
  Директива **ELEMENTS** формирует XML, в котором каждое значение в столбце соответствует элементу XML. Если этот значение в столбце имеет значение NULL, элемент не добавляется. Указав в директиве ELEMENTS необязательный параметр **XSINIL** , можно запросить, чтобы для значений NULL тоже создавались элементы. В этом случае атрибут **xsi:nil** этого элемента имеет значение TRUE для каждого значения NULL в столбце.  
  
## См. также:  
 [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  