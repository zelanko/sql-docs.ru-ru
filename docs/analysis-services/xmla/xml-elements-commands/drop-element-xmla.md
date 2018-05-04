---
title: Удалить элемент (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Drop Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Drop
- microsoft.xml.analysis.drop
- http://schemas.microsoft.com/analysisservices/2003/engine#Drop
helpviewer_keywords:
- Drop element
ms.assetid: a5d21db3-743a-4958-b16d-b6816a5ee787
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bd81c88f04fccbfabe50692762802f7bb040629a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="drop-element-xmla"></a>Элемент Drop (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Удаляет элементы атрибута из измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Drop>  
      <Object>...</Object>  
      <DeleteWithDescendants>...</DeleteWithDescendants>  
      <Where>...</Where>  
   </Drop>  
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
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[DeleteWithDescendants](../../../analysis-services/xmla/xml-elements-properties/deletewithdescendants-element-xmla.md), [объекта](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md), [где](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Команда **Drop** удаляет элементы атрибутов из измерения, доступного для записи.  
  
 Дополнительные сведения об удалении элементов см. в разделе [Вставка, обновление и удаление членов &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Вставить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Обновить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Команды & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
