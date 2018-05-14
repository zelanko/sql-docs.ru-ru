---
title: Элемент AggregationStorage (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c73a26c4cf05b8ba003eb92c9aba31cde63ef1f0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
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
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из следующих строк.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Regular*|Данные агрегата хранятся обычным способом.|  
|*MolapOnly*|Данные агрегата хранятся только в многомерном хранилище OLAP (MOLAP).|  
  
 *MolapOnly* параметр доступен только для [секции](../../../analysis-services/scripting/objects/partition-element-assl.md) элемента.  
  
 Перечисление, соответствующее разрешенным значениям для **AggregationStorage** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ProactiveCachingAggregationStorage>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
