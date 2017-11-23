---
title: "Append-метод (ADOX группы) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Groups::raw_Append
- Groups::Append
helpviewer_keywords: Append method [ADOX]
ms.assetid: 56b94fc6-7ef0-4e4a-82a3-033b94c46036
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b88abda8492902df0c050cad085e758bf6562fca
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="append-method-adox-groups"></a>Append-метод (ADOX группы)
Добавляет новый [группы](../../../ado/reference/adox-api/group-object-adox.md) объект [группы](../../../ado/reference/adox-api/groups-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>Параметры  
 *Группирование*  
 **Группы** добавляемый объект или имя группы для создания и добавления.  
  
## <a name="remarks"></a>Замечания  
 **Группы** коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет все учетные записи групп в каталоге. **Группы** коллекции для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет группу, к которой принадлежит пользователь.  
  
 Если поставщик не поддерживает создание групп, произойдет ошибка.  
  
> [!NOTE]
>  Перед добавлением **группы** объект **группы** коллекцию **пользователя** объекта, **группы** с тем же [ Имя](../../../ado/reference/adox-api/name-property-adox.md) как один, который будет добавляться уже должен существовать в **группы** коллекцию **каталога**.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Группы и пользователи присоединения, пример ChangePassword методы (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX индексы)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (ADOX ключи)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (ADOX процедур)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (ADOX таблицы)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (ADOX пользователей)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
