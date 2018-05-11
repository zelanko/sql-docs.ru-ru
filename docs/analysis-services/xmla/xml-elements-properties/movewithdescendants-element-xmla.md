---
title: Элемент MoveWithDescendants (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a61c8f56ae41d7fd1f58f394ea9adaca4a82ceb
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
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
  
  
