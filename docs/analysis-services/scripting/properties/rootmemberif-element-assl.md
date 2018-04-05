---
title: Элемент RootMemberIf (ASSL) | Документы Microsoft
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
- RootMemberIf Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- RootMemberIf
helpviewer_keywords:
- RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c5a3a75efa13710bcc00a94ed55cee407dbbbc8d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="rootmemberif-element-assl"></a>Элемент RootMemberIf (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет, как идентифицируются корневой элемент или элементы родительского атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*ParentIsBlankSelfOrMissing*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Значение **RootMemberIf** элемент используется только родительскими атрибутами (другими словами, значение [использование](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) элемент **DimensionAttribute** родительским элементом является значение *родительского*) для определения корневых (самых верхних) элементов иерархии типа «родители потомки».  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Корневыми считаются только те элементы, которые удовлетворяют одному или нескольким условиям, описанным для *ParentIsBlank*, *ParentIsSelf*или *ParentIsMissing* .|  
|*ParentIsBlank*|Только элементы, имеющие значение null, нуль или пустая строка в ключевых столбцах, представленных [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) коллекцию **DimensionAttribute** , считаются корневыми.|  
|*ParentIsSelf*|Корневыми считаются только элементы, которые сами для себя являются родительскими.|  
|*ParentIsMissing*|Корневыми считаются элементы, для которых невозможно найти родительские элементы.|  
  
 Перечисление, соответствующее разрешенным значениям для **RootMemberIf** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
