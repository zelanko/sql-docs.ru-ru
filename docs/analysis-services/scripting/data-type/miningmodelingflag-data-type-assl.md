---
title: Тип данных MiningModelingFlag (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- MiningModelingFlag Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1bfa25ee459c8816b272dea2ed01a949d64b7bd9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="miningmodelingflag-data-type-assl"></a>Тип данных MiningModelingFlag (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет тип-примитив, представляющий доступные флаги моделирования для [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Базовые типы данных|String (перечисление)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) ([ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md) коллекцию [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md) или [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 Имя флага может содержать пробелы. Изначально поддерживаемые значения перечислены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|Столбец должен моделироваться с двумя возможными состояниями: значение отсутствует или присутствует, независимо от самих значений в столбце. Это особенно удобно для столбцов во вложенной таблице, где значения распределены по вариантам.|  
|*НЕ NULL*|Столбец не может принимать значения NULL.|  
|*REGRESSOR*|Столбец предоставляет значения регрессора для проверочных вариантов.|  
  
 Дополнительные флаги поставщика может использоваться, если используются сторонние поставщики интеллектуального анализа данных OLE DB или данных в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Тесно связанный элемент в объектной модели AMO — это <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
