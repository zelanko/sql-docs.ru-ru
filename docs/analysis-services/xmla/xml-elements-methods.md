---
title: "Методы (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#
helpviewer_keywords:
- methods [XML for Analysis]
- XML for Analysis, methods
- XMLA, methods
ms.assetid: c6768dd4-ca06-4a85-93b7-5fd5700886ad
caps.latest.revision: 30
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d7e9b7f9ee860b8ff65664d15b17ca9ebe182e15
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---methods"></a>Элементы XML - методы
  Протокол XML для аналитики (XMLA) используется два метода, **Discover** и **Execute**, которые предлагают стандартный способ для приложений для доступа к данным в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Поскольку эти методы вызываются при помощи протокола SOAP, они получают входные данные и предоставляют результаты в формате XML. В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] реализованы оба метода в соответствии со спецификацией XML для аналитики 1.1.  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих разделах описываются методы XML для аналитики, реализованные в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Метод|Description|  
|------------|-----------------|  
|[Обнаружение метод &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)|Получает сведения, такие как список доступных баз данных или подробные сведения о конкретном объекте, из экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Данные, полученные с помощью метода **Discover** , зависят от значений параметров, переданных этому методу.|  
|[Выполнение метода &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)|Отправляет команды XMLA на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Сюда входят запросы, связанные с передачей данных, например извлечение или обновление данных на сервере.|  
  
## <a name="see-also"></a>См. также:  
 [XML-элементы &#40; XML для Аналитики &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Типы данных XML &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [XML-элементы &#40; XML для Аналитики &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
