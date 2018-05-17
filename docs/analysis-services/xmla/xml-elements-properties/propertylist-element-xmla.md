---
title: Элемент PropertyList (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8d7e92f667ebe37cbdfaf75393bdf2816ef818fd
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="propertylist-element-xmla"></a>Элемент PropertyList (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию XML для аналитики (XMLA) свойства, используемые [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) и [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) методы.  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Свойства](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
|Дочерние элементы|Свойства XML для аналитики (см. раздел «Примечания»)|  
  
## <a name="remarks"></a>Примечания  
 Элемент **PropertyList** содержит коллекцию свойств XMLA. Каждое свойство позволяет пользователю управлять определенным аспектом методов **Discover** и **Execute** , например определением сведений, необходимых для соединения с источником данных, указанием формата результирующего набора или локали, в которой форматируются данные. Каждое свойство XMLA в элементе **PropertyList** определено с помощью отдельного XML-элемента. Значением свойства XMLA являются данные, содержащиеся в этом XML-элементе, а имя свойства XMLA соответствует имени XML-элемента.  
  
 Доступные свойства и их значения можно получить, используя метод **Discover** с типом запроса DISCOVER_PROPERTIES. Для перечисления свойств в элементе **PropertyList** не требуется определенного порядка.  
  
 Дополнительные сведения о свойствах XMLA, поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
