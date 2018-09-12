---
title: Столбцы с именем, заданным в виде подстановочного символа | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 409d5ae6e546d070f789a56e10b72b265fac0ecc
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889560"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a>Столбцы с именем, заданным в виде символа-шаблона
  Если указанное имя столбца представляет собой подстановочный знак (\*), содержимое этого столбца вставляется, как будто имя столбца не указано. Если этот столбец является отличным от`xml` тип столбца, содержимое столбца вставляется в качестве текстового узла так, как показано в следующем примере:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 Результат:  
  
 `<row EmpID="1">KenJSánchez</row>`  
  
 Если столбец имеет тип -`xml`, вставляется соответствующее дерево XML. Например, в следующем запросе столбец, содержащий XML-данные, возвращенные в результате запроса на языке XQuery к столбцу Instructions, имеет имя «*».  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 Результат. Запрос на языке XQuery возвращает XML-данные, которые вставляются без закрытия элемента.  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a>См. также  
 [Использование режима PATH совместно с FOR XML](use-path-mode-with-for-xml.md)  
  
  
