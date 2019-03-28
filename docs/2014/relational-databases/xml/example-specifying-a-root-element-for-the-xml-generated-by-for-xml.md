---
title: Пример Задание корневого элемента для XML, сформированного предложением FOR XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying root element example
- RAW mode, with FOR XML example
ms.assetid: bcc54b11-0713-4e43-8dbe-d6f3ad1993b5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 97b1a4ecc9cfbe0f9f8b793cddc788baf81a2200
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531206"
---
# <a name="example-specifying-a-root-element-for-the-xml-generated-by-for-xml"></a>Пример Задание корневого элемента для XML-документа, сформированного предложением FOR XML
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
  
 Это результат:  
  
```  
<MyRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
  <row ProductModelID="115" Name="Cable Lock" />  
</MyRoot>  
```  
  
## <a name="see-also"></a>См. также  
 [Использование с RAW Mode для FOR XML](use-raw-mode-with-for-xml.md)  
  
  
