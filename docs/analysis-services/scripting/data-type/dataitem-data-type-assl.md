---
title: "Тип данных DataItem (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataItem Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DataItem
helpviewer_keywords: DataItem data type
ms.assetid: f4f5155f-9c3d-49a1-a390-a9c734fafbce
caps.latest.revision: "44"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ec40eca06225eef5d9c7e505e4fe2c9dee6972b1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="dataitem-data-type-assl"></a>Тип данных DataItem (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет тип-примитив, представляющий характеристики, связанные с данными, элемента данных, например столбца или атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataItem>  
   <DataType>...</DataType>  
   <DataSize>...</DataSize>  
   <MimeType>...</MimeType>  
   <NullProcessing>...</NullProcessing>  
   <Trimming>...</Trimming>  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
      <Collation>...</Collation>  
   <Format>...</Format>  
   <Source>...</Source>  
   <Annotations>...</Annotations>  
</DataItem>  
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
|Дочерние элементы|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Collation](../../../analysis-services/scripting/properties/collation-element-assl.md), [DataSize](../../../analysis-services/scripting/properties/datasize-element-assl.md), [DataType](../../../analysis-services/scripting/properties/datatype-element-assl.md), [Format](../../../analysis-services/scripting/properties/format-element-assl.md), [InvalidXmlCharacters](../../../analysis-services/scripting/properties/invalidxmlcharacters-element-assl.md), [MimeType](../../../analysis-services/scripting/properties/mimetype-element-assl.md), [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md), [Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md), [Trimming](../../../analysis-services/scripting/properties/trimming-element-assl.md)|  
|Производные элементы|См. таблицу в разделе «Примечания».|  
  
## <a name="remarks"></a>Remarks  
 Тип данных **DataItem** используется для любого элемента, который можно привязать, например меры, ключа атрибута и имени атрибута. Соответствующие подробности и применимые значения по умолчанию зависят от использования; например, имена атрибутов должны быть строками.  
  
 Экземпляр служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] принимает только определенный набор типов данных. Использование других типов данных приводит к ошибке, а не к неявному преобразованию к одному из допустимых типов.  
  
 В следующей таблице приведены элементы типа **DataItem**.  
  
|Родительский элемент|Элемент типа **DataItem**|Комментарии|  
|--------------------|----------------------------------|--------------|  
|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|[CaptionColumn](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) или [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[CustomRollupColumn](../../../analysis-services/scripting/objects/customrollupcolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) или [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[CustomRollupPropertiesColumn](../../../analysis-services/scripting/objects/customrolluppropertiescolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) или [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[Столбец KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) или [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[Столбец NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) или [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[SkippedLevelsColumn](../../../analysis-services/scripting/objects/skippedlevelscolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) или [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[UnaryOperatorColumn](../../../analysis-services/scripting/objects/unaryoperatorcolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) или [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[Меры](../../../analysis-services/scripting/objects/measure-element-assl.md)|[Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|**Source** типа **DataItem** должен иметь тип [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md), [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)или [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|[Столбец KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) или [InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[Столбец KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[Столбец NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|[ForeignKeyColumn](../../../analysis-services/scripting/objects/foreignkeycolumn-element-assl.md)|**Source** типа **DataItem** должен иметь тип [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
