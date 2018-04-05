---
title: Элемент MdxMissingMemberMode (ASSL) | Документы Microsoft
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
- MdxMissingMemberMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MdxMissingMemberMode element
ms.assetid: aca6130b-5fb8-4fa1-af8b-8e1ef361926f
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 02ede17b0011ed3eceecf35feaa93fc42c55da3c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdxmissingmembermode-element-assl"></a>Элемент MdxMissingMemberMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет, как отсутствующие элементы обрабатываются для инструкций многомерных выражений (MDX).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
   ...  
   <MdxMissingMemberMode>...</MdxMissingMemberMode>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*По умолчанию*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Dimension](../../../analysis-services/scripting/data-type/dimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Игнорировать*|Отсутствующие элементы пропускаются.|  
|*Ошибка*|При обнаружении отсутствующих элементов возникает ошибка.|  
|*По умолчанию*|Отсутствующие элементы пропускаются.|  
  
 Элемент, соответствующий родителю параметра **MdxMissingMemberMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>См. также:  
 [Многомерные выражения &#40; Многомерные Выражения &#41; Ссылка](../../../mdx/multidimensional-expressions-mdx-reference.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
