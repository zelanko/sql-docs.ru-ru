---
title: "Метод SetPermissions (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7987ce08f242421d2c84766c575e4867e7e1b8c8
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="setpermissions-method-adox"></a>Метод SetPermissions (ADOX)
Задает разрешения для [группы](../../../ado/reference/adox-api/group-object-adox.md) или [пользователя](../../../ado/reference/adox-api/user-object-adox.md) на объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Название*  
 Объект **строка** значение, указывающее имя объекта, для которого требуется задать разрешения.  
  
 *ObjectType*  
 Объект **длинные** значение может быть одним из [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) константы, которое указывает тип объекта, для которого необходимо получить разрешения.  
  
 *Действие*  
 Объект **длинные** значение может быть одним из [ActionEnum](../../../ado/reference/adox-api/actionenum.md) константы, которое указывает тип действия для выполнения при установке разрешений.  
  
 *Права*  
 Объект **длинные** значение, которое может быть битовой маской из одного или нескольких [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) констант, которые указывает права на установку.  
  
 *Inherit*  
 Необязательно. Объект **длинные** значение может быть одним из [InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md) констант, которые указывает, каким образом объекты наследуют эти разрешения. Значение по умолчанию — **adInheritNone**.  
  
 *ObjectTypeId*  
 Необязательно. Объект **Variant** значение, которое указывает идентификатор GUID для типа объекта поставщика, не определенных в спецификации OLE DB. Этот параметр является обязательным, если *ObjectType* равно **adPermObjProviderSpecific**; в противном случае он не используется.  
  
## <a name="remarks"></a>Remarks  
 Если поставщик не поддерживает назначении прав доступа для групп пользователей, произойдет ошибка.  
  
> [!NOTE]
>  При вызове **SetPermissions**, задавать действия **adAccessRevoke** переопределяет любые параметры *права* параметра. Не устанавливайте *действия* для **adAccessRevoke** Если права, указанные в *права* параметра вступили в силу.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>См. также  
 [GetPermissions и пример SetPermissions методы (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Метод GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
