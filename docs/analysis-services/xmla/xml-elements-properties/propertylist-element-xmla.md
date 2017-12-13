---
title: "Элемент PropertyList (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PropertyList Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PropertyList
- microsoft.xml.analysis.propertylist
- urn:schemas-microsoft-com:xml-analysis#PropertyList
helpviewer_keywords: PropertyList element
ms.assetid: 58e63bd9-8aac-438d-adba-1868b4d123f5
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 795c91c398337bba1444735e54bbbfeb33d07933
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="propertylist-element-xmla"></a>Элемент PropertyList (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Содержит коллекцию XML для аналитики (XMLA) свойства, используемые [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) и [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) методы.  
  
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
  
## <a name="remarks"></a>Замечания  
 Элемент **PropertyList** содержит коллекцию свойств XMLA. Каждое свойство позволяет пользователю управлять определенным аспектом методов **Discover** и **Execute** , например определением сведений, необходимых для соединения с источником данных, указанием формата результирующего набора или локали, в которой форматируются данные. Каждое свойство XMLA в элементе **PropertyList** определено с помощью отдельного XML-элемента. Значением свойства XMLA являются данные, содержащиеся в этом XML-элементе, а имя свойства XMLA соответствует имени XML-элемента.  
  
 Доступные свойства и их значения можно получить, используя метод **Discover** с типом запроса DISCOVER_PROPERTIES. Для перечисления свойств в элементе **PropertyList** не требуется определенного порядка.  
  
 Дополнительные сведения о свойствах XMLA, поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
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
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
