---
title: Удаление метода (ADOX коллекций) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 8704e69c777c9426af158b9866ca89e70de054b5
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285883"
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
  
## <a name="remarks"></a>Примечания  
 Если произойдет ошибка *имя* не существует в коллекции.  
  
 Для [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) и [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекций, ошибка возникает, если поставщик не поддерживает удаление таблиц или пользователей, соответственно. Для [процедуры](../../../ado/reference/adox-api/procedures-collection-adox.md) и [представления](../../../ado/reference/adox-api/views-collection-adox.md) коллекций, **удалить** завершится ошибкой, если поставщик не поддерживает сохранение команды.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Коллекция Indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>См. также  
 [Процедуры удаления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Пример метода Delete коллекции Views (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
