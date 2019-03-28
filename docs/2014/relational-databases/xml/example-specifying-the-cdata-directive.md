---
title: Пример Задание директивы CDATA | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- CDATA directive
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa5cec5be4153547d60e1592c21f00470ab1a5fe
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531666"
---
# <a name="example-specifying-the-cdata-directive"></a>Пример Задание директивы CDATA
  Если указана директива **CDATA**, содержащиеся данные не будут закодированы в сущность, а будут помещены в раздел CDATA. Атрибуты **CDATA** должны быть безымянными.  
  
 Следующий запрос упаковывает описания итога модели продукта в раздел CDATA.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Это результат:  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## <a name="see-also"></a>См. также  
 [Использование режима EXPLICIT совместно с предложением FOR XML](use-explicit-mode-with-for-xml.md)  
  
  
