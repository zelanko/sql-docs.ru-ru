---
title: Строка Element (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84cf252303832ed157981103ffaede9718949e16
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576216"
---
# <a name="row-element-xmla"></a>Элемент row (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит одну строку данных для [корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) элемент, который содержит табличные данные, возвращенные [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
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
  
## <a name="remarks"></a>Примечания  
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
  
 Дополнительные сведения об именовании столбцов и сведения о схеме для табличных данных см. в разделе [Rowset, тип данных &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
