---
title: "Элемент Properties (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: Properties Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Properties
- microsoft.xml.analysis.properties
- urn:schemas-microsoft-com:xml-analysis#Properties
- Properties
helpviewer_keywords: Properties element
ms.assetid: 0b5468e5-bf23-4d22-862f-72e27a9fff2f
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a1b6d317bee380fab7439ecc67b82fce452536ae
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="properties-element-xmla"></a>Элемент Properties (XML для аналитики)
  Содержит XML для аналитики (XMLA) свойства, используемые [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) и [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) методы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Discover> <!-- or Execute -->  
...  
   <Properties>  
      <PropertyList>...</PropertyList>  
   </Properties>  
...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Обнаружение](../../../analysis-services/xmla/xml-elements-methods-discover.md), [выполнение](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Дочерние элементы|[PropertyList](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 **Свойства** элемент представляет свойства XMLA, используемые для управления разными аспектами **Discover** и **Execute** методов, например определением сведений, необходимых для подключиться к источнику данных, указанием формата результирующего набора или локали, в которой форматируются данные.  
  
 Доступные свойства и их значения можно получить, используя метод **Discover** с типом запроса DISCOVER_PROPERTIES.  
  
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
  
  
