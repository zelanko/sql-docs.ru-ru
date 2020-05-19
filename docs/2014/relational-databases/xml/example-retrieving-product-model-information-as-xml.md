---
title: Пример. Получение сведений о модели продукта в формате XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8cc5eb38cf23b82f61d48941fbf828ff494f3049
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716826"
---
# <a name="example-retrieving-product-model-information-as-xml"></a>Пример. Получение сведений о модели продукта в формате XML
  Приведенный ниже пример запроса выводит сведения о модели продукта. `RAW` указывается в приложении `FOR XML` .  
  
## <a name="example"></a>Пример  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 Частичный результат:  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 Есть возможность получить XML-документ с данными по элементам при помощи определения директивы `ELEMENTS` .  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 Результат:  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 При необходимости можно задать директиву `TYPE` для получения результатов в виде `xml`. Директива `TYPE` не изменяет содержимое результата. Изменяется только тип данных результата.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование RAW Mode с FOR XML](use-raw-mode-with-for-xml.md)  
  
  
