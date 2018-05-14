---
title: Элемент ForeignKeyColumn (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49b159107dc3bfbd8f888265cef8ca64a08857c6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="foreignkeycolumn-element-assl"></a>Элемент ForeignKeyColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет соединение с родительской таблицей для реляционного источника данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ForeignKeyColumns>  
   <ForeignKeyColumn xsi:type="DataItem">...</ForeignKeyColumn>  
</ForeignKeyColumns>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ForeignKeyColumns](../../../analysis-services/scripting/collections/foreignkeycolumns-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о **DataItem** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства **DataItem** введите см. в разделе [данных DataItem Тип &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Элемент, соответствующий родителю параметра **ForeignKeyColumns** коллекции в объектной модели Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных TableMiningStructureColumn &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)   
 [Тип данных MiningStructureColumn &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)   
 [Элемент MiningStructure &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
