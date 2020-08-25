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
ms.openlocfilehash: 14900e34ef93f2ad738779b0cf7478372ab59179
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88771483"
---
# <a name="append-method-adox-groups"></a>Метод Append (коллекция Groups ADOX)
Добавляет новый объект [группы](./group-object-adox.md) в коллекцию [Groups](./groups-collection-adox.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Groups.Append Group  
```  
  
#### <a name="parameters"></a>Параметры  
 *Группа*  
 Добавляемый объект **группы** или имя группы для создания и добавления.  
  
## <a name="remarks"></a>Remarks  
 Коллекция **Groups** [каталога](./catalog-object-adox.md) представляет все учетные записи групп каталога. Коллекция **Groups** для [пользователя](./user-object-adox.md) представляет только группу, к которой принадлежит пользователь.  
  
 Если поставщик не поддерживает создание групп, возникнет ошибка.  
  
> [!NOTE]
>  Перед добавлением объекта **группы** в коллекцию **Groups** объекта **пользователя** объект **группы** с тем же [именем](./name-property-adox.md) , что и один из добавляемых, должен уже существовать в коллекции **Groups** **каталога**.  
  
## <a name="applies-to"></a>Применение  
 [Коллекция Groups (ADOX)](./groups-collection-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример добавления групп и пользователей, методы ChangePassword (Visual Basic)](./groups-and-users-append-changepassword-methods-example-vb.md)   
 [Метод Append (столбцы ADOX)](./append-method-adox-columns.md)   
 [Метод Append (индексы ADOX)](./append-method-adox-indexes.md)   
 [Метод Append (ключи ADOX)](./append-method-adox-keys.md)   
 [Метод Append (процедуры ADOX)](./append-method-adox-procedures.md)   
 [Метод Append (таблицы ADOX)](./append-method-adox-tables.md)   
 [Метод Append (пользователи ADOX)](./append-method-adox-users.md)   
 [Метод Append (коллекция Views ADOX)](./append-method-adox-views.md)