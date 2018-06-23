---
title: Тип ScalarMiningStructureColumn Measurebinding (ASSL) | Документы Microsoft
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
api_name:
- ScalarMiningStructureColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ScalarMiningStructureColumn
helpviewer_keywords:
- ScalarMiningStructureColumn data type
ms.assetid: 8f4afc15-601c-4189-bc45-f5a216aed879
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 15e88a5e82dc960e3428587b8d74a046781b90ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190525"
---
# <a name="scalarminingstructurecolumn-data-type-assl"></a>Тип ScalarMiningStructureColumn MeasureBinding (ASSL)
  Определяет производный тип данных, представляющий [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) элемент, который содержит скалярные значения, в отличие от вложенных таблиц, связанных с [TableMiningStructureColumn](tableminingstructurecolumn-data-type-assl.md) элемент содержащий вложенные таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ScalarMiningStructureColumn>  
   <!-- The following elements extend MiningStructureColumn -->  
   <IsKey>...</IsKey>  
   <Source>...</Source>  
   <Distribution>...</Distribution>  
   <ModelingFlags>...</ModelingFlags>  
   <Content>...</Content>  
   <ClassifiedColumnID>...</<ClassifiedColumnI  
   <DiscretizationMethod>...</DiscretizationMethod>  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   <KeyColumns>...</KeyColumns>  
   <NameColumn>...</NameColumn>  
   <Translations>...</Translations>  
</ScalarMiningStructureColumn>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[MiningStructureColumn](miningstructurecolumn-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[ClassifiedColumnID](../properties/id-element-assl.md), [содержимого](../properties/content-element-assl.md), [DiscretizationBucketCount](../properties/discretizationbucketcount-element-assl.md), [DiscretizationMethod](../properties/discretizationmethod-element-assl.md), [распространения](../properties/distribution-element-assl.md), [IsKey](../properties/iskey-element-assl.md), [KeyColumns](../collections/columns-element-assl.md), [ModelingFlags](../collections/modelingflags-element-assl.md), [NameColumn](../objects/column-element-assl.md), [источника](../properties/source-element-binding-assl.md), [ Переводы](../collections/translations-element-assl.md)|  
|Производные элементы|[Столбец](../objects/column-element-assl.md) ([столбцы](../collections/columns-element-assl.md) коллекцию [MiningStructure](../objects/miningstructure-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  