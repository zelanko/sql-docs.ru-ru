---
title: Тип данных MeasureGroupBinding (вне строки) (ASSL) | Документы Microsoft
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
- MeasureGroupBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupBinding
helpviewer_keywords:
- MeasureGroupBinding data type
ms.assetid: e6c65597-89ac-457e-a0e5-01d85449a1b7
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4c467267028e60910be01466754648e216c685d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100575"
---
# <a name="measuregroupbinding-data-type-out-of-line-assl"></a>Тип данных MeasureGroupBinding (внешний) (ASSL)
  Определяет примитивный тип данных, который представляет привязку к группе мер.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroupBinding>  
   <ID>...</ID>  
   <Source>...</Source>  
   <EstimatedRows>...</EstimatedRows>  
   <Dimensions>...</Dimensions>  
   <Measures>...</Measures>  
      <Partitions>...</Partitions>  
</MeasureGroupBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Измерения](../collections/dimensions-element-assl.md), [EstimatedRows](../properties/estimatedrows-element-assl.md), [идентификатор](../properties/id-element-assl.md), [меры](../collections/measures-element-assl.md), [секций](../collections/partitions-element-assl.md), [источника](../properties/source-element-binding-assl.md)|  
|Производные элементы|В разделе [привязки](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения см в разделе внешние привязки, [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  