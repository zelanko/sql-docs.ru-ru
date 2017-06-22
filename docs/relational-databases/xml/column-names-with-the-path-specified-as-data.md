---
title: "Имена столбцов с путем, указанным как data() | Документация Майкрософт"
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
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7684de73d40f3ac587f0307d904931c99a9a822a
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="column-names-with-the-path-specified-as-data"></a>Имена столбцов с путем, указанным как data()
  Если путь для имени столбца указан как «data()», то в сформированном XML-документе его значение обрабатывается как атомарное. Если следующий элемент последовательности также является элементарным значением, в XML-документ добавляется символ пробела. Это может пригодиться при создании списка типизированных элементов и значений атрибутов. Следующий запрос извлекает код модели продукции, ее имя и список продуктов этой модели.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 Вложенная инструкция SELECT извлекает список кодов продуктов. Имя столбца для кодов продуктов в нем указано как «data()». Поскольку режим PATH указывает для имени элемента строки пустую строку, формирования элемента строки не происходит. Вместо этого возвращаются значения, назначенные атрибуту ProductIDs элемента строки <`ProductModelData`> в родительской инструкции SELECT. Результат:  
  
 `<ProductModelData ProductModelID="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 888 889 890 891 892 893" />`  
  
## <a name="see-also"></a>См. также:  
 [Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
