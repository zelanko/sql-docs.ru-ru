---
title: "Тип данных MiningModelColumn (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MiningModelColumn Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MiningModelColumn
helpviewer_keywords: MiningModelColumn data type
ms.assetid: de8bf815-43b4-4983-bdb9-b67e8563be0e
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b370120671fc14afee8cfc8838f3e918fb9de364
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="miningmodelcolumn-data-type-assl"></a>Тип данных MiningModelColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет тип-примитив, представляющий сведения о столбце в [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelColumn>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <SourceColumnID>...</SourceColumnID>  
            <Usage>...</Usage>  
            <Translations>...</Translations>  
      <Columns>...</Columns>  
      <ModelingFlags>...</ModelingFlags>  
      <Annotations>...</Annotations>  
</MiningModelColumn>  
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
|Дочерние элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [столбцы](../../../analysis-services/scripting/collections/columns-element-assl.md), [описание](../../../analysis-services/scripting/properties/description-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md), [SourceColumnID](../../../analysis-services/scripting/properties/sourcecolumnid-element-assl.md), [переводы](../../../analysis-services/scripting/collections/translations-element-assl.md), [использования](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)|  
|Производные элементы|[Столбец](../../../analysis-services/scripting/objects/column-element-assl.md) ([столбцы](../../../analysis-services/scripting/collections/columns-element-assl.md), коллекция [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.MiningModelColumn>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
