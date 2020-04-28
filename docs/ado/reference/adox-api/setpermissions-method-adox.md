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
ms.openlocfilehash: 50a609d0cebe70ea5127ed448e57a70881e35097
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965227"
---
# <a name="setpermissions-method-adox"></a>Метод SetPermissions (ADOX)
Задает разрешения для [группы](../../../ado/reference/adox-api/group-object-adox.md) или [пользователя](../../../ado/reference/adox-api/user-object-adox.md) на объекте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Параметры  
 *имя*;  
 **Строковое** значение, указывающее имя объекта, для которого задаются разрешения.  
  
 *ObjectType*  
 Значение типа **Long** , которое может быть одной из констант [обжекттипинум](../../../ado/reference/adox-api/objecttypeenum.md) , указывающее тип объекта, для которого нужно получить разрешения.  
  
 *Действие*  
 Значение типа **Long** , которое может быть одной из констант [актионенум](../../../ado/reference/adox-api/actionenum.md) , которое указывает тип действия, выполняемого при установке разрешений.  
  
 *Права*  
 **Длинное** значение, которое может быть битовой маской одной или нескольких констант [ригхтсенум](../../../ado/reference/adox-api/rightsenum.md) , указывающих права на установку.  
  
 *Следующих*  
 Необязательный параметр. Значение **типа Long** , которое может быть одной из констант [инхериттипинум](../../../ado/reference/adox-api/inherittypeenum.md) , которое указывает, как объекты будут наследовать эти разрешения. Значение по умолчанию — **адинхеритноне**.  
  
 *обжекттипеид*  
 Необязательный параметр. Значение **типа Variant** , указывающее идентификатор GUID для типа объекта поставщика, который не определен спецификацией OLE DB. Этот параметр является обязательным, если для *ObjectType* задано значение **адпермобжпровидерспеЦифик**. в противном случае он не используется.  
  
## <a name="remarks"></a>Remarks  
 Если поставщик не поддерживает установку прав доступа для групп или пользователей, возникнет ошибка.  
  
> [!NOTE]
>  При вызове **SetPermissions**Установка действий в **адакцессревоке** переопределяет все параметры параметра *Rights* . Не устанавливайте *действия* в **адакцессревоке** , если вы хотите, чтобы права, указанные в параметре *Rights* , вступили в силу.  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов SetPermissions и Methods (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Метод PermissionSet (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
