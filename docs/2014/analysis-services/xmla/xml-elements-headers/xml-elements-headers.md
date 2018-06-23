---
title: Заголовки (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: bb2cff2e70ccd1ac0cf391f7832db4978a415f56
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190610"
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
 [XML-элементы &#40;XML для Аналитики&#41;](../../dev-guide/xml-elements-xmla.md)   
 [Типы данных XML &#40;XML для Аналитики&#41;](../xml-data-types/xml-data-types-xmla.md)   
 [XML-элементы &#40;XML для Аналитики&#41;](../../dev-guide/xml-elements-xmla.md)  
  
  