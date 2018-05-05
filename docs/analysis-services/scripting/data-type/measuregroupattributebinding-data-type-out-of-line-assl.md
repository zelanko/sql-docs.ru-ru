---
title: Тип данных MeasureGroupAttributeBinding (вне строки) (ASSL) | Документы Microsoft
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
- MeasureGroupAttributeBinding Data Type (out-of-line)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MeasureGroupAttributeBinding data type
ms.assetid: bfe09a95-4e04-4f93-9389-7dd0b4c8f5e4
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9c20cbcc3020fffba41b894d7efcc9c79013b232
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="measuregroupattributebinding-data-type-out-of-line-assl"></a>Тип данных MeasureGroupAttributeBinding (внешний) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет производный тип данных, представляющий внешнюю привязку для атрибута в измерении, включенном в группу мер.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroupAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <GranularityAttributeID>...</GranularityAttributeID>  
   <Source>...</Source>  
</MeasureGroupAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[CubeID](../../../analysis-services/scripting/properties/cubeid-element-assl.md), [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md), [MeasureGroupID](../../../analysis-services/scripting/properties/measuregroupid-element-assl.md), [GranularityAttributeID](../../../analysis-services/scripting/properties/granularityattributeid-element-assl.md), [источника](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
|Производные элементы|[Привязка](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md) ([привязки](../../../analysis-services/scripting/collections/attributes-element-assl.md) коллекцию XML для аналитики (XMLA) [пакета](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) и [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) команды)|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о ожидания привязок см. в разделе [& #40; источники данных и привязки Многомерные службы SSAS & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
