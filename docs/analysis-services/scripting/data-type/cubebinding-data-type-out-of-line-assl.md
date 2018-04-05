---
title: Тип данных CubeBinding (вне строки) (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- CubeBinding Data Type (out-of-line)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeBinding
helpviewer_keywords:
- CubeBinding data type
ms.assetid: 5e1ee8ef-855c-4f3d-ae21-a33360d00d66
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c270c264bb018f499e36fc5b3f54e959d4838f20
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="cubebinding-data-type-out-of-line-assl"></a>Тип данных CubeBinding (внешний) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет тип-примитив, представляющий связь между [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемент и [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md) элемента.  
  
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
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Источник данных](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [группы мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Производные элементы|[Привязка](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md) ([привязки](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md) коллекцию [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) или [пакета](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) команды)|  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения о ожидания привязок см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также:  
 [Тип привязки данных &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
