---
title: "Пример. Указание директивы HIDE | Документация Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HIDE directive
ms.assetid: 87504d87-1cbd-412a-9041-47884b6efcec
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f76513d7db83b1b24f3fd5964689c47f5b96133b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="example-specifying-the-hide-directive"></a>Примеры. Указание директивы HIDE
  Этот пример демонстрирует использование директивы **HIDE** . Эта директива полезна, если требуется, чтобы запрос возвращал атрибут сортировки строк в универсальной таблице, возвращаемой запросом, но этот атрибут не должен появиться в конечном XML-документе.  
  
 Этот запрос создает соответствующий XML:  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
           <Summary> element from XML stored in CatalogDescription column  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Этот запрос формирует желаемый XML. В запросе задаются две группы столбцов со значениями Tag, равными 1 и 2, в именах столбцов.  
  
 В этом запросе используется [метод query() (тип данных xml)](../../t-sql/xml/query-method-xml-data-type.md) типа данных **xml** для выполнения запроса к столбцу CatalogDescription типа **xml** с целью получения описания итога. В запросе также используется [метод value() (тип данных xml)](../../t-sql/xml/value-method-xml-data-type.md) типа данных **xml** для получения значения ProductModelID из столбца CatalogDescription. Это значение не должно присутствовать в конечном XML, но оно необходимо для сортировки конечного набора строк. Поэтому имя столбца, `[Summary!2!ProductModelID!HIDE]`, включает директиву **HIDE** . Если этот столбец не включен в инструкцию SELECT, то набор строк придется отсортировать по столбцам `[ProductModel!1!ProdModelID]` и `[Summary!2!SummaryDescription]` , которые имеют тип **xml** , а использовать столбцы типа **xml** в предложении ORDER BY нельзя. Поэтому добавляется дополнительный столбец `[Summary!2!ProductModelID!HIDE]` , который затем указывается в предложении ORDER BY.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID     as [ProductModel!1!ProdModelID],  
        Name               as [ProductModel!1!Name],  
        NULL               as [Summary!2!ProductModelID!hide],  
        NULL               as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
        CatalogDescription.value('  
         declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       (/PD:ProductDescription/@ProductModelID)[1]', 'int'),  
        CatalogDescription.query('  
         declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /pd:ProductDescription/pd:Summary')  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],[Summary!2!ProductModelID!hide]  
FOR XML EXPLICIT  
go  
```  
  
 Результат:  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <pd:Summary xmlns:pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription" xmlns="">  
        <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike. Performance-enhancing options include the innovative HL Frame, super-smooth front suspension, and traction for all terrain. </p1:p>  
      </pd:Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование режима EXPLICIT совместно с предложением FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  

