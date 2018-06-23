---
title: Пример. Запросы к столбцам XMLType | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RAW mode, querying XML example
ms.assetid: d9f3710d-7a2e-4abe-9c02-3e3c0df4d620
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0ccfde903ae66af77f7d37e9c6cb70b891e60268
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193320"
---
# <a name="example-querying-xmltype-columns"></a>Пример. Запросы к столбцам XMLType
  Следующий запрос включены столбцы типа `xml` типа. Запрос возвращает идентификатор модели продукта, имя и шаги производства в первом месте из столбца `Instructions` типа `xml`.  
  
## <a name="example"></a>Пример  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
')   
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
GO  
```  
  
 Ниже показан результат. Следует заметить, что в таблице содержатся инструкции по производству продукта только для некоторых моделей продукта. Этапы производства возвращаются в качества подэлементов элемента <`ProductModelData`> в итоговом документе.  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
    <MI:step> ... </MI:step>  
    <MI:step> ... </MI:step>  
 </ProductModelData>  
```  
  
 Если в запросе задано имя столбца для XML-документа, возвращаемого XQuery, так как это задано в следующей инструкции `SELECT`, то шаги производства помещаются в элемент, имеющий указанное имя.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
go  
```  
  
 Результат:  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
  <ManuSteps>  
    <MI:step ... </MI:step>  
    <MI:step ... </MI:step>  
  </ManuSteps>  
</ProductModelData>  
```  
  
 В следующем запросе задана директива `ELEMENTS` . Поэтому результат будет состоять из элементов. Параметр `XSINIL`, заданный вместе с директивой `ELEMENTS`, возвращает элементы <`ManuSteps`>, даже если соответствующий столбец в наборе строк имеет значение NULL.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData'), root('MyRoot'), ELEMENTS XSINIL  
go  
```  
  
 Результат:  
  
```  
<MyRoot xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   ...  
  <ProductModelData>  
    <ProductModelID>6</ProductModelID>  
    <Name>HL Road Frame</Name>  
    <ManuSteps xsi:nil="true" />  
  </ProductModelData>  
  <ProductModelData>  
    <ProductModelID>7</ProductModelID>  
    <Name>HL Touring Frame</Name>  
    <ManuSteps>  
      <MI:step ... </MI:step>  
      <MI:step ...</MI:step>  
       ...  
    </ManuSteps>  
  </ProductModelData>  
</MyRoot>  
```  
  
## <a name="see-also"></a>См. также  
 [Использование с RAW Mode для FOR XML](use-raw-mode-with-for-xml.md)  
  
  