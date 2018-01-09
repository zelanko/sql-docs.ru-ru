---
title: "Базы данных элемент (ASSL) | Документы Microsoft"
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
apiname: Database Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DATABASE
helpviewer_keywords: Database element
ms.assetid: c3bc7eaf-ed0d-4395-a3b7-8d9cfacfe911
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2154ccd56f5b1fac0388b68a45c0649860f23f98
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="database-element-assl"></a>Элемент Database (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Определяет [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Databases>  
   <Database>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastUpdate>...</LastUpdate>  
      <Description>...</Description>  
      <State>   </State>  
      <AggregationPrefix>...</AggregationPrefix>  
      <EstimatedSize>...</EstimatedSize>  
      <LastProcessed>...</LastProcessed>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <Visible>...</Visible>  
      <MasterDatasourceID>...</MasterDataSourceID>  
      <Accounts>...</Accounts>  
      <DataSources>...</DataSources>  
      <DataSourceViews>...</DataSourceViews>  
      <Dimensions>...</Dimensions>  
      <Cubes>...</Cubes>  
      <MiningStructures>...</MiningStructures>  
            <Roles>...</Roles>  
      <Assemblies>...</Assemblies>  
      <DatabasePermissions>...</DatabasePermissions>  
            <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Database>  
</Databases>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Базы данных](../../../analysis-services/scripting/collections/databases-element-assl.md)|  
|Дочерние элементы|[Учетные записи](../../../analysis-services/scripting/collections/accounts-element-assl.md), [AggregationPrefix](../../../analysis-services/scripting/properties/aggregationprefix-element-assl.md), [заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [сборки](../../../analysis-services/scripting/collections/assemblies-element-assl.md), [сортировки](../../../analysis-services/scripting/properties/collation-element-assl.md), [ CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [кубы](../../../analysis-services/scripting/collections/cubes-element-assl.md), [DatabasePermissions](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md), [DataSources](../../../analysis-services/scripting/collections/datasources-element-assl.md), [DataSourceViews](../../../analysis-services/scripting/collections/datasourceviews-element-assl.md), [Описание](../../../analysis-services/scripting/properties/description-element-assl.md), [измерения](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [EstimatedSize](../../../analysis-services/scripting/properties/estimatedsize-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [языка](../../../analysis-services/scripting/properties/language-element-assl.md), [ LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [LastUpdate](../../../analysis-services/scripting/properties/lastupdate-element-assl.md), [MasterDatasourceID](../../../analysis-services/scripting/properties/masterdatasourceid-element-assl.md), [MiningStructures](../../../analysis-services/scripting/collections/miningstructures-element-assl.md), [Имя](../../../analysis-services/scripting/properties/name-element-assl.md), [ролей](../../../analysis-services/scripting/collections/roles-element-assl.md), [состояние](../../../analysis-services/scripting/properties/state-element-assl.md), [переводы](../../../analysis-services/scripting/collections/translations-element-assl.md), [видимыми](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Database>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Server &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
