---
title: Элемент MiningStructurePermission (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- MiningStructurePermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningStructurePermission
helpviewer_keywords:
- MiningStructurePermission element
ms.assetid: 4ba2bfd2-9003-4eed-8049-a74d452894ea
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7002a55d6ba81c76bb7b1bf3d96ccd2e5b4d6f7d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="miningstructurepermission-element-assl"></a>Элемент MiningStructurePermission (язык ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет разрешения членов элемента [роли](../../../analysis-services/scripting/objects/role-element-assl.md) имеют для отдельных [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructurePermissions>  
   <MiningStructurePermission xsi:type="Permission">  
      <AllowDrillthrough>...</AllowDrillthrough>  
  
      <!-- This element also inherits all the child elements listed in Permission -->  
   </MiningStructurePermission>  
</MiningStructurePermissions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[Разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
 В [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], разрешение **AllowDrillthrough** была расширена для применения к структуре интеллектуального анализа данных. При назначении роли разрешения любой пользователь, являющийся членом этой роли, может отправлять прямые запросы к структуре интеллектуального анализа данных с помощью следующего синтаксиса:  
  
```  
SELECT <structure column list> FROM <structure>.CASES  
```  
  
 Кроме того, если включено разрешение **AllowDrillthrough** как для структуры, так и для модели интеллектуального анализа данных, пользователи могут запрашивать столбцы структуры, не включенные в модель интеллектуального анализа данных, с помощью следующего синтаксиса:  
  
```  
SELECT StructureColumn('<structure column name>' FROM <model>.CASES  
```  
  
 Например, создается модель с использованием только столбцов, содержащих ключ клиента, доход клиента и покупки клиента. С помощью детализации пользователь может возвращать другие столбцы структуры, не включенные в модель интеллектуального анализа данных, например контактные сведения клиента.  
  
 Поэтому, чтобы защитить конфиденциальные или персональные данные, необходимо так сконструировать представление источника данных, чтобы замаскировать персональные данные, а разрешение **AllowDrillthrough** на структуру интеллектуального анализа данных предоставлять только при необходимости.  
  
 Дополнительные сведения см. в разделе [Запросы детализации (интеллектуальный анализ данных)](../../../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.MiningModel.AllowDrillThrough%2A>   
 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModel.AllowDrillThrough%2A>   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
