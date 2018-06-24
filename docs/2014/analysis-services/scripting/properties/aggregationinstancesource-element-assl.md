---
title: Элемент AggregationInstanceSource (ASSL) | Документы Microsoft
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
- AggregationInstanceSource Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstanceSource element
ms.assetid: ab58c817-eb2b-4974-8470-2946ca5affea
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 318f70f156d78df90ceeb53e56cbc83f9d4e43a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195244"
---
# <a name="aggregationinstancesource-element-assl"></a>Элемент AggregationInstanceSource (ASSL)
  Определяет источник данных для экземпляров определяемых пользователем агрегатов, привязанных к [секции](../objects/partition-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Partition>  
   ...  
   <AggregationInstanceSource xsi:type="DataSourceViewBinding">...</AggregationInstanceSource>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataSourceViewBinding](../data-type/binding-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Секция](../objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если элемент отсутствует или равен пустой строке, то по умолчанию используется представление источника данных для куба, которому принадлежит секция.  
  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) `Binding` тип и иерархию наследования `Binding` типов, в разделе [тип привязки данных &#40;ASSL&#41;](../data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  