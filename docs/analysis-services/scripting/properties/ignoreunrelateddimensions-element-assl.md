---
title: Элемент IgnoreUnrelatedDimensions (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 42dbcb7a41eec2d620b0a0c098503ff2aa8d2fec
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="ignoreunrelateddimensions-element-assl"></a>Элемент IgnoreUnrelatedDimensions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, будут ли несвязанные измерения принудительно перемещаться на верхний уровень, если элементы измерений, не связанных с группой мер, включаются в запрос.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|True|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если элемент **IgnoreUnrelatedDimensions** имеет значение **true**, несвязанные измерения принудительно переводятся на верхний уровень; если его значение равно **false**, измерения на верхний уровень принудительно не переводятся. Это свойство похоже на функцию многомерных выражений (MDX) [ValidMeasure](../../../mdx/validmeasure-mdx.md) функции.  
  
 Элемент, соответствующий родителю параметра **IgnoreUnrelatedDimensions** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
