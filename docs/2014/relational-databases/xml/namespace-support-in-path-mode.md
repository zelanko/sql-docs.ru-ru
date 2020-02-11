---
title: Поддержка пространства имен в режиме PATH | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad1a6af717dcfa8ea42d9171e5ab23d9c24c6225
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63240788"
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
 [Использование режима PATH совместно с FOR XML](use-path-mode-with-for-xml.md)  
  
  
