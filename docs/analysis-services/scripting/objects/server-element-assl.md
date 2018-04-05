---
title: Элемент Server (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- Server Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- server
helpviewer_keywords:
- Server element
ms.assetid: 92ca67f6-817e-4a75-9244-8f8bcf412190
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f614b8a35253208970ee54a3261c35c0c169bf40
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="server-element-assl"></a>Элемент Server (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Описывает экземпляр служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Server>  
   <!—These elements are common to each major object -->  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <Description>...</Description>  
   <Annotations>...</Annotations>  
   <!-- server elements or properties -->  
   <ProductName>...</ProductName>  
   <Edition>...</Edition>  
   <EditionId>...</Edition>  
   <Version>...</Version>  
   <ServerMode>...</ServerMode>  
   <ProductLevel>...</Databases>  
   <Databases>...</Databases>  
   <Assemblies>...</Assemblies>  
   <Traces>...</Traces>  
   <Roles>...</Roles>  
   <ServerProperties>...</ServerProperties>  
</Server>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Имя](../../../analysis-services/scripting/properties/name-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [описание](../../../analysis-services/scripting/properties/description-element-assl.md), [заметок ](../../../analysis-services/scripting/collections/annotations-element-assl.md), [ProductName](../../../analysis-services/scripting/properties/productname-element-assl.md), [Edition](../../../analysis-services/scripting/properties/edition-element-assl.md), [EditionId](../../../analysis-services/xmla/xml-elements-properties/editionid-element.md), [версии](../../../analysis-services/scripting/properties/version-element-assl.md), [ServerMode](../../../analysis-services/xmla/xml-elements-properties/editionid-element.md), [ProductLevel](../../../analysis-services/xmla/xml-elements-properties/productlabel-element.md), [баз данных](../../../analysis-services/scripting/collections/databases-element-assl.md), [сборки](../../../analysis-services/scripting/collections/assemblies-element-assl.md), [трассировок](../../../analysis-services/scripting/collections/traces-element-assl.md), [роли](../../../analysis-services/scripting/collections/roles-element-assl.md), [ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)>|  
  
## <a name="remarks"></a>Remarks  
 **Сервера** элемент представляет экземпляр [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]и служит в качестве самый верхний узел в иерархии узлов языка сценариев служб Analysis Services (ASSL).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Server>.  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
