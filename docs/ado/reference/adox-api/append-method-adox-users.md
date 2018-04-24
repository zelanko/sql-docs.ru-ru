---
title: Append-метод (ADOX пользователей) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Users::raw_Append
- Users::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b80bc5d5-78ca-4f75-956b-2ac658029cc7
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 267dbd8bc1eb05a1d0f56c9078c5f5518d1e38d7
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="append-method-adox-users"></a>Append-метод (ADOX пользователей)
Добавляет новый [пользователя](../../../ado/reference/adox-api/user-object-adox.md) объект [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Пользователь*  
 Объект **Variant** значение, содержащее **пользователя** добавляемый объект или имя пользователя для создания и добавления.  
  
 *Пароль*  
 Необязательно. Объект **строка** значение, содержащее пароль для пользователя. *Пароль* параметр соответствует параметру значение, заданное параметром [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) метод **пользователя** объекта.  
  
## <a name="remarks"></a>Замечания  
 **Пользователей** коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет каталог пользователей. **Пользователей** коллекции для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только пользователи, имеющие членства в определенной группе.  
  
 Если поставщик не поддерживает создание пользователей, произойдет ошибка.  
  
> [!NOTE]
>  Перед добавлением **пользователя** объект **пользователей** коллекцию **группы** объекта, **пользователя** с тем же [имя ](../../../ado/reference/adox-api/name-property-adox.md) как один, который будет добавляться уже должен существовать в **пользователей** коллекцию **каталога**.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Группы и пользователи присоединения, пример ChangePassword методы (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX группы)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (ADOX индексы)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (ADOX ключи)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (ADOX процедур)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (ADOX таблицы)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
