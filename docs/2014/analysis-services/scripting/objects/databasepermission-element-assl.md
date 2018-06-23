---
title: Элемент DatabasePermission (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e47203616cc76fa09c0fd0658e7dad8a89c90a9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110239"
---
# <a name="databasepermission-element-assl"></a>Элемент DatabasePermission (ASSL)
  Определяет разрешения по умолчанию в [базы данных](database-element-assl.md) для конкретного элемента [роли](role-element-assl.md) элемента.  
  
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
  
-   *Администрирование* атрибута по умолчанию имеет значение `False`, за исключением случаев, когда пользователь имеет права администратора. Для пользователей с административными правами доступа атрибут имеет значение `True`.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.DatabasePermission>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Role &#40;ASSL&#41;](role-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  