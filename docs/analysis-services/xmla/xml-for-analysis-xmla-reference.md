---
title: XML для аналитики (XMLA) ссылку | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 514e886357fe388a344b7b434bf7042bab5375e7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="xml-for-analysis--xmla-reference"></a>XML для аналитики (XMLA) ссылки
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] использует протокол XML для аналитики (XMLA) для обеспечения взаимодействия между клиентскими приложениями и экземпляром служб Analysis Services. На самом базовом уровне другие клиентские библиотеки, такие как ADOMD.NET и объекты AMO, составляют запросы и декодируют ответы в XMLA, образуя промежуточный слой для экземпляра служб Analysis Services, который использует исключительно XMLA.  
  
 Для поддержки обнаружения и управления данными в многомерном и табличном форматах, спецификации XMLA было определено два общедоступных метода [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) и [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)и Коллекция элементов и типов данных XML. Поскольку в XML допускается существование слабосвязанной архитектуры клиент-сервер, оба этих метода обрабатывают входящую и исходящую информацию в формате XML. Службы Analysis Services соответствуют спецификации XMLA 1.1, Спецификация, а также расширяют ее для включения данных определение и изменение возможности реализованы в виде заметок **Discover** и **Execute** методы. Расширенный XML-синтаксис называется языком ASSL. Язык ASSL построен на основе спецификации XMLA и не нарушает ее. Совместимость в рамках XMLA гарантируется и при использовании только XMLA, и при совместном использовании XMLA и ASSL.  
  
 Программист может использовать XMLA в качестве интерфейса программирования, если для решения требуются стандартные протоколы, такие как XML, SOAP и HTTP. Программисты и администраторы также могут использовать XMLA в специальных случаях для получения сведений с сервера или выполнения команд.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[XML-элементы & #40; XML для Аналитики & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)|Описывает элементы в спецификации XMLA.|  
|[Типы данных XML &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Описывает типы данных в спецификации XMLA.|  
|[XML для аналитики соответствия &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Описывает уровень совместимости со спецификацией XMLA 1.1.|  
  
## <a name="related-sections"></a>См. также  
 [Разработка с использованием служб Analysis Services Scripting Language & #40; ASSL & #41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [XML для аналитики наборы строк схемы](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Разработка с использованием ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Разработка с использованием объектов AMO & #40; Объекты AMO & #41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>См. также  
 [Основные сведения об архитектуре Microsoft OLAP](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
