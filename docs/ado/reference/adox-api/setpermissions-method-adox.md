---
title: Метод SetPermissions (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d3ff679af7a577433a8191d3beca10eed1d22cf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602424"
---
# <a name="setpermissions-method-adox"></a>Метод SetPermissions (ADOX)
Определяет разрешения для [группы](../../../ado/reference/adox-api/group-object-adox.md) или [пользователя](../../../ado/reference/adox-api/user-object-adox.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Название*  
 Объект **строка** значение, указывающее имя объекта, для которого задаются разрешения.  
  
 *ObjectType*  
 Объект **Long** значение, которое может быть одним из [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) константы, которое указывает тип объекта, для которого необходимо получить разрешения.  
  
 *Действие*  
 Объект **Long** значение, которое может быть одним из [ActionEnum](../../../ado/reference/adox-api/actionenum.md) константы, указывающее тип действия для выполнения при установке разрешений.  
  
 *Права*  
 Объект **Long** значение, которое может быть битовой маской, из одного или нескольких из [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) констант, указывающих права на установку.  
  
 *Наследовать*  
 Необязательный параметр. Объект **Long** значение, которое может быть одним из [InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md) констант, определяющих, как объекты наследуют эти разрешения. Значение по умолчанию — **adInheritNone**.  
  
 *ObjectTypeId*  
 Необязательный параметр. Объект **Variant** значение, которое указывает идентификатор GUID для типа объекта поставщика, который не определен в спецификации OLE DB. Этот параметр является обязательным, если *ObjectType* присваивается **adPermObjProviderSpecific**; в противном случае он не используется.  
  
## <a name="remarks"></a>Примечания  
 Если поставщик не поддерживает параметр права доступа для групп или пользователей, произойдет ошибка.  
  
> [!NOTE]
>  При вызове **SetPermissions**, задавать действия **adAccessRevoke** переопределяет любые параметры *права* параметра. Не устанавливайте *действия* для **adAccessRevoke** Если вы хотите, чтобы права, указанные в *права* параметра вступили в силу.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>См. также  
 [GetPermissions и SetPermissions методы (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Метод GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
