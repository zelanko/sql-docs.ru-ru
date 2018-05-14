---
title: Элемент DatabasePermission (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 855c632b78beb3a5ba75ff7acf31b72fff229e95
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="databasepermission-element-assl"></a>Элемент DatabasePermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет разрешения по умолчанию в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) для конкретного элемента [роли](../../../analysis-services/scripting/objects/role-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DatabasePermissions>  
      <DatabasePermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <Administer>...</Administer>  
...</DatabasePermission>  
</DatabasePermissions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[Разрешение](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Значение по умолчанию|False|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DatabasePermissions](../../../analysis-services/scripting/collections/databasepermissions-element-assl.md)|  
|Дочерние элементы|[Администрирование](../../../analysis-services/scripting/properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Объекты**DatabasePermission** могут существовать только для ролей, принадлежащих базе данных, а для каждой роли может существовать только один объект **DatabasePermission** .  
  
 Этот элемент имеет следующие проверки в DeploymentMode со значением 2 (табличные модели).  
  
-   По умолчанию атрибут*Administer* имеет значение **False**, за исключением тех случаев, когда пользователь имеет административные права доступа. Для пользователей с административными правами доступа атрибут имеет значение **True**.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Role & #40; ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
