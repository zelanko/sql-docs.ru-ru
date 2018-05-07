---
title: Элемент MiningStructure (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7639078695b80d45f8fc90d6d925ea2335314d15
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="miningstructure-element-assl"></a>Элемент MiningStructure (язык ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Родительские элементы|[MiningStructures](../../../analysis-services/scripting/collections/miningstructures-element-assl.md)|  
|Дочерние элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CacheMode](../../../analysis-services/scripting/properties/cachemode-element-assl.md), [сортировки](../../../analysis-services/scripting/properties/collation-element-assl.md), [столбцы](../../../analysis-services/scripting/collections/columns-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [описание ](../../../analysis-services/scripting/properties/description-element-assl.md), [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md),<br /><br /> [HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md),<br /><br /> [HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md),<br /><br /> [HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md),<br /><br /> [HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md),<br /><br /> [Идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [язык](../../../analysis-services/scripting/properties/language-element-assl.md), [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [MiningModels](../../../analysis-services/scripting/collections/miningmodels-element-assl.md), [ MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md), [источника](../../../analysis-services/scripting/properties/source-element-binding-assl.md), [состояние](../../../analysis-services/scripting/properties/state-element-assl.md), [переводов](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Структура интеллектуального анализа данных определяет столбцы и привязки. После того, как структура интеллектуального анализа данных определена, ее можно использовать для определения различных моделей интеллектуального анализа данных. Структура интеллектуального анализа данных и входящие в нее модели могут обрабатываться независимо.  
  
> [!NOTE]  
>  Свойства контрольных **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, и **HoldoutActualSize**, были введены в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Эти свойства позволяют определить секцию структуры интеллектуального анализа данных, которая действует как проверочный набор для всех моделей интеллектуального анализа данных, связанных с этой структурой. [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] не поддерживает эти свойства. Поэтому при попытке использовать эти свойства в экземпляре [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратят ошибку.  
  
## <a name="drillthrough-to-structure-columns"></a>Детализация столбцов структуры  
 В [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], будет добавлен новый элемент разрешений [элемент MiningStructurePermissions &#40;ASSL&#41; ](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) коллекции. При добавлении **AllowDrillthrough** разрешение на оба [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) и [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md) коллекций, включена детализация из модели интеллектуального анализа данных к структуре, таким образом, что члены роли, имеющей **AllowDrillthrough** для модели разрешения запросов к модели интеллектуального анализа данных и возвращать столбцы структуры, которые не были включены в модель.  
  
 Поэтому, чтобы защитить конфиденциальные или персональные данные, необходимо настроить для представления источников данных маскирование конфиденциальных данных, а разрешение **AllowDrillthrough** для структуры интеллектуального анализа данных предоставлять только при необходимости. Дополнительные сведения см. в разделе [элемент AllowDrillThrough &#40;ASSL&#41;](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Элемент MiningModel &#40;ASSL&#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Объекты &#40;ASSL&#41;](../../../analysis-services/scripting/objects/objects-assl.md)   
 [ВЫБЕРИТЕ &AMP;#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&AMP;#41;](../../../dmx/select-dmx.md)  
  
  
