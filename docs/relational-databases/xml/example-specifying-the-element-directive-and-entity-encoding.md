---
title: Пример. Указание директивы ELEMENT и кодировка сущности | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 953878b10ee3b83e2425642b6669efacbbcef3b2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33013611"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a>Пример. Указание директивы ELEMENT и кодировка сущности
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Этот пример демонстрирует различие между директивами **ELEMENT** и **XML** . Директива **ELEMENT** преобразует данные в сущность, а директива **XML** не делает этого. Элемент \<Summary> представляет XML `<Summary>This is summary description</Summary>`, назначенный в запросе.  
  
 Рассмотрим следующий запрос:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Результат. Описание итога преобразуется в результате в сущность.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Теперь, если указать директиву **XML** в имени столбца, `Summary!2!SummaryDescription!XML`, вместо директивы **ELEMENT** , будет получено описание сводки без преобразования в сущность.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Вместо присвоения статического значения XML в следующем запросе используется метод **query()** типа **xml** для получения описания итога модели продукта из столбца CatalogDescription типа **xml** . Так как известно, что результат будет иметь тип **xml** , преобразование в сущность не применяется.  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование режима EXPLICIT совместно с предложением FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
