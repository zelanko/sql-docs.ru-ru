---
title: Обновить элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Update Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Update
- microsoft.xml.analysis.update
- http://schemas.microsoft.com/analysisservices/2003/engine#Update
helpviewer_keywords:
- Update command [XMLA]
ms.assetid: 324dcc16-865d-4d0a-b393-2b06c18ac807
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75dda4a163ce6551246e11aa9eba6b57fcd9fb25
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283962"
---
# <a name="update-element-xmla"></a>Элемент Update (XML для аналитики)
  Обновляет элементы атрибута в измерении.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Update>  
      <Object>...</Object>  
      <MoveWithDescendants>...</MoveWithDescendants>  
      <Attributes>...</Attributes>  
      <Where>...</Where>  
   </Update>  
</Command>  
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
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Атрибуты](../xml-elements-properties/attributes-element-xmla.md), [MoveWithDescendants](../xml-elements-properties/movewithdescendants-element-xmla.md), [объект](../xml-elements-properties/object-element-dimension-xmla.md), [где](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда `Update` перемещает элементы атрибута в пределах измерения, доступного для записи.  
  
 Дополнительные сведения об обновлении элементов см. в разделе [Вставка, обновление и удаление членов &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент DROP &#40;XML для Аналитики&#41;](drop-element-xmla.md)   
 [Вставка элемента &#40;XML для Аналитики&#41;](insert-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
