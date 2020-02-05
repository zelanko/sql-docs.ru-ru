---
title: Определение корневого элемента для использования с FOR XML | Документация Майкрософт
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying root element example
- RAW mode, with FOR XML example
ms.assetid: bcc54b11-0713-4e43-8dbe-d6f3ad1993b5
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: 6ce63dc5a35b9359e24bc410be2a0d53f80cfc99
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75246902"
---
# <a name="example-specifying-a-root-element-for-the-xml-generated-by-for-xml"></a>Пример. Задание корневого элемента для XML-документа, сформированного предложением FOR XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Путем определения параметра `ROOT` в запросе `FOR XML` можно выполнить запрос одного элемента высшего уровня для итогового XML-документа, как показано в этом запросе. Данный аргумент, определенный для директивы `ROOT` , задает имя корневого элемента.  
  
## <a name="example"></a>Пример  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119 or ProductModelID=115  
FOR XML RAW, ROOT('MyRoot')  
GO
```  
  
 Результат:  
  
```  
<MyRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
  <row ProductModelID="115" Name="Cable Lock" />  
</MyRoot>  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование RAW Mode с FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
