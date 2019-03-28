---
title: Пример Извлечение двоичных данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c39f508d20e194b0031baecf168851cd300031e1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528186"
---
# <a name="example-retrieving-binary-data"></a>Пример Получение двоичных данных
  В следующем запросе возвращается фотография продукта, хранящаяся в столбце с типом данных `varbinary(max)`. Для возвращения двоичных данных в base64-кодированном формате для запроса должен быть определен параметр `BINARY BASE64` .  
  
## <a name="example"></a>Пример  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductPhotoID, ThumbNailPhoto  
FROM Production.ProductPhoto  
WHERE ProductPhotoID=1  
FOR XML RAW, BINARY BASE64 ;  
GO  
```  
  
 Это результат:  
  
```  
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>  
```  
  
## <a name="see-also"></a>См. также  
 [Использование с RAW Mode для FOR XML](use-raw-mode-with-for-xml.md)  
  
  
