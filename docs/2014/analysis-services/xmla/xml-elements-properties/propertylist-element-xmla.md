---
title: Элемент PropertyList (XML для Аналитики) | Документы Microsoft
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
- PropertyList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PropertyList
- microsoft.xml.analysis.propertylist
- urn:schemas-microsoft-com:xml-analysis#PropertyList
helpviewer_keywords:
- PropertyList element
ms.assetid: 58e63bd9-8aac-438d-adba-1868b4d123f5
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4b49ad0cf03ce331a00a7eefc9f1302176d89e74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087723"
---
# <a name="propertylist-element-xmla"></a>Элемент PropertyList (XML для аналитики)
  Содержит коллекцию XML для аналитики (XMLA) свойства, используемые [Discover](../xml-elements-methods-discover.md) и [Execute](../xml-elements-methods-execute.md) методы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Properties>  
   <PropertyList>  
      <!-- Zero or more XMLA properties -->  
   </PropertyList>  
</Properties>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Свойства](properties-element-xmla.md)|  
|Дочерние элементы|Свойства XML для аналитики (см. раздел «Примечания»)|  
  
## <a name="remarks"></a>Примечания  
 `PropertyList` Элемент содержит коллекцию свойств XMLA. Каждое свойство позволяет пользователю управлять определенным аспектом методов `Discover` и `Execute`, например определением сведений, необходимых для соединения с источником данных, указанием формата результирующего набора или локали, в которой форматируются данные. Каждое свойство XMLA в `PropertyList` элемент определяется отдельным элементом XML. Значением свойства XMLA являются данные, содержащиеся в этом XML-элементе, а имя свойства XMLA соответствует имени XML-элемента.  
  
 Доступные свойства и их значения могут быть получены с помощью с типом запроса DISCOVER_PROPERTIES `Discover` метод. Для перечисления свойств в элементе `PropertyList` не требуется определенного порядка.  
  
 Дополнительные сведения о свойствах XMLA, поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](propertylist-element-supported-xmla-properties.md).  
  
## <a name="example"></a>Пример  
  
```  
<Properties>  
   <PropertyList>  
      <DataSourceInfo>  
         Provider=MSOLAP;Data Source=local;  
      </DataSourceInfo>  
      <Catalog>  
         Foodmart 2000  
      </Catalog>  
      <Format>  
         Multidimensional  
      </Format>  
   </PropertyList>  
</Properties>  
```  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  