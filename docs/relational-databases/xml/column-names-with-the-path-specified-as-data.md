---
title: Имена столбцов с путем, указанным как data() | Документация Майкрософт
description: Сведения о запросах XML, содержащих имена столбцов с путем, указанным как data().
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 71cddb62a7277d32d9f43f499c83f3df9e9f69d6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775590"
---
# <a name="column-names-with-the-path-specified-as-data"></a>Имена столбцов с путем, указанным как data()

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Если путь для имени столбца указан как «data()», то в сформированном XML-документе его значение обрабатывается как атомарное. Если следующий элемент последовательности также является элементарным значением, в XML-документ добавляется символ пробела. Это может пригодиться при создании списка типизированных элементов и значений атрибутов. Следующий запрос извлекает код модели продукции, ее имя и список продуктов этой модели.  
  
```sql
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
  
 Вложенная инструкция SELECT извлекает список кодов продуктов. Имя столбца для кодов продуктов в нем указано как «data()». Поскольку режим PATH указывает для имени элемента строки пустую строку, формирования элемента строки не происходит. Вместо этого возвращаются значения, назначенные атрибуту ProductIDs элемента строки `<ProductModelData>` в родительской инструкции SELECT. Результат:  

```sql
<ProductModelData
  ProductModelID="7"
  ProductModelName="HL Touring Frame"
  ProductIDs="885 887 888 889 890 891 892 893"
/>
```

## <a name="see-also"></a>См. также:  
 [Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
