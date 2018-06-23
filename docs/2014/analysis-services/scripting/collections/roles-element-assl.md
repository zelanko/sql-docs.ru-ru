---
title: Элемент Roles (ASSL) | Документы Microsoft
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
- Roles Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Roles
helpviewer_keywords:
- Roles element
ms.assetid: 4191b7ce-bae4-4200-8550-3904420efafd
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f8ced51e40e2804054a0c63368622d2df70f81fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190627"
---
# <a name="roles-element-assl"></a>Элемент Roles (ASSL)
  Содержит коллекцию элементов [Role](../objects/role-element-assl.md) , определенных в родительском элементе.  
  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Database](../objects/database-element-assl.md), [Server](../objects/server-element-assl.md)|  
|Дочерние элементы|[Роль](../objects/role-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Roles`, связанный с элементом `Server`, содержит только одну роль Administrators, которая представляет роль администратора сервера. Роль администратора сервера не может быть изменена или удалена, кроме того, к этой коллекции не могут быть добавлены дополнительные роли.  
  
 Элемент `Roles`, связанный с элементом `Database`, содержит роли, определенные для этой базы данных.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.RoleCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  