---
title: Элемент MiningStructure (ASSL) | Документация Майкрософт
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
- MiningStructure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructure
helpviewer_keywords:
- MiningStructure element
ms.assetid: b943cd92-0ed8-4bd8-8fbc-7dab0534aede
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ed39aafbe937c637abd7a6ec67fbd7343b62b116
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271830"
---
# <a name="miningstructure-element-assl"></a>Элемент MiningStructure (язык ASSL)
  Определяет структуру для набора моделей интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructures>  
   <MiningStructure>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <Source>...</Source>  
      <CreatedTimestamp>...</<CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <CacheMode>...</CacheMode>  
            <Columns>...</Columns>  
      <State>...</State>  
      <HoldoutActualSize>...</HoldoutActualSize>  
      <HoldoutMaxCases>...</HoldoutMaxCases>  
      <HoldoutMaxPercent>...</HoldoutMaxPercent>  
      <HoldoutSeed>...</HoldoutSeed>        
            <MiningStructurePermissions>...</<MiningStructurePermissions>  
            <MiningModels>...</MiningModels>  
            <Annotations>...</Annotations>  
   </MiningStructure>  
</MiningStructures>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MiningStructures](../collections/miningstructures-element-assl.md)|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [CacheMode](../properties/cachemode-element-assl.md), [параметры сортировки](../properties/collation-element-assl.md), [столбцы](../collections/columns-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [описание ](../properties/description-element-assl.md), [ErrorConfiguration](errorconfiguration-element-assl.md),<br /><br /> [HoldoutActualSize](../properties/holdoutactualsize-element.md),<br /><br /> [HoldoutMaxCases](../properties/holdoutmaxcases-element.md),<br /><br /> [HoldoutMaxPercent](../properties/holdoutmaxpercent-element.md),<br /><br /> [HoldoutSeed](../properties/holdoutseed-element.md),<br /><br /> [Идентификатор](../properties/id-element-assl.md), [языка](../properties/language-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [MiningModels](../collections/miningmodels-element-assl.md), [ MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md), [имя](../properties/name-element-assl.md), [источника](../properties/source-element-binding-assl.md), [состояние](../properties/state-element-assl.md), [переводы](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Структура интеллектуального анализа данных определяет столбцы и привязки. После того, как структура интеллектуального анализа данных определена, ее можно использовать для определения различных моделей интеллектуального анализа данных. Структура интеллектуального анализа данных и входящие в нее модели могут обрабатываться независимо.  
  
> [!NOTE]  
>  В [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] введено использование контрольных свойств `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` и `HoldoutActualSize`. Эти свойства позволяют определить секцию структуры интеллектуального анализа данных, которая действует как проверочный набор для всех моделей интеллектуального анализа данных, связанных с этой структурой. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] не поддерживает эти свойства. Поэтому при попытке использовать эти свойства в экземпляре [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратят ошибку.  
  
## <a name="drillthrough-to-structure-columns"></a>Детализация столбцов структуры  
 В [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], будет добавлен новый элемент разрешения [элемент MiningStructurePermissions &#40;ASSL&#41; ](../collections/miningstructurepermissions-element-assl.md) коллекции. При добавлении `AllowDrillthrough` разрешение на оба [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md) и [MiningModelPermission](miningmodelpermission-element-assl.md) коллекций, детализация включена из модели интеллектуального анализа данных к структуре, и таким образом, Члены роли, обладающей `AllowDrillthrough` разрешения на модель запросов к модели интеллектуального анализа данных и возвращать столбцы структуры, которые не были включены в модели.  
  
 Поэтому, чтобы защитить конфиденциальные или персональные данные, необходимо настроить для представления источников данных маскирование конфиденциальных данных, а разрешение `AllowDrillthrough` для структуры интеллектуального анализа данных предоставлять только при необходимости. Дополнительные сведения см. в разделе [элемент AllowDrillThrough &#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md).  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Элемент MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)   
 [ВЫБЕРИТЕ &AMP;#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&AMP;#41;](/sql/dmx/select-dmx)  
  
  
