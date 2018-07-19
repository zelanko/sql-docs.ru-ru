---
title: Элемент UnknownMemberName (ASSL) | Документация Майкрософт
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d744357078e4cfaa73fe3170dba8f1321313efad
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050582"
---
# <a name="unknownmembername-element-assl"></a>Элемент UnknownMemberName (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит заголовок (на языке по умолчанию для измерения) для неизвестного элемента измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMemberName>...</UnknownMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|*Unknown*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение элемента **UnknownMemberName** задает заголовок, используемый для неизвестного элемента. Идентификатором неизвестного элемента является *Dimension*.UnknownMember, где *Dimension* представляет собой уникальное имя измерения, которое не может быть изменено.  
  
 Элемент, соответствующий родителю параметра **UnknownMemberName** в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
