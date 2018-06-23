---
title: Тип данных EnumString (XML для Аналитики) | Документы Microsoft
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
api_name:
- EnumString Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
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
manager: mblythe
ms.openlocfilehash: 034ebe0218a8effece3aee526f9920850a7df536
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189597"
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
|Базовые типы данных|`string`|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 В XML для аналитики используются перечисления, позволяющие ограничить строковые значения набором параметров, которые можно проверить. `EnumString` использует стандартный тип данных XML `string`. Конкретные значения для каждой именованной константы указываются в определении перечислителя. Перечислители определяются путем добавления их в [DISCOVER_ENUMERATORS](../../schema-rowsets/xml/discover-enumerators-rowset.md) набора строк схемы и может быть получен с помощью [Discover](../xml-elements-methods-discover.md) метод с DISCOVER_ENUMERATORS тип запроса.  
  
 В следующей таблице описаны перечислители, поддерживаемые экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Перечислитель|Описание|  
|----------------|-----------------|  
|ProviderType|Поддерживает столбец ProviderType в [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md) набора строк схемы, который определяет тип данных, который может быть возвращен [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.<br /><br /> Данное перечисление также поддерживает свойство XMLA `ProviderType`, которое определяет типы поставщиков, поддерживаемые экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Данное перечисление также используется в наборе строк схемы DISCOVER_DATASOURCES.<br /><br /> Дополнительные сведения о `ProviderType`, в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|AuthenticationMode|Поддерживает столбец AuthenticationMode в наборе строк схемы DISCOVER_DATASOURCES, в котором определяются учетные данные безопасности, необходимые для получения доступа к экземпляру служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|PropertyAccessType|Поддерживает столбец PropertyAccessType в [DISCOVER_PROPERTIES](../../schema-rowsets/xml/discover-properties-rowset.md) набора строк схемы, который определяет тип доступа к свойству XMLA.|  
|StateSupport|Поддерживает свойство XMLA `StateSupport`, которое определяет уровень контроля изменений состояния, поддерживаемый экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Дополнительные сведения о `StateSupport`, в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|StateActionVerb|Содержит список команд, поддерживаемых XMLA для заголовков SOAP, которые используются, чтобы начать, идентифицировать или закончить сеанс.<br /><br /> Дополнительные сведения о сеансах см. в разделе [Управление соединениями и сеансами &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Поддерживает свойство XMLA `Format`, которое определяет тип данных, возвращаемых в [корневой](../xml-elements-properties/root-element-xmla.md) элемента.<br /><br /> Дополнительные сведения о `Format`, в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Поддерживает свойство XMLA `AxisFormat`, которое определяет формат сведений об оси, возвращаемых элементом `root`, содержащим многомерные данные.<br /><br /> Дополнительные сведения о `AxisFormat`, в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Поддерживает свойство XMLA `Content`, определяющее, возвращает ли элемент `root` метаданные или обычные данные.<br /><br /> Дополнительные сведения о `Content`, в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Поддерживает свойство XMLA `MDXSupport`, которое определяет уровень поддержки многомерных выражений, доступной в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Дополнительные сведения о `MDXSupport`, в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](xml-data-types-xmla.md)  
  
  