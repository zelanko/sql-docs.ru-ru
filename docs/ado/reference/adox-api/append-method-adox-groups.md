---
title: Append-метод (коллекция Groups ADOX) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8281b8b480289dca2b4976cea61a6d6838fa2779
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967317"
---
# <a name="append-method-adox-groups"></a>Метод Append (коллекция Groups ADOX)
Добавляет новый [группы](../../../ado/reference/adox-api/group-object-adox.md) объект [группы](../../../ado/reference/adox-api/groups-collection-adox.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>Параметры  
 *Группирование*  
 **Группы** добавляемый объект или имя группы для создания и добавления.  
  
## <a name="remarks"></a>Примечания  
 **Группы** коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет все учетные записи группы каталога. **Группы** коллекции для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет только группы, к которой принадлежит пользователь.  
  
 Если поставщик не поддерживает создание групп, произойдет ошибка.  
  
> [!NOTE]
>  Перед добавлением **группы** объект **группы** коллекцию **пользователя** объекта, **группы** с тем же [ Имя](../../../ado/reference/adox-api/name-property-adox.md) как один, который будет добавляться уже должен существовать в **группы** коллекцию **каталога**.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Группы и пользователи Append, пример метода ChangePassword (Visual Basic)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)   
 [Append-метод (коллекция Columns ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (коллекция Indexes ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-метод (коллекция Keys ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-метод (коллекция Procedures ADOX)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-метод (коллекция Tables ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-метод (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
