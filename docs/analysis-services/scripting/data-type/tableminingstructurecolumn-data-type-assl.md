---
title: Тип данных TableMiningStructureColumn (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01d5afbc2d69985ab571ee55b2583f08d090a446
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="tableminingstructurecolumn-data-type-assl"></a>Тип данных TableMiningStructureColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет производный тип данных, представляющий элемент [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) , который содержит вложенные таблицы, в отличие от скалярных значений, связанных с элементом [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md) , содержащим скалярные значений.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<TableMiningStructureColumn>  
   <!-- The following elements extend MiningStructureColumn -->  
   <ForeignKeyColumn>..</ForeignKeyColumn>  
   <SourceMeasureGroup>..</SourceMeasureGroup>  
   <Columns>..</Columns>  
   <Translations>..</Translations>  
</TableMiningStructureColumn>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Columns](../../../analysis-services/scripting/collections/columns-element-assl.md), [ForeignKeyColumn](../../../analysis-services/scripting/objects/foreignkeycolumn-element-assl.md), [SourceMeasureGroup](../../../analysis-services/scripting/objects/sourcemeasuregroup-element-assl.md), [Translations](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|Производные элементы|[Column](../../../analysis-services/scripting/objects/column-element-assl.md) (коллекция[Columns](../../../analysis-services/scripting/collections/columns-element-assl.md) элемента [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
