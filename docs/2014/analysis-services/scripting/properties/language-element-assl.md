---
title: Элемент Language (ASSL) | Документы Microsoft
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
- Language Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LANGUAGE
helpviewer_keywords:
- Language element
ms.assetid: 4d745d23-6b1f-4a85-97cf-d034cc41356f
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 09a51320df0cf5d4246fbc14307f488c2d754e3c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193680"
---
# <a name="language-element-assl"></a>Элемент Language (ASSL)
  Содержит идентификатор языка родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube> <!-- or Database, Dimension, MiningModel, MiningStructure, Translation -->  
   ...  
   <Language>...</Language>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
  
 **Количество элементов**  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[Перевод](../objects/translation-element-assl.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|Все остальные|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../objects/cube-element-assl.md), [базы данных](../objects/database-element-assl.md), [измерения](../objects/dimension-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [перевода](../objects/translation-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Language` содержит идентификатор языка по умолчанию, используемый родительским элементом, или идентификатор с конкретным языком для элемента `Translation`. Язык должен быть определен с помощью кодов идентификатора локали (LCID). Например, LCID 1033 используется для обозначения американского английского языка.  
  
 Элементами, которые соответствуют родителям элемента `Language` в модели объектов AMO, являются <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure> и <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  