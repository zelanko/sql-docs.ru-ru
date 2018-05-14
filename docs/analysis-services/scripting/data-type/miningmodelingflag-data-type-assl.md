---
title: Тип данных MiningModelingFlag (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ffbf5b43efb72e32b49cf70a1a114a4b2c07b3de
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="miningmodelingflag-data-type-assl"></a>Тип данных MiningModelingFlag (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет примитивный тип данных, представляющий доступные флаги моделирования для элемента [ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) .  
  
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
|Производные элементы|[ModelingFlag](../../../analysis-services/scripting/objects/modelingflag-element-assl.md) (коллекция[ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md) элемента [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md) или [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Имя флага может содержать пробелы. Изначально поддерживаемые значения перечислены в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*MODEL_EXISTENCE_ONLY*|Столбец должен моделироваться с двумя возможными состояниями: значение отсутствует или присутствует, независимо от самих значений в столбце. Это особенно удобно для столбцов во вложенной таблице, где значения распределены по вариантам.|  
|*НЕ NULL*|Столбец не может принимать значения NULL.|  
|*REGRESSOR*|Столбец предоставляет значения регрессора для проверочных вариантов.|  
  
 Дополнительные флаги, зависящие от поставщика, можно использовать, если сторонние поставщики OLE DB или поставщики интеллектуального анализа данных используются в экземпляре служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Тесно связанный элемент в объектной модели AMO — это <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
