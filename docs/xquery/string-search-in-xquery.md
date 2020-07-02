---
title: Поиск строки в XQuery | Документация Майкрософт
description: Узнайте, как искать текст в XML-документах, просмотрев пример поиска строк в XQuery.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- strings [SQL Server], search
- XML [SQL Server], searching text
- searches [SQL Server], XML documents
- XQuery, string search
ms.assetid: edc62024-4c4c-4970-b5fa-2e54a5aca631
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ae897a8a945c477ce201b4037f3b05dbb13160e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765561"
---
# <a name="string-search-in-xquery"></a>Поиск строки в XQuery
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  В этом подразделе приведены примеры запросов, показывающие, как производится поиск текста в XML-документах.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-find-feature-descriptions-that-contain-the-word-maintenance-in-the-product-catalog"></a>A. Поиск описаний характеристик, содержащих слово «maintenance», в каталоге продуктов  
  
```  
SELECT CatalogDescription.query('  
     declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    for $f in /p1:ProductDescription/p1:Features/*  
     where contains(string($f), "maintenance")  
     return  
           $f ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 В предыдущем запросе `where` выражение в выражении Flow фильтрует результат `for` выражения и возвращает только те элементы, которые соответствуют условию **Contains ()** .  
  
 Результат:  
  
```  
<p1:Maintenance     
      xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
 <p1:NoOfYears>10</p1:NoOfYears>  
 <p1:Description>maintenance contact available through your   
               dealer or any AdventureWorks retail store.</p1:Description>  
</p1:Maintenance>  
```  
  
## <a name="see-also"></a>См. также  
 [SQL Server &#40;XML-данных&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)  
  
  
