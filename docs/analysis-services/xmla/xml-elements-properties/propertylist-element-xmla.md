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
ms.openlocfilehash: 3e773de16e65aa9c7f1be521214088aa9f06b369
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34577836"
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Свойства](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
|Дочерние элементы|Свойства XML для аналитики (см. раздел «Примечания»)|  
  
## <a name="remarks"></a>Примечания  
 Элемент **PropertyList** содержит коллекцию свойств XMLA. Каждое свойство позволяет пользователю управлять определенным аспектом методов **Discover** и **Execute** , например определением сведений, необходимых для соединения с источником данных, указанием формата результирующего набора или локали, в которой форматируются данные. Каждое свойство XMLA в элементе **PropertyList** определено с помощью отдельного XML-элемента. Значением свойства XMLA являются данные, содержащиеся в этом XML-элементе, а имя свойства XMLA соответствует имени XML-элемента.  
  
 Доступные свойства и их значения можно получить, используя метод **Discover** с типом запроса DISCOVER_PROPERTIES. Для перечисления свойств в элементе **PropertyList** не требуется определенного порядка.  
  
 Дополнительные сведения о свойствах XMLA, поддерживаемые службами Analysis Services см. в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
