---
title: Измерения элемента (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f884fcaa96a1406ad1bf1de948c6689a8ab909c3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="dimension-element-xmla"></a>Элемент Dimension (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет измерение куба, представленного родительским [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Object>  
   ...  
   <Dimension>...</Dimension>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Измерения** элемент — это идентификатор объекта, содержащее имя измерения куба, представленного **объекта** элемент.  
  
## <a name="see-also"></a>См. также  
 [Элемент Database & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)   
 [Элемент Dimension (XML для Аналитики)](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
