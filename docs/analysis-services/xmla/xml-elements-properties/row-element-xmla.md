---
title: "Строка Element (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
apiname: row Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#row
- microsoft.xml.analysis.row
- http://schemas.microsoft.com/analysisservices/2003/engine#row
helpviewer_keywords: row element
ms.assetid: 4d9977a0-c396-44c7-9fd4-97f4c3d643aa
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 31ce205d17095d2a6df40adb7ce0be64f883b5f4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="row-element-xmla"></a>Элемент row (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Содержит одну строку данных для [корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) элемент, который содержит табличные данные, возвращенные [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <row>  
      <!-- One or more column elements -->  
   </row>  
</root>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) (с помощью [строк](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) тип данных)|  
|Дочерние элементы|Один или несколько элементов столбца.|  
  
## <a name="remarks"></a>Замечания  
 Каждая строка, возвращенная элементом **root** , который содержит табличные данные, имеет соответствующий элемент **row** . Каждый столбец в элементе **root** представлен отдельным элементом XML. Значение столбца для элемента **row** представляет собой данные, содержащиеся в элементе XML, а имя столбца соответствует имени элемента XML.  
  
 Есть два следующих способа указать значение NULL для столбца внутри строки.  
  
-   При отсутствии элемента столбца подразумевается, что значением столбца является NULL.  
  
-   В элементе столбца может использоваться атрибут `xsi:nil='true'` , указывающий, что столбец имеет значение NULL.  
  
 Например, если строка содержит единственный столбец Store_Name и его значение равно NULL, он может быть представлен в одной из следующих форм.  
  
```  
<row>  
</row>  
```  
  
 или:  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
 Если элемент столбца содержит ошибку, элемент **Error** предоставляет информацию об ошибке, как описано в следующем примере.  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 Дополнительные сведения об именовании столбцов и сведения о схеме для табличных данных см. в разделе [Rowset, тип данных &#40; XML для Аналитики &#41; ](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
