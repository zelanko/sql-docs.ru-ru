---
title: "Тип данных RowBinding (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: RowBinding Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: RowBinding
helpviewer_keywords: RowBinding data type
ms.assetid: 5a49a6e3-25f3-43c8-8529-bcf245b02415
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5bed109c81e253e2124478c7de6c7cb411695c76
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="rowbinding-data-type-assl"></a>Тип данных RowBinding (ASSL)
  Определяет производный тип данных, представляющий привязку к строкам таблицы в [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RowBinding>  
   <!-- The following elements extend Binding -->  
   <TableID>...</TableID>  
</RowBinding>  
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
|Дочерние элементы|[TableID](../../../analysis-services/scripting/properties/tableid-element-assl.md)|  
|Производные элементы|В разделе [привязки](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о **привязки** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) **привязки** тип и иерархию наследования **привязки**  типов, в разделе [тип привязки данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [&#40; источники данных и привязки Многомерные службы SSAS &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.RowBinding>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
