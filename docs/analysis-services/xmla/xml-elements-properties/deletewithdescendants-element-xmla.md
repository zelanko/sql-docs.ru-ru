---
title: Элемент DeleteWithDescendants (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a646a910443055b3fbfb892743493d86e2ba370e
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574806"
---
# <a name="deletewithdescendants-element-xmla"></a>Элемент DeleteWithDescendants (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает, удаляются ли потомки элементов атрибутов командой [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) , примененной к родительскому элементу.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Drop>  
   ...  
   <DeleteWithDescendants>...</DeleteWithDescendants>  
   ...  
</Drop>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|False|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DROP](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент **DeleteWithDescendants** определяет, должна ли команда **Drop** удалять не только элементы атрибутов, определенных в элементе [Where](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md) , но и потомки этих элементов атрибутов.  
  
> [!NOTE]  
>  Этот элемент применяется только к элементам атрибутов в иерархиях родителей-потомков.  
  
 Дополнительные сведения об удалении и обновлении элементов атрибутов см. в разделе [Вставка, обновление и удаление элементов (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
