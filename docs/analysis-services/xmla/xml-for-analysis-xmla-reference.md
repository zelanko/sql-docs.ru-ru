---
title: "XML для аналитики (XMLA) ссылку | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 826536d6f28df078b3ca0899176303cbe1a06865
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="xml-for-analysis--xmla-reference"></a>XML для аналитики (XMLA) ссылки
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] использует протокол XML для аналитики (XMLA) для обеспечения взаимодействия между клиентскими приложениями и экземпляром служб Analysis Services. На самом базовом уровне другие клиентские библиотеки, такие как ADOMD.NET и объекты AMO, составляют запросы и декодируют ответы в XMLA, образуя промежуточный слой для экземпляра служб Analysis Services, который использует исключительно XMLA.  
  
 Для поддержки обнаружения и управления данными в многомерном и табличном форматах, спецификации XMLA было определено два общедоступных метода [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) и [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)и Коллекция элементов и типов данных XML. Поскольку в XML допускается существование слабосвязанной архитектуры клиент-сервер, оба этих метода обрабатывают входящую и исходящую информацию в формате XML. Службы Analysis Services соответствуют спецификации XMLA 1.1, Спецификация, а также расширяют ее для включения данных определение и изменение возможности реализованы в виде заметок **Discover** и **Execute** методы. Расширенный XML-синтаксис называется языком ASSL. Язык ASSL построен на основе спецификации XMLA и не нарушает ее. Совместимость в рамках XMLA гарантируется и при использовании только XMLA, и при совместном использовании XMLA и ASSL.  
  
 Программист может использовать XMLA в качестве интерфейса программирования, если для решения требуются стандартные протоколы, такие как XML, SOAP и HTTP. Программисты и администраторы также могут использовать XMLA в специальных случаях для получения сведений с сервера или выполнения команд.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[XML-элементы &#40; XML для Аналитики &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)|Описывает элементы в спецификации XMLA.|  
|[Типы данных XML &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Описывает типы данных в спецификации XMLA.|  
|[XML для аналитики соответствия &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Описывает уровень совместимости со спецификацией XMLA 1.1.|  
  
## <a name="related-sections"></a>См. также  
 [Разработка на языке ASSL (язык ASSL)](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [Наборы строк схемы XML для аналитики](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Разработка с использованием ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Разработка объектов управления аналитикой (объекты AMO)](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения об архитектуре Microsoft OLAP](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
