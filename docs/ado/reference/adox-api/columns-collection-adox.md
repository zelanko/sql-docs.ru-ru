---
title: Коллекция Columns (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index::Columns
- Table::Columns
- Key::Columns
- Columns
helpviewer_keywords:
- Columns collection [ADOX]
ms.assetid: 23b9fea8-4f76-4a51-95ce-1a6ce4560b34
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4bdb60a6d174ab82df7529b6e26d8d5b2c031107
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703960"
---
# <a name="columns-collection-adox"></a>Коллекция Columns (ADOX)
Содержит все [столбец](../../../ado/reference/adox-api/column-object-adox.md) объекты, таблицы, индекса или ключа.  
  
## <a name="remarks"></a>Примечания  
 [Append](../../../ado/reference/adox-api/append-method-adox-columns.md) метод **столбцы** является уникальным для ADOX. Можно выполнить следующие действия:  
  
-   Добавить новый столбец в коллекцию с **Append** метод.  
  
 Остальные свойства и методы являются стандартными для коллекции ADO. Можно выполнить следующие действия:  
  
-   Доступ к столбцу в коллекции с [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Возвращает количество столбцов, содержащихся в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Удаление столбца из коллекции с [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод.  
  
-   Обновление объектов в коллекции в соответствии с текущей базы данных схемы с [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
> [!NOTE]
>  Произойдет ошибка при добавлении **столбец** для **столбцы** коллекцию [индекс](../../../ado/reference/adox-api/index-object-adox.md) Если **столбца** не существует в [Таблицы](../../../ado/reference/adox-api/table-object-adox.md) , добавляется к уже [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) коллекции.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события коллекции Columns](../../../ado/reference/adox-api/columns-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Столбцов и таблиц методов append для коллекций, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Подключение примеры метода Close, таблица тип свойства (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Append коллекции Keys метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
