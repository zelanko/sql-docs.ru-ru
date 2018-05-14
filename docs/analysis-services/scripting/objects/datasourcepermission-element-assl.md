---
title: Элемент DataSourcePermission (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c6dabefaa319bb847975da03b5593e5dc79e4268
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="datasourcepermission-element-assl"></a>Элемент DataSourcePermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
 Объекты**DataSourcePermission** могут существовать только для ролей, принадлежащих базе данных, а для каждой роли может существовать только один объект **DataSourcePermission** .  
  
## <a name="see-also"></a>См. также  
 [Элемент Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
