---
title: Элемент RootMemberIf (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0a738d6d859a74430d50439ebcee3d4aab8d031c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="rootmemberif-element-assl"></a>Элемент RootMemberIf (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, как идентифицируются корневой элемент или элементы родительского атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*ParentIsBlankSelfOrMissing*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение **RootMemberIf** элемент используется только родительскими атрибутами (другими словами, значение [использование](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) элемент **DimensionAttribute** родительским элементом является значение *родительского*) для определения корневых (самых верхних) элементов иерархии типа «родители потомки».  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Корневыми считаются только те элементы, которые удовлетворяют одному или нескольким условиям, описанным для *ParentIsBlank*, *ParentIsSelf*или *ParentIsMissing* .|  
|*ParentIsBlank*|Только элементы, имеющие значение null, нуль или пустая строка в ключевых столбцах, представленных [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) коллекцию **DimensionAttribute** , считаются корневыми.|  
|*ParentIsSelf*|Корневыми считаются только элементы, которые сами для себя являются родительскими.|  
|*ParentIsMissing*|Корневыми считаются элементы, для которых невозможно найти родительские элементы.|  
  
 Перечисление, соответствующее разрешенным значениям для **RootMemberIf** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
