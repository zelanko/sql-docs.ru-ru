---
title: Элемент AlgorithmParameters (ASSL) | Документы Microsoft
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
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c73495677fd6a1eaf8ff1c70f154bf240b04e709
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192986"
---
# <a name="algorithmparameters-element-assl"></a>Элемент AlgorithmParameters (ASSL)
  Содержит коллекцию параметров для алгоритма, используемого в [MiningModel](../objects/miningmodel-element-assl.md) элемента.  
  
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
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Algorithm &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [Набор строк DMSCHEMA_MINING_SERVICE_PARAMETERS](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  