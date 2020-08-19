---
description: Метод Append (коллекция Groups ADOX)
title: Метод Append (группы ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups::raw_Append
- Groups::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 56b94fc6-7ef0-4e4a-82a3-033b94c46036
author: rothja
ms.author: jroth
ms.openlocfilehash: 2dc46d1c0d44ec175b442df943ce72a38ec2b761
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440496"
---
# <a name="append-method-adox-groups"></a>Метод Append (коллекция Groups ADOX)
Добавляет новый объект [группы](../../../ado/reference/adox-api/group-object-adox.md) в коллекцию [Groups](../../../ado/reference/adox-api/groups-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>Параметры  
 *Группа*  
 Добавляемый объект **группы** или имя группы для создания и добавления.  
  
## <a name="remarks"></a>Remarks  
 Коллекция **Groups** [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет все учетные записи групп каталога. Коллекция **Groups** для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет только группу, к которой принадлежит пользователь.  
  
 Если поставщик не поддерживает создание групп, возникнет ошибка.  
  
> [!NOTE]
>  Перед добавлением объекта **группы** в коллекцию **Groups** объекта **пользователя** объект **группы** с тем же [именем](../../../ado/reference/adox-api/name-property-adox.md) , что и один из добавляемых, должен уже существовать в коллекции **Groups** **каталога**.  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример добавления групп и пользователей, методы ChangePassword (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Метод Append (столбцы ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Метод Append (индексы ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
