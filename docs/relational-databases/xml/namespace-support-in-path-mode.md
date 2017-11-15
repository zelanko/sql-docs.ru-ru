---
title: "Поддержка пространства имен в режиме PATH | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 142105e53a75f3e7ccabd0ad4f60467c212f4363
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="namespace-support-in-path-mode"></a>Поддержка пространства имен в режиме PATH
  Поддержка пространства имен в режиме PATH осуществляется с помощью предложения WITH NAMESPACES. Например, в следующем запросе синтаксис WITH NAMESPACES применяется для объявления пространства имен («a:»), которое затем можно использовать в последующей инструкции SELECT.  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>Примеры  
 В этих примерах показано использование режима PATH при формировании XML-документа из запроса SELECT. Многие из этих запросов являются запросами к XML-документам с инструкциями по производству велосипедов, хранящимся в столбце Instructions таблицы ProductModel.  
  
## <a name="see-also"></a>См. также:  
 [Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
