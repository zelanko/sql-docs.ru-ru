---
description: Метод Append (коллекция Users ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 35583e55a15fcbf781bc156b9c9fe1f226279d51
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771343"
---
# <a name="append-method-adox-users"></a>Метод Append (коллекция Users ADOX)
Добавляет новый объект [User](./user-object-adox.md) в коллекцию [пользователей](./users-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Параметры  
 *Пользователь*  
 Значение **типа Variant** , содержащее добавляемый объект- **пользователь** или имя пользователя для создания и добавления.  
  
 *Пароль*  
 Необязательный элемент. **Строковое** значение, содержащее пароль для пользователя. Параметр *Password* соответствует значению, заданному методом [ChangePassword](./changepassword-method-adox.md) объекта **пользователя** .  
  
## <a name="remarks"></a>Remarks  
 Коллекция **пользователей** [каталога](./catalog-object-adox.md) представляет всех пользователей каталога. Коллекция **пользователей** для [группы](./group-object-adox.md) представляет только тех пользователей, которые имеют членство в определенной группе.  
  
 Если поставщик не поддерживает создание пользователей, возникнет ошибка.  
  
> [!NOTE]
>  Перед добавлением объекта **пользователя** в коллекцию **Users** объекта **Group** объект **пользователя** с тем же [именем](./name-property-adox.md) , что и у добавляемого, должен уже существовать в коллекции **пользователей** **каталога**.  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Users (ADOX)](./users-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример добавления групп и пользователей, методы ChangePassword (Visual Basic)](./groups-and-users-append-changepassword-methods-example-vb.md)   
 [Метод Append (столбцы ADOX)](./append-method-adox-columns.md)   
 [Метод Append (группы ADOX)](./append-method-adox-groups.md)   
 [Метод Append (индексы ADOX)](./append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](./append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](./append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](./append-method-adox-tables.md)   
 [Метод Append (коллекция Views ADOX)](./append-method-adox-views.md)