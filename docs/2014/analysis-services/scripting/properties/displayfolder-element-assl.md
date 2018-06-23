---
title: Элемент DisplayFolder (ASSL) | Документы Microsoft
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
- DisplayFolder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DisplayFolder
helpviewer_keywords:
- DisplayFolder element
ms.assetid: 55184c02-03e7-4d6c-b87a-d4d34bc11d0e
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c959f1c2fe298217b46849c6a13d3e0f313f6803
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100092"
---
# <a name="displayfolder-element-assl"></a>Элемент DisplayFolder (ASSL)
  Указывает папку, в которой должен отображаться родительский элемент. В приложениях служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для разработчиков и администраторов могут поддерживать использование папок отображения для визуальной классификации нескольких элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CalculationProperty> <!-- or Hierarchy, Kpi, Measure, Translation -->  
   ...  
   <DisplayFolder>...</DisplayFolder>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[CalculationProperty](../objects/calculationproperty-element-assl.md), [иерархии](../objects/hierarchy-element-assl.md), [ключевого показателя эффективности](../objects/kpi-element-assl.md), [мер](../objects/measure-element-assl.md), [перевода](../objects/translation-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 В более крупных кубах могут существовать сотни мер и иерархий. Свойство `DisplayFolder` определяет внешний вид для пользователя на клиенте. Возможен любой из следующих вариантов значения свойства `DisplayFolder`.  
  
-   Пустое значение означает, что мера не принадлежит папке.  
  
-   Одно имя папки означает, что мера должна обрабатываться как принадлежащая папке с таким же именем.  
  
-   Несколько имен папок, разделенных обратной косой черты (\\), обозначающий иерархию вложенных папок.  
  
 `DisplayFolder` Свойство применяется к `CalculationProperty` элементы только тогда, когда значение [CalculationType](calculationtype-element-assl.md) равно *член*.  
  
 Элементы, соответствующие родителям элемента `DisplayFolder` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.CalculationProperty>, <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.Measure> и <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>См. также  
 [Элемент CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Элемент MdxScript &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  