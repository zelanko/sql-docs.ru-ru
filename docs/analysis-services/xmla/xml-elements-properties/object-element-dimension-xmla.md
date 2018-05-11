---
title: Объект элемента (измерение) (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6183485943974072f4532f519021664a2ae7001d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="object-element-dimension-xmla"></a>Элемент Object (Dimension) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит ссылку на объект для измерения, на котором родительского [вставить](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [обновление](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), или [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) выполняется команда.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Insert> <!-- or any of the parent elements in the Element Relationships table -->  
...  
   <Object>  
      <Database>...</Database>  
      <Cube>...</Cube>  
      <Dimension>...</Dimension>  
   </Object>  
...  
</Insert>  
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
|Родительские элементы|[Удалить](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [вставить](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [обновления](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Дочерние элементы|[Куб](../../../analysis-services/xmla/xml-elements-properties/cube-element-xmla.md), [базы данных](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md), [измерения](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
