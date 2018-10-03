---
title: Тип данных permission (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Permission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Permission
helpviewer_keywords:
- Permission data type
ms.assetid: 5f309544-59f8-4432-b1eb-b7c1a049f8df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d12fb71a8ed19ca083e8ec506fba6338f6b58a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101947"
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
|Производные типы данных|[CubePermission](../objects/cubepermission-element-assl.md), [DatabasePermission](../objects/databasepermission-element-assl.md), [DimensionPermission](permission-data-type-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [описание](../properties/description-element-assl.md), [идентификатор](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [имя](../properties/name-element-assl.md), [Процесс](../properties/process-element-assl.md), [чтения](../properties/read-element-assl.md), [ReadDefinition](../properties/readdefinition-element-assl.md), [RoleID](../properties/roleid-element-assl.md), [записи](../properties/write-element-assl.md)|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `Permission` Служит абстрактным базовым типом для ряда производных типов разрешений используется в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Этот тип данных имеет следующие проверки с параметром DeploymentMode со значением 2 (табличный режим сервера).  
  
-   *Процесс* присваивается значение по умолчанию атрибут `False`, за исключением случаев, когда пользователь имеет **обновить** разрешение. Для пользователей с **обновить** разрешение *процесс* атрибут имеет значение `True`.  
  
-   *ReadDefinition* атрибут имеет значение `None`; любое другое значение приводит к ошибке.  
  
-   *Чтение* атрибут имеет значение `Allowed` для пользователей с **пользователя** разрешение и `None` Если пользователи имеют разрешение **обновить** ; Если пользователь имеет **Пользователя** и **обновить** разрешения, то атрибуту присваивается `Allowed`. Для пользователей с административными правами доступа атрибут имеет значение `Allowed`.  
  
-   *Запись* атрибут имеет значение `None`; любое другое значение приводит к ошибке.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
