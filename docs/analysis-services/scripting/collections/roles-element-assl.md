---
title: Элемент Roles (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d246999149c2b23868522fe5d4beb50526993287
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="roles-element-assl"></a>Элемент Roles (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
 Элемент **Roles** , связанный с элементом **Server** , содержит только одну роль Administrators, которая представляет роль администратора сервера. Роль администратора сервера не может быть изменена или удалена, кроме того, к этой коллекции не могут быть добавлены дополнительные роли.  
  
 Элемент **Roles** , связанный с элементом **Database** , содержит роли, определенные для этой базы данных.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.RoleCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
