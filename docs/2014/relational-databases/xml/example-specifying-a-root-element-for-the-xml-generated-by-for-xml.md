---
title: Пример. Задание корневого элемента для XML-документа, сформированного предложением FOR XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying root element example
- RAW mode, with FOR XML example
ms.assetid: bcc54b11-0713-4e43-8dbe-d6f3ad1993b5
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8b2d59080f9e6df980f96ccfca20c728d72924ff
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889730"
---
# <a name="example-specifying-a-root-element-for-the-xml-generated-by-for-xml"></a>Пример. Задание корневого элемента для XML-документа, сформированного предложением FOR XML
  Путем определения параметра `ROOT` в запросе `FOR XML` можно выполнить запрос одного элемента высшего уровня для итогового XML-документа, как показано в этом запросе. Данный аргумент, определенный для директивы `ROOT` , задает имя корневого элемента.  
  
## <a name="example"></a>Пример  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119 or ProductModelID=115  
FOR XML RAW, ROOT('MyRoot')  
go  
```  
  
 Результат:  
  
```  
<MyRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
  <row ProductModelID="115" Name="Cable Lock" />  
</MyRoot>  
```  
  
## <a name="see-also"></a>См. также  
 [Использование с RAW Mode для FOR XML](use-raw-mode-with-for-xml.md)  
  
  
