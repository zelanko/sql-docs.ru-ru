---
title: Создание представлений для столбцов XML | Документация Майкрософт
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40c91548b4bf106f938f4bce8298a162937e7ffc
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664600"
---
# <a name="create-views-over-xml-columns"></a>Создание представления для XML-столбцов
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Чтобы создавать представления, можно использовать столбец типа **xml** . В следующем примере создается представление, в котором для получения значения из столбца типа `xml` используется метод **value()** типа данных **xml** .  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 Выполните следующий запрос к представлению:  
  
```  
SELECT *   
FROM   MyView  
```  
  
 Результат:  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 Обратите внимание на следующие аспекты использования типа данных **xml** при создании представлений:  
  
-   тип данных xml может быть создан в материализованном представлении. Материализованное представление не может быть основано на методе типа данных xml. Однако они могут быть приведены к коллекции XML-схем, отличающейся от столбца типа xml базовой таблицы;  
  
-   тип данных **xml** нельзя использовать в распределенных секционированных представлениях;  
  
-   выполнение предикатов SQL по отношению к представлению не будет включено в выражения XQuery определения этого представления;  
  
-   обновление методов типа данных xml в представлениях невозможно.  
  
  
