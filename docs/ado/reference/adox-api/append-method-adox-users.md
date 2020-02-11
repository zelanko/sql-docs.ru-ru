---
title: Метод Append (пользователи ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Users::raw_Append
- Users::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b80bc5d5-78ca-4f75-956b-2ac658029cc7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 99a21cd5dd32af9e84877865cfe7c0fc92f6c087
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967229"
---
# <a name="append-method-adox-users"></a>Метод Append (коллекция Users ADOX)
Добавляет новый объект [User](../../../ado/reference/adox-api/user-object-adox.md) в коллекцию [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Пользователь*  
 Значение **типа Variant** , содержащее добавляемый объект- **пользователь** или имя пользователя для создания и добавления.  
  
 *Пароль*  
 Необязательный параметр. **Строковое** значение, содержащее пароль для пользователя. Параметр *Password* соответствует значению, заданному методом [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) объекта **пользователя** .  
  
## <a name="remarks"></a>Remarks  
 Коллекция **пользователей** [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет всех пользователей каталога. Коллекция **пользователей** для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только тех пользователей, которые имеют членство в определенной группе.  
  
 Если поставщик не поддерживает создание пользователей, возникнет ошибка.  
  
> [!NOTE]
>  Перед добавлением объекта **пользователя** в коллекцию **Users** объекта **Group** объект **пользователя** с тем же [именем](../../../ado/reference/adox-api/name-property-adox.md) , что и у добавляемого, должен уже существовать в коллекции **пользователей** **каталога**.  
  
## <a name="applies-to"></a>Применяется к  
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример добавления групп и пользователей, методы ChangePassword (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Метод Append (столбцы ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
