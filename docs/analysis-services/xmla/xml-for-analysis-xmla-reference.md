---
title: XML для аналитики (XMLA) ссылку | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e8c3645175d8d1f3251fd621825f5a542669cbb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576766"
---
# <a name="xml-for-analysis--xmla-reference"></a>XML для аналитики (XMLA) ссылки
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]   

Azure служб Analysis Services и SQL Server Analysis Services используют протокол XML для аналитики (XMLA) для обмена данными между клиентскими приложениями и экземпляром служб Analysis Services. На самом базовом уровне другие клиентские библиотеки, такие как ADOMD.NET и объекты AMO, составляют запросы и декодируют ответы в XMLA, образуя промежуточный слой для экземпляра служб Analysis Services, который использует исключительно XMLA.  
  
 Для поддержки обнаружения и управления данными в табличном и многомерном режимах, спецификации XMLA было определено два общедоступных метода [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) и [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)и Коллекция элементов и типов данных XML. Поскольку в XML допускается существование слабосвязанной архитектуры клиент-сервер, оба этих метода обрабатывают входящую и исходящую информацию в формате XML. 

Службы Analysis Services соответствуют спецификации XMLA 1.1, Спецификация, а также расширяют ее для включения данных определение и изменение возможности реализованы в виде заметок **Discover** и **Execute** методы. Расширенный синтаксис XML: табличный языка скриптов модели (TMSL) и языка сценариев служб Analysis Services (ASSL). 

TMSL приведен синтаксис определение команды и объект модели для баз данных табличной модели на уровне совместимости 1200 и выше. TMSL взаимодействует со службами Analysis Services через протокол XML для Аналитики, где `XMLA.Execute` метод принимает обоих сценариев на основе JSON-инструкции на TMSL, а также традиционного скриптов XML в язык сценариев Analysis Services (ASSL XML для Аналитики). Дополнительные сведения см. в разделе [ссылка табличных языка скриптов модели (TMSL)](../tabular-model-scripting-language-tmsl-reference.md).

ASSL приведен синтаксис определение команды и объект модели для баз данных многомерной модели и табличном режиме уровня совместимости 1103 или ниже. Это определение основана на спецификации XML для Аналитики не нарушает ее. Совместимость в рамках XMLA гарантируется и при использовании только XMLA, и при совместном использовании XMLA и ASSL. Дополнительные сведения см. в разделе [язык сценариев Analysis Services (ASSL для XMLA)](../scripting/analysis-services-scripting-language-assl-for-xmla.md).
  
 Как разработчик можно использовать XML для Аналитики в форме интерфейса, если решения требуются стандартные протоколы, такие как XML, SOAP и HTTP. Разработчики и Администраторы также можно использовать XML для Аналитики в на основе ad-hoc для получения сведений с сервера или выполните команды. 
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Типы данных XML (XML для аналитики)](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Описывает типы данных в спецификации XMLA.|  
|[Элементы XML - команды (XMLA)](../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)|Элементы, которые могут использоваться в элементе команды во время вызова метода Execute.|  
|[Элементы XML - команды (XMLA)](../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)|Элементы, которые могут использоваться в элементе команды во время вызова метода Execute.|  
|[Элементы XML - заголовки (XML для Аналитики)](../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)| Элементы заголовка, реализуемый Microsoft Analysis Services.|  
|[Элементы XML - свойства (XML для Аналитики)](../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)| Элементы, представляющие сведения о свойстве и значения для заголовков, методов, объектов, команды и данные типов XML для Аналитики.|  
|[Элементы XML - методы — обнаружение (XML для Аналитики)](../../analysis-services/xmla/xml-elements-methods-discover.md)| Получает сведения, такие как список доступных баз данных или сведений о конкретном объекте от экземпляра служб Analysis Services.|  
|[Элементы XML - методы — выполнение (XML для Аналитики)](../../analysis-services/xmla/xml-elements-methods-execute.md)| Отправляет XML для аналитики (XMLA) команды к экземпляру служб Analysis Services.|  
|[DiscoverResponse элементов - объектов - XML (XML для Аналитики)](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)| Содержит сведения, возвращаемые экземпляром служб Analysis Services в ответ на вызов метода Discover.|  
|[ExecuteResponse элементов - объектов - XML (XML для Аналитики)](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)| Содержит сведения, возвращаемые экземпляром служб Analysis Services в ответ на вызов метода Execute.|  
|[Элементы XML - объектов (XMLA)](../../analysis-services/xmla/xml-elements-objects.md)| Объекты, реализованные службами Analysis Services.|  
|[Соответствие спецификациям XML для аналитики (XMLA)](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Описывает уровень совместимости со спецификацией XMLA 1.1.|  
  
## <a name="see-also"></a>См. также
 [Наборы строк схемы XML для аналитики](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
 [Разработка с использованием ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 [Разработка объектов управления аналитикой (объекты AMO)](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
