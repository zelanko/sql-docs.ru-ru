---
title: Элемент IgnoreUnrelatedDimensions (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IgnoreUnrelatedDimensions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- IgnoreUnrelatedDimensions
helpviewer_keywords:
- IgnoreUnrelatedDimensions element
ms.assetid: c7d7a1cd-a8e0-4ae7-9464-a1d2a55a86ab
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 717d36bd445d777981c24e466c4bdcea674e00b1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="ignoreunrelateddimensions-element-assl"></a>Элемент IgnoreUnrelatedDimensions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет, является ли несвязанные измерения принудительно переводятся на верхний уровень, если элементы измерений, не связанных с группой мер, включаются в запрос.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|True|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Если элемент **IgnoreUnrelatedDimensions** имеет значение **true**, несвязанные измерения принудительно переводятся на верхний уровень; если его значение равно **false**, измерения на верхний уровень принудительно не переводятся. Это свойство похоже на функцию многомерных выражений (MDX) [ValidMeasure](../../../mdx/validmeasure-mdx.md) функции.  
  
 Элемент, соответствующий родителю параметра **IgnoreUnrelatedDimensions** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
