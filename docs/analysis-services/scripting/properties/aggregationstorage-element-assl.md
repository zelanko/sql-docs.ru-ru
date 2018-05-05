---
title: Элемент AggregationStorage (ASSL) | Документы Microsoft
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
- AggregationStorage Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationStorage
helpviewer_keywords:
- AggregationStorage element
ms.assetid: dd082388-534d-4847-9232-8f80fc9fe96e
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b629e033c5ce4985a2af5a8f244b8c34e8c9e780
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="aggregationstorage-element-assl"></a>Элемент AggregationStorage (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет метод хранения для агрегатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <AggregationStorage>...</AggregationStorage>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Regular*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Regular*|Данные агрегата хранятся обычным способом.|  
|*MolapOnly*|Данные агрегата хранятся только в многомерном хранилище OLAP (MOLAP).|  
  
 *MolapOnly* параметр доступен только для [секции](../../../analysis-services/scripting/objects/partition-element-assl.md) элемента.  
  
 Перечисление, соответствующее разрешенным значениям для **AggregationStorage** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ProactiveCachingAggregationStorage>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
