---
title: "XQuery Prolog | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- XQuery, prolog
- prolog
- namespaces [XQuery]
- default namespace declarations
ms.assetid: 03924684-c5fd-44dc-8d73-c6ab90f5e069
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d46786394ce7eb8d6331de98a98ede8999451607
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="modules-and-prologs---xquery-prolog"></a>Модули и Прологи - прологе XQuery
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запрос XQuery состоит из пролога и текста запроса. Пролог XQuery является набором объявлений и определений, создающим требуемую для обработки запроса среду. На сервере SQL Server, в прологе XQuery могут содержаться объявления пространств имен. Текст запроса XQuery состоит из последовательности выражений, которые определяют желаемый результат запроса.  
  
 Например, следующий запрос XQuery задан для столбца Instructions **xml** тип, который хранит промышленные инструкции в формате XML. Запрос получает инструкции по производству продукта для производственного цеха `10`. `query()` Метод **xml** тип данных используется для определения запроса XQuery.  
  
```  
SELECT Instructions.query('declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') AS Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Пролог XQuery содержит объявление пространства имен (AWMI) префикс `(namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";`.  
  
-   Ключевое слово `declare namespace` определяет префикс пространств имен, который впоследствии используется в теле запроса.  
  
-   `/AWMI:root/AWMI:Location[@LocationID="10"]` является текстом запроса.  
  
## <a name="namespace-declarations"></a>Объявление пространств имен  
 Объявление пространств имен задает префикс и связывает его с URI-кодом пространства имен, как показано в следующем запросе. В запросе `CatalogDescription` — **xml** тип столбца.  
  
 В определенном запросе XQuery для этого столбца пролог запроса определяет объявление `declare namespace`, которое связывает префикс `PD`, описание продукта с URI-кодом пространства имен. Затем этот префикс используется в теле запроса вместо URI-кода пространства имен. Узлы результирующего XML находятся в пространстве имен, связанном с URI-кодом пространства имен.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Чтобы упростить понимание запроса, можно объявлять пространства имен при помощи WITH XMLNAMESPACES, а не путем объявления префиксов и пространств имен, связанных в прологе запроса при помощи `declare namespace`.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
  
SELECT CatalogDescription.query('  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Дополнительные сведения см. в разделе, [добавление пространств имен в запросы с WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md).  
  
### <a name="default-namespace-declaration"></a>Установленные по умолчанию объявления пространств имен  
 Вместо объявления префикса пространства при помощи объявления `declare namespace` можно использовать объявление `declare default element namespace` для привязки заданного по умолчанию пространства имен к именам элементов. В этом случае не нужно задавать префикс.  
  
 В следующем примере выражение пути в теле запроса не определяет префикс пространства имен. По умолчанию все имена элементов, принадлежащие заданному по умолчанию пространству имен, определяются в прологе.  
  
```  
SELECT CatalogDescription.query('  
     declare default element namespace  "http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
 Можно объявить заданное по умолчанию пространство имен при помощи WITH XMLNAMESPACES:  
  
```  
WITH XMLNAMESPACES (DEFAULT 'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription')  
SELECT CatalogDescription.query('  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
## <a name="see-also"></a>См. также:  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)  
  
  
