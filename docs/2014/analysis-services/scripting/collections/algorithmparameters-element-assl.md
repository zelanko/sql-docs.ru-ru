---
title: Элемент AlgorithmParameters (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AlgorithmParameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AlgorithmParameters
helpviewer_keywords:
- AlgorithmParameters element
ms.assetid: 240cbb60-7fa3-46ef-b5be-cd14c9ec10de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c15cfd9be773af74c195860f7b0b16989b8c4355
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048894"
---
# <a name="algorithmparameters-element-assl"></a>Элемент AlgorithmParameters (ASSL)
  Содержит коллекцию параметров для алгоритма, используемого в [MiningModel](../objects/miningmodel-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModel>  
   ...  
   <AlgorithmParameters>  
      <AlgorithmParameter>...</AlgorithmParameter>  
   </AlgorithmParameters>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|нет (коллекция)|  
|Значение по умолчанию|нет (коллекция)|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Дочерние элементы|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Коллекция `AlgorithmParameters` содержит расширяемый набор параметров, представленных парами «имя-значение», для алгоритма модели интеллектуального анализа данных. Набор применимых параметров зависит от алгоритма. Дополнительные сведения о параметрах конкретного алгоритма см. в соответствующей документации по этому алгоритму.  
  
 Выборка доступных параметров алгоритма, включая информацию для проверки и отображения, может быть выполнена из набора строк схемы DMSCHEMA_MINING_SERVICE_PARAMETERS.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Algorithm &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
