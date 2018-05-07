---
title: Заголовки (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f0e0c74a34a5a1e9632caf052893f2944cf9ffc4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="xml-elements---headers"></a>Элементы XML - заголовки
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  В протоколе XMLA предусматривается использование элементов XML в заголовке SOAP для управления функциями на уровне протокола, такими как поддержка сеансов и согласование поддерживаемых функций.  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих разделах описываются элементов заголовка XMLA, реализуемый [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Метод|Description|  
|------------|-----------------|  
|[Элемент BeginSession & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для запуска нового сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент EndSession & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для завершения существующего сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент Session & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для идентификации существующего, явно определенного сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент ProtocolCapabilities & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для обозначения возможностей протокола обмена данными между экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и клиентским приложением.|  
  
## <a name="see-also"></a>См. также:  
 [XML-элементы & #40; XML для Аналитики & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Типы данных XML & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [XML-элементы & #40; XML для Аналитики & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
