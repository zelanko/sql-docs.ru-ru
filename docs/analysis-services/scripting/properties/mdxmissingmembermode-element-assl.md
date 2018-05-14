---
title: Элемент MdxMissingMemberMode (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7c521b2ca9c4f8b455d472f43612c23e27076780
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="mdxmissingmembermode-element-assl"></a>Элемент MdxMissingMemberMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Значение по умолчанию|*Default*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Измерения](../../../analysis-services/scripting/data-type/dimension-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Игнорировать*|Отсутствующие элементы пропускаются.|  
|*Ошибка*|При обнаружении отсутствующих элементов возникает ошибка.|  
|*Default*|Отсутствующие элементы пропускаются.|  
  
 Элемент, соответствующий родителю параметра **MdxMissingMemberMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>См. также  
 [Многомерные выражения & #40; Многомерные Выражения & #41; Ссылка](../../../mdx/multidimensional-expressions-mdx-reference.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
