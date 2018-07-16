---
title: Столбцы без имени | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 723ee2f2c9d9da6665c6a9a4b530e3deb247ff2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292164"
---
# <a name="columns-without-a-name"></a>Столбцы без имени
  Любой столбец, не имеющий имени, будет встроенным. Например, вычисляемые столбцы или вложенные скалярные запросы, в которых не задан псевдоним столбца, формируют столбцы без имени. Если столбец имеет `xml` вставляется тип, содержимое экземпляра этого типа данных. В противном случае содержимое столбца вставляется как текстовый узел.  
  
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
  
## <a name="see-also"></a>См. также  
 [Использование режима PATH совместно с FOR XML](use-path-mode-with-for-xml.md)  
  
  
