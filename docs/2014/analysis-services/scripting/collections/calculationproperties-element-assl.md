---
title: Элемент CalculationProperties (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CalculationProperties Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalculationProperties
helpviewer_keywords:
- CalculationProperties element
ms.assetid: dccfe036-0b1b-4877-8bdd-4b128ccb55c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e2c4b115c76930bb00a333d36fcec361fe1d297
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113559"
---
# <a name="calculationproperties-element-assl"></a>Элемент CalculationProperties (ASSL)
  Содержит коллекцию элементов [CalculationProperty](../objects/calculationproperty-element-assl.md) элементы, связанные с [MdxScript](../objects/mdxscript-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MdxScript>  
   ...  
   <CalculationProperties>  
      <CalculationProperty>...</CalculationProperty>  
   </CalculationProperties>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MdxScript](../objects/mdxscript-element-assl.md)|  
|Дочерние элементы|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CalculationPropertyCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
