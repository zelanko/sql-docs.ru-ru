---
title: "Тип данных CubeDimension (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CubeDimension Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeDimension
helpviewer_keywords:
- CubeDimension data type
ms.assetid: 128ac790-65a1-4e35-b909-8dba2a61b24c
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6e66f279cfff5bd8f80cacedf014eb318c7ad9a4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="cubedimension-data-type-assl"></a>Тип данных CubeDimension (ASSL)
  Определяет примитивный тип данных, представляющий связь между измерением и кубом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimension>  
      <ID>...</ID>  
   <Name>...</Name>  
   <Translations>...</Translations>  
   <DimensionID>...</DimensionID>  
   <Visible>...</Visible>  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
      <Attributes>...</Attributes>  
   <Hierarchies>...</Hierarchies>  
      <Annotations>...</Annotation>  
</CubeDimension>  
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
|Дочерние элементы|[AllMemberAggregationUsage](../../../analysis-services/scripting/properties/allmemberaggregationusage-element-assl.md), [заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [атрибуты](../../../analysis-services/scripting/collections/attributes-element-assl.md), [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md), [иерархий](../../../analysis-services/scripting/collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../../../analysis-services/scripting/properties/hierarchyuniquenamestyle-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [MemberUniqueNameStyle](../../../analysis-services/scripting/properties/memberuniquenamestyle-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md), [видимым](../../../analysis-services/scripting/properties/visible-element-assl.md), [Переводов](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|Производные элементы|[Измерение](../../../analysis-services/scripting/objects/dimension-element-assl.md) ([измерения](../../../analysis-services/scripting/collections/dimensions-element-assl.md) коллекцию [куба](../../../analysis-services/scripting/objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Предусмотрено по одному измерению **CubeDimension** для каждой связи измерений в кубе **Cube**. Объект **CubeDimension** охватывает все группы мер **MeasureGroups** куба.  
  
 Объект **CubeDimension** должен включать [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md) Если измерение содержит какие-то конкретные сведения об иерархии, включая отключение иерархии (и тем самым допускающие выбор которого иерархии относятся к конкретному применению измерения), или обеспечение невидимости иерархии.  
  
 Аналогичным образом **CubeDimension** должен включать [CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md) только в том случае, если измерение содержит какие-то конкретные сведения об атрибуте. (Какой-либо способ, позволяющий выбирать атрибуты, относящиеся к конкретному назначению измерения, не предусмотрен, однако атрибуты можно преобразовать в невидимые.)  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
