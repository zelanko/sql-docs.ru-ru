---
title: Элемент DatabasePermission (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DatabasePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DatabasePermission
helpviewer_keywords:
- DatabasePermission element
ms.assetid: 6dcb9136-a40d-42e3-ad3b-b8ce8c7ca78c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a904f12b86d6449c11f354a790503dc1bd93ffbe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106664"
---
# <a name="databasepermission-element-assl"></a>Элемент DatabasePermission (ASSL)
  Определяет разрешения по умолчанию в [базы данных](database-element-assl.md) для конкретного элемента [роли](role-element-assl.md) элемент.  
  
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
|Тип данных и длина|[Разрешение](../data-type/permission-data-type-assl.md)|  
|Значение по умолчанию|False|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DatabasePermissions](../collections/databasepermissions-element-assl.md)|  
|Дочерние элементы|[Администрирование](../properties/administer-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Объекты `DatabasePermission` могут существовать только для ролей, принадлежащих базе данных, а для каждой роли может существовать только один объект `DatabasePermission`.  
  
 Этот элемент имеет следующие проверки в DeploymentMode со значением 2 (табличные модели).  
  
-   *Администрирование* присваивается значение по умолчанию атрибут `False`, за исключением случаев, когда пользователь имеет права администратора. Для пользователей с административными правами доступа атрибут имеет значение `True`.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Role &#40;ASSL&#41;](role-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
