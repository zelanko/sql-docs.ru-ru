---
title: "Формирование XML-кода с вложенными запросами FOR XML | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9dd8e345930a2e4ed7d036e9969ec8600f85853e
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="shape-xml-with-nested-for-xml-queries"></a>Формирование XML-кода с вложенными запросами FOR XML
  В следующем примере к таблице `Production.Product` выполняется запрос, чтобы получить значения `ListPrice` и `StandardCost` указанного продукта. Чтобы сделать пример более информативным, обе цены возвращаются как элемент <`Price`> и у каждого элемента <`Price`> имеется атрибут `PriceType`.  
  
## <a name="example"></a>Пример  
 Это прогнозируемая форма XML:  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="http://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="http://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="http://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 Это вложенный запрос FOR XML:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Внешняя инструкция SELECT строит элемент <`Product`>, который имеет атрибут **ProductID** и два дочерних элемента <`Price`>.  
  
-   Две внутренние инструкции SELECT создают два элемента <`Price`>, каждый с атрибутом **PriceType**, а также XML, который возвращает цену продукта.  
  
-   Директива XMLSCHEMA во внешней инструкции SELECT создает встроенную XSD-схему, которая описывает форму результирующего XML.  
  
 Чтобы сделать запрос более информативным, можно составить запрос FOR XML, а затем подготовить запрос XQuery к результату для переформирования XML, как показано в следующем запросе:  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 В предыдущем примере метод **query()** типа данных **xml** используется, чтобы запросить XML, возвращаемый внутренним запросом FOR XML, и построить прогнозируемый результат.  
  
 Результат:  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование вложенных запросов FOR XML](../../relational-databases/xml/use-nested-for-xml-queries.md)  
  
  

