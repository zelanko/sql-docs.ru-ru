---
title: Элемент RootMemberIf (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RootMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RootMemberIf
helpviewer_keywords:
- RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fb10d62b14c5f13fbc26de23d832d77b724bebc6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118704"
---
# <a name="rootmemberif-element-assl"></a>Элемент RootMemberIf (ASSL)
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
|Родительский элемент|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение `RootMemberIf` элемент используется только родительскими атрибутами (другими словами, значение [использования](usage-element-dimensionattribute-assl.md) элемент `DimensionAttribute` родительского элемента имеет значение *родительского*) для определения root ( самых верхних) элементов иерархии «родители потомки».  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Корневыми считаются только те элементы, которые удовлетворяют одному или нескольким условиям, описанным для *ParentIsBlank*, *ParentIsSelf*или *ParentIsMissing* .|  
|*ParentIsBlank*|Только элементы, имеющие значение null, нуль или пустую строку в ключевых столбцах, представленных свойством [KeyColumns](../collections/columns-element-assl.md) коллекцию `DimensionAttribute` , считаются корневыми.|  
|*ParentIsSelf*|Корневыми считаются только элементы, которые сами для себя являются родительскими.|  
|*ParentIsMissing*|Корневыми считаются элементы, для которых невозможно найти родительские элементы.|  
  
 Перечисление, соответствующее допустимым значениям элемента `RootMemberIf` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
