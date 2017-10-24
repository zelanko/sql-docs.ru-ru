---
title: "Удаление метода (ADOX коллекций) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Views::Delete
- Groups::Delete
- Indexes::raw_Delete
- Columns::raw_Delete
- Tables::Delete
- Keys::Delete
- Users::Delete
- Users::raw_Delete
- Keys::raw_Delete
- Procedures::raw_Delete
- Views::raw_Delete
- Indexes::Delete
- Procedures::Delete
- Groups::raw_Delete
- Tables::raw_Delete
- Columns::Delete
helpviewer_keywords:
- delete method [ADOX]
ms.assetid: e6b6e3a4-8952-4d79-81f4-51019c338374
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 72dd3f6d514b20bb28f9daee6fc16c5c7c346095
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-adox-collections"></a>Удаление метода (ADOX коллекций)
Удаляет объект из коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Параметры  
 *Название*  
 Объект **Variant** , указывающий имя или порядковый номер (индекс) удаляемого объекта.  
  
## <a name="remarks"></a>Замечания  
 Если произойдет ошибка *имя* не существует в коллекции.  
  
 Для [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) и [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекций, ошибка возникает, если поставщик не поддерживает удаление таблиц или пользователей, соответственно. Для [процедуры](../../../ado/reference/adox-api/procedures-collection-adox.md) и [представления](../../../ado/reference/adox-api/views-collection-adox.md) коллекций, **удалить** завершится ошибкой, если поставщик не поддерживает сохранение команды.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Коллекция столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Коллекция групп (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Коллекция индексов (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Коллекция ключей (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Коллекция процедур (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Коллекция таблиц (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Коллекции пользователей (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Коллекции представлений (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>См. также:  
 [Процедуры удаления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Представления удаления пример метода (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)

