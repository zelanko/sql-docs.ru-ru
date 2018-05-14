---
title: Элемент MoveWithDescendants (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 34ea88c2aee76684c3876195bda9b1f2633bab3a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="movewithdescendants-element-xmla"></a>Элемент MoveWithDescendants (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает, является ли потомки элементов атрибутов обновляются в родительском [обновление](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Update>  
   ...  
   <MoveWithDescendants>...</MoveWithDescendants>  
   ...  
</Update>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|False|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **MoveWithDescendants** определяет ли **обновление** команды должен обновлять не только элементы атрибутов, определенных в [атрибуты](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md) элемент, но Кроме того, должны также обновить потомки этих элементов атрибутов.  
  
> [!NOTE]  
>  Этот элемент применяется только к элементам атрибутов в иерархиях родителей-потомков.  
  
 Дополнительные сведения об обновлении элементов см. в разделе [Вставка, обновление и удаление членов &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
