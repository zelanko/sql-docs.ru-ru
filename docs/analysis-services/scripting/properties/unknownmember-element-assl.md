---
title: Элемент UnknownMember (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d0cc0d68cdfcc859a4d79d67c3cf61093ecfac60
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="unknownmember-element-assl"></a>Элемент UnknownMember (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Показывает, видим ли неизвестный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMember>...</UnknownMember>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Отображается*|Неизвестный элемент существует и отображается.|  
|*Скрыта*|Неизвестный элемент существует, но не отображается.|  
|*None*|Неизвестный элемент не используется.|  
  
 Перечисление, соответствующее разрешенным значениям для **UnknownMember** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.UnknownMemberBehavior>.  
  
## <a name="see-also"></a>См. также  
 [Элемент UnknownMemberName &#40;ASSL&#41;](../../../analysis-services/scripting/properties/unknownmembername-element-assl.md)   
 [Элемент UnknownMemberTranslation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
