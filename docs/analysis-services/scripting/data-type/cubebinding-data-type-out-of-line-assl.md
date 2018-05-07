---
title: Тип данных CubeBinding (вне строки) (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 74a782f551ad31e583c5d9fd33d02f7d975ec7b8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="cubebinding-data-type-out-of-line-assl"></a>Тип данных CubeBinding (внешний) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет примитивный тип данных, представляющий связь между элементом [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) и элементом [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeBinding>  
   <ID>...</ID>  
   <DataSourceID>...</DataSourceID>  
   <DataSource>...</DataSource>  
   <MeasureGroup>...</MeasureGroup>  
</CubeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Производные элементы|[Binding](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md) (коллекция[Bindings](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md) команд [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) или [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) )|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о ожидания привязок см. в разделе [& #40; источники данных и привязки Многомерные службы SSAS & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также:  
 [Тип привязки данных & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
