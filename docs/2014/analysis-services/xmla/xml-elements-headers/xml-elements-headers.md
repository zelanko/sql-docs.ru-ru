---
title: Заголовки (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XMLA, headers
- SOAP headers [XML for Analysis]
- XML for Analysis, headers
- headers [XML for Analysis]
ms.assetid: 36407b5c-d98d-47e4-8d36-d8896e15a748
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fdc6c9ebfef18b108c31870c5703cac3841cfc29
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155703"
---
# <a name="headers-xmla"></a>Заголовки (XML для аналитики)
  В протоколе XMLA предусматривается использование элементов XML в заголовке SOAP для управления функциями на уровне протокола, такими как поддержка сеансов и согласование поддерживаемых функций.  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих разделах описываются элементов заголовка XMLA, реализуемый [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Метод|Описание|  
|------------|-----------------|  
|[Элемент BeginSession &#40;XML для Аналитики&#41;](session-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для запуска нового сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент EndSession &#40;XML для Аналитики&#41;](endsession-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для завершения существующего сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент Session &#40;XML для Аналитики&#41;](session-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для идентификации существующего, явно определенного сеанса в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Элемент ProtocolCapabilities &#40;XML для Аналитики&#41;](protocolcapabilities-element-xmla.md)|Использует заголовок SOAP в сообщении SOAP-запроса для обозначения возможностей протокола обмена данными между экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и клиентским приложением.|  
  
## <a name="see-also"></a>См. также  
 [XML-элементов &#40;XML для Аналитики&#41;](../../dev-guide/xml-elements-xmla.md)   
 [Типы данных XML &#40;XML для Аналитики&#41;](../xml-data-types/xml-data-types-xmla.md)   
 [XML-элементов &#40;XML для Аналитики&#41;](../../dev-guide/xml-elements-xmla.md)  
  
  
