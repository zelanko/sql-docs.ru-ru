---
title: Пример. Переименование элемента &lt;row&gt; | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 082bbb9ce94b8f3b2625176e27f4c088ffef3b8b
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888520"
---
# <a name="example-renaming-the-ltrowgt-element"></a>Пример. Переименование элемента &lt;row&gt;
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
  
## <a name="see-also"></a>См. также  
 [Использование с RAW Mode для FOR XML](use-raw-mode-with-for-xml.md)  
  
  
