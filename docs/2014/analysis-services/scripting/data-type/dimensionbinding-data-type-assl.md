---
title: Тип данных DimensionBinding (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DimensionBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionBinding
helpviewer_keywords:
- DimensionBinding data type
ms.assetid: 6163d86b-0f6c-4237-b07b-47bc7e2962c4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b43ff1d359a53bfbe59c1938c4da3ebb065ea6c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125939"
---
# <a name="dimensionbinding-data-type-assl"></a>Тип данных DimensionBinding (ASSL)
  Определяет производный тип данных, представляющий привязку между источником данных и [измерения](../objects/dimension-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionBinding>  
   <!-- The following elements extend Binding -->  
      <DataSourceID>...</DataSourceID>  
   <DimensionID>...</DimensionID>  
      <Persistence>...</Persistence>  
      <RefreshPolicy>...</RefreshPolicy>  
   <RefreshInterval>...</RefreshInterval>  
</DimensionBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[DataSourceID](../properties/id-element-assl.md), [DimensionID](../properties/dimensionid-element-assl.md), [сохраняемости](../properties/persistence-element-assl.md), [RefreshInterval](../properties/refreshinterval-element-assl.md), [RefreshPolicy](../properties/refreshpolicy-element-assl.md)|  
|Производные элементы|См. в разделе [привязки](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) типа `Binding` тип и иерархию наследования `Binding` типов, см. в разделе [типа привязки данных &#40;ASSL&#41; ](binding-data-type-assl.md) элемент.  
  
 Обзор привязки данных в языке ASSL, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.DimensionBinding>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
