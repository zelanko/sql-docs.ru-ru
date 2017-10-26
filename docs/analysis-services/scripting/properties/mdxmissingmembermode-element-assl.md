---
title: "Элемент MdxMissingMemberMode (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
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
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b938068f6e9f55f5d9d94ea5c65a01b5281152f2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdxmissingmembermode-element-assl"></a>Элемент MdxMissingMemberMode (ASSL)
  Определяет, как обрабатываются пропущенные элементы для инструкций многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
   ...  
   <MdxMissingMemberMode>...</MdxMissingMemberMode>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*По умолчанию*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Dimension](../../../analysis-services/scripting/data-type/dimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
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
  
  

