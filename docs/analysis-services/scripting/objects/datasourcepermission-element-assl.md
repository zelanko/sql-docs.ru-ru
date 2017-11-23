---
title: "Элемент DataSourcePermission (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataSourcePermission Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DataSourcePermission element
ms.assetid: 6dc6fb13-034e-479a-902e-27f3fb78c33f
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 98e1742be14d8d7e16bc967e3d5202e046d894d6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="datasourcepermission-element-assl"></a>Элемент DataSourcePermission (ASSL)
  Определяет разрешения по умолчанию в [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) тип данных для конкретного [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataSourcePermissions>  
   <DataSourcePermission xsi:type="Permission">  
      <!-- No child elements other than those from Permission are defined -->  
...</DataSourcePermission>  
</DataSourcePermissions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[Разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может появляться один или несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DataSourcePermissions](../../../analysis-services/scripting/collections/datasourcepermissions-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Объекты**DataSourcePermission** могут существовать только для ролей, принадлежащих базе данных, а для каждой роли может существовать только один объект **DataSourcePermission** .  
  
## <a name="see-also"></a>См. также:  
 [Элемент Role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
