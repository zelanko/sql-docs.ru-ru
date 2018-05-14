---
title: Тип данных StandardAction (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 67e1de4dfcc2c87079cb5c2b1158e4374a03d959
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="standardaction-data-type-assl"></a>Тип данных StandardAction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет производный тип данных, представляющий любой элемент [Action](../../../analysis-services/scripting/objects/action-element-assl.md) , отличный от элемента [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md) или [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<StandardAction>  
   <!-- The following elements extend Action -->  
   <Expression>...</Expression>  
</StandardAction>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Действие](../../../analysis-services/scripting/data-type/action-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Выражение](../../../analysis-services/scripting/properties/expression-element-assl.md)|  
|Производные элементы|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md) ([действия](../../../analysis-services/scripting/collections/actions-element-assl.md) коллекцию [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) или [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
