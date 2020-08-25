---
description: Метод GetPermissions (ADOX)
title: Метод PermissionSet (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _User25::GetPermissions
- _Group25::raw_GetPermissions
- _Group25::GetPermissions
- _User25::raw_GetPermissions
helpviewer_keywords:
- GetPermissions method [ADOX]
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
author: rothja
ms.author: jroth
ms.openlocfilehash: d9533ca5260a8e5dc900a28d883f66994d7a9669
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770463"
---
# <a name="getpermissions-method-adox"></a>Метод GetPermissions (ADOX)
Возвращает разрешения для [группы](./group-object-adox.md) или [пользователя](./user-object-adox.md) в контейнере объекта или объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** , указывающее битовую маску, содержащую разрешения, которые группа или пользователь имеет на объекте. Это значение может быть одной или несколькими константами [ригхтсенум](./rightsenum.md) .  
  
#### <a name="parameters"></a>Параметры  
 *Имя*  
 Значение **типа Variant** , указывающее имя объекта, для которого задаются разрешения. Задайте для *Name* значение null, если требуется получить разрешения для контейнера объектов.  
  
 *ObjectType*  
 Значение типа **Long** , которое может быть одной из констант [обжекттипинум](./objecttypeenum.md) , указывающее тип объекта, для которого нужно получить разрешения.  
  
 *обжекттипеид*  
 Необязательный элемент. Значение **типа Variant** , указывающее идентификатор GUID для типа объекта поставщика, не определенного спецификацией OLE DB. Этот параметр является обязательным, если для *ObjectType* задано значение **адпермобжпровидерспеЦифик**. в противном случае он не используется.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Group (ADOX)](./group-object-adox.md)  
    :::column-end:::
    :::column:::
        [Объект User (ADOX)](./user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Примеры методов SetPermissions и Methods (Visual Basic)](./getpermissions-and-setpermissions-methods-example-vb.md)   
 [Свойство Name (ADOX)](./name-property-adox.md)   
 [Метод SetPermissions (ADOX)](./setpermissions-method-adox.md)