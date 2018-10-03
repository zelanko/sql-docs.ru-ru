---
title: Поддержка пространства имен в режиме PATH | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 19c932a3927e71208e4b1c82c8c3bce4cbadfd8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747042"
---
# <a name="namespace-support-in-path-mode"></a>Поддержка пространства имен в режиме PATH
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
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
  
  
