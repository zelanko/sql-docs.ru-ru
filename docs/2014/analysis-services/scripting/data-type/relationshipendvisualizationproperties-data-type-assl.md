---
title: Тип данных RelationshipEndVisualizationProperties (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 11f9a10f-d36c-4faf-b595-3fe969d1935e
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58348251e9ea00c4f6eebc5fcec067683e49a3a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161275"
---
# <a name="relationshipendvisualizationproperties-data-type-assl"></a>Тип данных RelationshipEndVisualizationProperties (язык ASSL)
  Определяет примитивный тип данных, который представляет элемент связи в связи.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationshipEnd>  
   <FolderPosition>...</FolderPosition>  
   <ContextualNameRule>...</ContextualNameRule>  
   <DefaultDetailsPosition>...</DefaultDetailsPosition>  
   <DisplayKeyPosition>...</DisplayKeyPosition>  
   <CommonIdentifierPosition>...</CommonIdentifierPosition>  
   <IsDefaultMeasure>...</IsDefaultMeasure>  
   <IsDefaultImage>...</IsDefaultImage>  
   <SortPropertiesPosition>...</SortPropertiesPosition>  
</RelationshipEnd>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[RelationshipEnd](relationshipend-data-type-assl.md)|  
|Дочерние элементы|[FolderPosition](../../xmla/xml-elements-properties/folderposition-element-xml.md), [ContextualNameRule](../../xmla/xml-elements-properties/contextualnamerule-element-xml.md), [DefaultDetailsPosition](../../xmla/xml-elements-properties/defaultdetailsposition-element-xml.md), [DisplayKeyPosition](../../xmla/xml-elements-properties/displaykeyposition-element-xml.md), [CommonIdentifierPosition](../../xmla/xml-elements-properties/commonidentifierposition-element-xml.md), [IsDefaultMeasure](../../xmla/xml-elements-properties/isdefaultmeasure-element-xml.md), [IsDefaultImage](../../xmla/xml-elements-properties/isdefaultimage-element-xml.md), [SortPropertiesPosition](../../xmla/xml-elements-properties/sortpropertiesposition-element-xml.md)|  
|Производные элементы||  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.RelationshipEnd>.  
  
  
