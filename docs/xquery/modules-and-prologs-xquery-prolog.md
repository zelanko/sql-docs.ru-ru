---
title: Пролог XQuery | Документация Майкрософт
description: Сведения о прологе XQuery, содержащем ряд объявлений и определений, которые создают необходимую среду для обработки запросов.
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
- namespaces [XQuery]
- default namespace declarations
ms.assetid: 03924684-c5fd-44dc-8d73-c6ab90f5e069
author: rothja
ms.author: jroth
ms.openlocfilehash: 8098ddebb61a33c017f22598bec16041f112097a
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918491"
---
# <a name="modules-and-prologs---xquery-prolog"></a>Модули и прологи — пролог XQuery
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]

  Запрос XQuery состоит из пролога и текста запроса. Пролог XQuery является набором объявлений и определений, создающим требуемую для обработки запроса среду. На сервере SQL Server, в прологе XQuery могут содержаться объявления пространств имен. Текст запроса XQuery состоит из последовательности выражений, которые определяют желаемый результат запроса.  
  
 Например, следующий запрос XQuery задается для столбца Instructions типа **XML** , который хранит инструкции по производству в виде XML. Запрос получает инструкции по производству продукта для производственного цеха `10`. `query()`Метод типа данных **XML** используется для указания языка XQuery.  
  
```  
SELECT Instructions.query('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') AS Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Пролог XQuery содержит объявление префикса пространства имен (AWMI), `(namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";` .  
  
-   Ключевое слово `declare namespace` определяет префикс пространств имен, который впоследствии используется в теле запроса.  
  
-   `/AWMI:root/AWMI:Location[@LocationID="10"]` является текстом запроса.  
  
## <a name="namespace-declarations"></a>Объявление пространств имен  
 Объявление пространств имен задает префикс и связывает его с URI-кодом пространства имен, как показано в следующем запросе. В запросе `CatalogDescription` является столбцом типа **XML** .  
  
 В определенном запросе XQuery для этого столбца пролог запроса определяет объявление `declare namespace`, которое связывает префикс `PD`, описание продукта с URI-кодом пространства имен. Затем этот префикс используется в теле запроса вместо URI-кода пространства имен. Узлы результирующего XML находятся в пространстве имен, связанном с URI-кодом пространства имен.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Чтобы упростить понимание запроса, можно объявлять пространства имен при помощи WITH XMLNAMESPACES, а не путем объявления префиксов и пространств имен, связанных в прологе запроса при помощи `declare namespace`.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
  
SELECT CatalogDescription.query('  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Дополнительные сведения см. в разделе [Добавление пространств имен в запросы с помощью предложения WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md).  
  
### <a name="default-namespace-declaration"></a>Установленные по умолчанию объявления пространств имен  
 Вместо объявления префикса пространства при помощи объявления `declare namespace` можно использовать объявление `declare default element namespace` для привязки заданного по умолчанию пространства имен к именам элементов. В этом случае не нужно задавать префикс.  
  
 В следующем примере выражение пути в теле запроса не определяет префикс пространства имен. По умолчанию все имена элементов, принадлежащие заданному по умолчанию пространству имен, определяются в прологе.  
  
```  
SELECT CatalogDescription.query('  
     declare default element namespace  "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
 Можно объявить заданное по умолчанию пространство имен при помощи WITH XMLNAMESPACES:  
  
```  
WITH XMLNAMESPACES (DEFAULT 'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription')  
SELECT CatalogDescription.query('  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
## <a name="see-also"></a>См. также  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)  
  
  
