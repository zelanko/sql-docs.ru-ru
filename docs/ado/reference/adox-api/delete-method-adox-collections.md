---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: be2aa91cf27d7dc12d3cd0c1e0bf719bd43797ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67966431"
---
# <a name="delete-method-adox-collections"></a>Метод Delete (коллекции ADOX)
Удаляет объект из коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Параметры  
 *Название*  
 **Значение типа Variant** , указывающее имя или порядковый номер объекта, который нужно удалить.  
  
## <a name="remarks"></a>Remarks  
 Если *имя* не существует в коллекции, возникнет ошибка.  
  
 Для коллекций [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) и [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) возникнет ошибка, если поставщик не поддерживает удаление таблиц или пользователей соответственно. Для [процедур](../../../ado/reference/adox-api/procedures-collection-adox.md) и коллекций [представлений](../../../ado/reference/adox-api/views-collection-adox.md) команда **Delete** завершится ошибкой, если поставщик не поддерживает сохранение команд.  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Коллекция Indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>См. также:  
 [Пример метода Delete процедур (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Пример метода Delete коллекции Views (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
