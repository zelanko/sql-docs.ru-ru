---
title: Append-метод (коллекция Users ADOX) | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967229"
---
# <a name="append-method-adox-users"></a>Метод Append (коллекция Users ADOX)
Добавляет новый [пользователя](../../../ado/reference/adox-api/user-object-adox.md) объект [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Пользователь*  
 Объект **Variant** значение, содержащее **пользователя** добавляемый объект или имя пользователя для создания и добавления.  
  
 *Пароль*  
 Необязательный параметр. Объект **строка** значение, содержащее пароль для пользователя. *Пароль* параметр соответствует параметру значение, заданное параметром [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) метод **пользователя** объекта.  
  
## <a name="remarks"></a>Примечания  
 **Пользователей** коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет пользователей каталога. **Пользователей** коллекции для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только пользователи, имеющие членства в определенной группе.  
  
 Если поставщик не поддерживает создание пользователей, произойдет ошибка.  
  
> [!NOTE]
>  Перед добавлением **пользователя** объект **пользователей** коллекцию **группы** объекта, **пользователя** с тем же [имя ](../../../ado/reference/adox-api/name-property-adox.md) как один, который будет добавляться уже должен существовать в **пользователей** коллекцию **каталога**.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Группы и пользователи Append, пример метода ChangePassword (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append-метод (коллекция Columns ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (коллекция Groups ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (коллекция Indexes ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (коллекция Keys ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (коллекция Procedures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (коллекция Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
