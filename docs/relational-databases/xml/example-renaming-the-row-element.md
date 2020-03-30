---
title: Пример. Переименование элемента &lt;row&gt; | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 275b1c6c138b11fa6330dc61fbfbfd2014a229c5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68006812"
---
# <a name="example-renaming-the-ltrowgt-element"></a>Пример. Переименование элемента &lt;row&gt;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Для каждой строки результирующего набора режим RAW создает элемент `<row>`. При необходимости можно задать другое имя для этого элемента путем определения дополнительного аргумента в режиме RAW, как показано в данном запросе. Запрос возвращает элемент <`ProductModel`> для каждой строки из набора строк.  
  
## <a name="example"></a>Пример  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 Результат. Из-за того, что в запрос добавлена директива `ELEMENTS` , результат состоит из элементов.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>См. также:  
 [Использование RAW Mode с FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
