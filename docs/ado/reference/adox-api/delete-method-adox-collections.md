---
description: Метод Delete (коллекции ADOX)
title: Метод Delete (коллекции ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7345337ab35f4154fd9dc53f749e04dba96dad48
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440116"
---
# <a name="delete-method-adox-collections"></a>Метод Delete (коллекции ADOX)
Удаляет объект из коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Параметры  
 *имя*;  
 **Значение типа Variant** , указывающее имя или порядковый номер объекта, который нужно удалить.  
  
## <a name="remarks"></a>Remarks  
 Если *имя* не существует в коллекции, возникнет ошибка.  
  
 Для коллекций [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) и [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) возникнет ошибка, если поставщик не поддерживает удаление таблиц или пользователей соответственно. Для [процедур](../../../ado/reference/adox-api/procedures-collection-adox.md) и коллекций [представлений](../../../ado/reference/adox-api/views-collection-adox.md) команда **Delete** завершится ошибкой, если поставщик не поддерживает сохранение команд.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
        [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
        [Коллекция Indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
        [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
        [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
        [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Пример метода Delete процедур (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Пример метода Delete коллекции Views (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
