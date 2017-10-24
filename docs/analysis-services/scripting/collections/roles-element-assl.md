---
title: "Элемент Roles (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Roles Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Roles
helpviewer_keywords:
- Roles element
ms.assetid: 4191b7ce-bae4-4200-8550-3904420efafd
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d3c077f05af1af38b2160d07bedf3e6ae401acd0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="roles-element-assl"></a>Элемент Roles (ASSL)
  Содержит коллекцию элементов [Role](../../../analysis-services/scripting/objects/role-element-assl.md) , определенных в родительском элементе.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database> <!-- or Server -->  
   ...  
   <Roles>  
      <Role>...</Role>  
   </Roles>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Database](../../../analysis-services/scripting/objects/database-element-assl.md), [Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Дочерние элементы|[Роль](../../../analysis-services/scripting/objects/role-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Элемент **Roles** , связанный с элементом **Server** , содержит только одну роль Administrators, которая представляет роль администратора сервера. Роль администратора сервера не может быть изменена или удалена, кроме того, к этой коллекции не могут быть добавлены дополнительные роли.  
  
 Элемент **Roles** , связанный с элементом **Database** , содержит роли, определенные для этой базы данных.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.RoleCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

