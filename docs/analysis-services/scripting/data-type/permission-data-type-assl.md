---
title: "Тип данных permission (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Permission Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Permission
helpviewer_keywords:
- Permission data type
ms.assetid: 5f309544-59f8-4432-b1eb-b7c1a049f8df
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 56534a2dfba72ed8f620da5b7e8959ccb3f04d24
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="permission-data-type-assl"></a>Тип данных Permission (ASSL)
  Определяет абстрактный примитивный тип данных, представляющий сведения об отдельном разрешении.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Permission>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <RoleID>...</RoleID>  
   <Description>...</Description>  
   <Process>...</Process>  
   <ReadDefinition>...</ReadDefinition>  
   <Read>...</Read>  
   <Write>...</Write>  
   <Annotations>...</Annotations>  
</Permission>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md), [DimensionPermission](../../../analysis-services/scripting/data-type/dimensionpermission-data-type-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [описание](../../../analysis-services/scripting/properties/description-element-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [имя ](../../../analysis-services/scripting/properties/name-element-assl.md), [Процесс](../../../analysis-services/scripting/properties/process-element-assl.md), [чтения](../../../analysis-services/scripting/properties/read-element-assl.md), [ReadDefinition](../../../analysis-services/scripting/properties/readdefinition-element-assl.md), [RoleID](../../../analysis-services/scripting/properties/roleid-element-assl.md), [записи](../../../analysis-services/scripting/properties/write-element-assl.md)|  
|Производные элементы|Нет|  
  
## <a name="remarks"></a>Замечания  
 **Разрешение** служит абстрактным базовым типом для ряда производных типов разрешений используется в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Этот тип данных имеет следующие проверки с параметром DeploymentMode со значением 2 (табличный режим сервера).  
  
-   По умолчанию атрибут*Process* имеет значение **False**, за исключением тех случаев, когда пользователь имеет разрешение **Refresh** . Для пользователей с разрешением **Refresh** значение атрибута *Process* имеет значение **True**.  
  
-   Атрибуту*ReadDefinition* назначается значение **None**, любое другое значение приводит к ошибке.  
  
-   Атрибуту*Read* устанавливается значение **Allowed** для пользователей с разрешением **User** или **None** , если пользователи имеют разрешение **Refresh** ; если пользователь имеет разрешения **User** и **Refresh** , то атрибуту присваивается значение **Allowed**. Для пользователей с административными правами доступа атрибут имеет значение **Allowed**.  
  
-   Атрибуту*Write* назначается значение **None**, любое другое значение приводит к ошибке.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

