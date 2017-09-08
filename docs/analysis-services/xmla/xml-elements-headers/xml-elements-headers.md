---
title: "Заголовки (XMLA) | Документы Microsoft"
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
helpviewer_keywords:
- XMLA, headers
- SOAP headers [XML for Analysis]
- XML for Analysis, headers
- headers [XML for Analysis]
ms.assetid: 36407b5c-d98d-47e4-8d36-d8896e15a748
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b12c8b2b22d51069998b4b49d1c9aceb43f063a5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---headers"></a>Элементы XML - заголовки
  В протоколе XMLA предусматривается использование элементов XML в заголовке SOAP для управления функциями на уровне протокола, такими как поддержка сеансов и согласование поддерживаемых функций.  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих разделах описываются элементов заголовка XMLA, реализуемый [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Метод|Description|  
|------------|-----------------|  
|[Элемент BeginSession &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для запуска нового сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент EndSession &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для завершения существующего сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент Session &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для идентификации существующего, явно определенного сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент ProtocolCapabilities &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для обозначения возможностей протокола обмена данными между экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и клиентским приложением.|  
  
## <a name="see-also"></a>См. также:  
 [XML-элементы &#40; XML для Аналитики &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Типы данных XML &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [XML-элементы &#40; XML для Аналитики &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
