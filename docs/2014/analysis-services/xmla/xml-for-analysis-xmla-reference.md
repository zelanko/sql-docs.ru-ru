---
title: XML для аналитики (XMLA) ссылку | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fde04360c7b6af1c9bf6aa906328e5031eb76c32
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164444"
---
# <a name="xml-for-analysis--xmla-reference"></a>XML для аналитики (XMLA) ссылки
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] использует протокол XML для аналитики (XMLA) для обеспечения взаимодействия между клиентскими приложениями и экземпляром служб Analysis Services. На самом базовом уровне другие клиентские библиотеки, такие как ADOMD.NET и объекты AMO, составляют запросы и декодируют ответы в XMLA, образуя промежуточный слой для экземпляра служб Analysis Services, который использует исключительно XMLA.  
  
 Для поддержки обнаружения и управления данными в многомерном и табличном форматах, спецификации XMLA было определено два общедоступных метода [Discover](xml-elements-methods-discover.md) и [Execute](xml-elements-methods-execute.md)и Коллекция элементов и типов данных XML. Поскольку в XML допускается существование слабосвязанной архитектуры клиент-сервер, оба этих метода обрабатывают входящую и исходящую информацию в формате XML. Службы Analysis Services соответствуют спецификации XMLA 1.1, а также расширяют ее, добавляя возможности описания данных и обработки данных, которые реализованы в виде заметок к методам `Discover` и `Execute`. Расширенный XML-синтаксис называется языком ASSL. Язык ASSL построен на основе спецификации XMLA и не нарушает ее. Совместимость в рамках XMLA гарантируется и при использовании только XMLA, и при совместном использовании XMLA и ASSL.  
  
 Программист может использовать XMLA в качестве интерфейса программирования, если для решения требуются стандартные протоколы, такие как XML, SOAP и HTTP. Программисты и администраторы также могут использовать XMLA в специальных случаях для получения сведений с сервера или выполнения команд.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[XML-элементов &#40;XML для Аналитики&#41;](../dev-guide/xml-elements-xmla.md)|Описывает элементы в спецификации XMLA.|  
|[Типы данных XML &#40;XML для Аналитики&#41;](xml-data-types/xml-data-types-xmla.md)|Описывает типы данных в спецификации XMLA.|  
|[XML для анализа соответствия &#40;XML для Аналитики&#41;](xml-for-analysis-compliance-xmla.md)|Описывает уровень совместимости со спецификацией XMLA 1.1.|  
  
## <a name="related-sections"></a>См. также  
 [Язык сценариев разработки с использованием Analysis Services &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [Наборы строк схемы XML для аналитики](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Разработка с использованием ADOMD.NET](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Разработка объектов управления аналитикой &#40;объектов AMO&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>См. также  
 [Основные сведения об архитектуре Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
