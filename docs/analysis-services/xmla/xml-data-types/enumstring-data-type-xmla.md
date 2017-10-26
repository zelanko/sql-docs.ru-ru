---
title: "Тип данных EnumString (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- EnumString Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- EnumString
- urn:schemas-microsoft-com:xml-analysis#EnumString
- http://schemas.microsoft.com/analysisservices/2003/engine#EnumString
helpviewer_keywords:
- EnumString data type
ms.assetid: 9214195e-4539-419b-95ec-b7aa75e033ab
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3209c6fd1546a4b1596eaaf6f4a19049bfc1fa92
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="enumstring-data-type-xmla"></a>Тип данных EnumString (XML для аналитики)
  Определяет производный тип данных, представляющий набор именованных констант для данного перечислителя.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|**строка**|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|Нет|  
  
## <a name="remarks"></a>Замечания  
 В XML для аналитики используются перечисления, позволяющие ограничить строковые значения набором параметров, которые можно проверить. **EnumString** использует стандартный тип данных XML **string** . Конкретные значения для каждой именованной константы указываются в определении перечислителя. Перечислители определяются путем добавления их в [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md) набора строк схемы и может быть получен с помощью [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с DISCOVER_ENUMERATORS тип запроса.  
  
 В следующей таблице описаны перечислители, поддерживаемые экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Перечислитель|Описание|  
|----------------|-----------------|  
|ProviderType|Поддерживает столбец ProviderType в [DISCOVER_DATASOURCES](../../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md) набора строк схемы, который определяет тип данных, который может быть возвращен [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.<br /><br /> Данное перечисление также поддерживает свойство XMLA **ProviderType**, который определяет типы поставщиков, поддерживаемые [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Данное перечисление также используется в наборе строк схемы DISCOVER_DATASOURCES.<br /><br /> Дополнительные сведения о **ProviderType**, в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|AuthenticationMode|Поддерживает столбец AuthenticationMode в наборе строк схемы DISCOVER_DATASOURCES, в котором определяются учетные данные безопасности, необходимые для получения доступа к экземпляру служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|PropertyAccessType|Поддерживает столбец PropertyAccessType в [DISCOVER_PROPERTIES](../../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md) набора строк схемы, который определяет тип доступа к свойству XMLA.|  
|StateSupport|Поддерживает свойство XMLA **Несущеемножествосостояния**, которое определяет уровень контроля изменений состояния, поддерживаемый [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.<br /><br /> Дополнительные сведения о **Несущеемножествосостояния**, в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|StateActionVerb|Содержит список команд, поддерживаемых XMLA для заголовков SOAP, которые используются, чтобы начать, идентифицировать или закончить сеанс.<br /><br /> Дополнительные сведения о сеансах см. в разделе [Управление соединениями и сеансами &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Поддерживает свойство XMLA **формат**, которое определяет тип данных, возвращаемых в [корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) элемента.<br /><br /> Дополнительные сведения о **формат**, в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Поддерживает свойство XMLA **AxisFormat**, которое определяет формат сведений об оси, возвращаемых элементом **root** , содержащим многомерные данные.<br /><br /> Дополнительные сведения о **AxisFormat**, в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Поддерживает свойство XMLA **Content**, определяющее, возвращает ли элемент **root** метаданные или обычные данные.<br /><br /> Дополнительные сведения о **содержимого**, в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Поддерживает свойство XMLA **MDXSupport**, которое определяет уровень поддержки многомерных выражений (MDX), доступные на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.<br /><br /> Дополнительные сведения о **MDXSupport**, в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных XML &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  

