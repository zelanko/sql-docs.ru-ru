---
title: Тип данных MiningModelingFlag (ASSL) | Документация Майкрософт
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
- MiningModelingFlag Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelingFlag
helpviewer_keywords:
- MiningModelingFlag data type
ms.assetid: aaa72ba8-051e-4b01-b1e9-9c8d83b8b752
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ece92d63c0d66c1ef845ce2d28d3317b2f65d66f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167525"
---
# <a name="miningmodelingflag-data-type-assl"></a>Тип данных MiningModelingFlag (ASSL)
  Определяет тип-примитив, представляющий доступные флаги моделирования для [ModelingFlag](../objects/modelingflag-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelingFlag>...</MiningModelingFlag>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|String (перечисление)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|[ModelingFlag](../objects/modelingflag-element-assl.md) ([ModelingFlags](../collections/modelingflags-element-assl.md) коллекцию [MiningModelColumn](miningmodelcolumn-data-type-assl.md) или [ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Имя флага может содержать пробелы. Изначально поддерживаемые значения перечислены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|Столбец должен моделироваться с двумя возможными состояниями: значение отсутствует или присутствует, независимо от самих значений в столбце. Это особенно удобно для столбцов во вложенной таблице, где значения распределены по вариантам.|  
|*NOT NULL*|Столбец не может принимать значения NULL.|  
|*РЕГРЕССОР*|Столбец предоставляет значения регрессора для проверочных вариантов.|  
  
 Дополнительные флаги поставщика может использоваться, если используются сторонние поставщики интеллектуального анализа данных OLE DB или данных на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Тесно связанный элемент в объектной модели AMO — это <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
