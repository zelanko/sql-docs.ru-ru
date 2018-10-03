---
title: Элемент Distribution (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Distribution Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Distribution
helpviewer_keywords:
- Distribution element
ms.assetid: a1309b90-8ad8-431b-a918-67f0cdd4fd20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f71addc3c9c793a19e88e52bb0b82519b5f33f1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166454"
---
# <a name="distribution-element-assl"></a>Элемент Distribution (ASSL)
  Содержит значение поставщика, которое описывает как скалярные значения распределяются внутри столбца [MiningStructure](../objects/miningstructure-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Distribution>...</Distribution>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Доступные значения `Distribution` элемент, такой как *обычный* или *универсальный код,* являются специфическими для каждого поставщика алгоритма интеллектуального анализа данных. Дополнительные сведения о допустимых значениях элемента `Distribution` см. в документации по поставщику алгоритма интеллектуального анализа данных.  
  
 Элемент, соответствующий родителю параметра `Distribution` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
