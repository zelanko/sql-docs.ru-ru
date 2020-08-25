---
description: Коллекция Columns (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c0e37715077af500e0c5cc023021765a9e4978d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770983"
---
# <a name="columns-collection-adox"></a>Коллекция Columns (ADOX)
Содержит все объекты [Column](./column-object-adox.md) таблицы, индекса или ключа.  
  
## <a name="remarks"></a>Remarks  
 Метод [append](./append-method-adox-columns.md) для коллекции **Columns** уникален для ADOX. Вы можете:  
  
-   Добавьте новый столбец в коллекцию с помощью метода **append** .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Вы можете:  
  
-   Доступ к столбцу в коллекции со свойством [Item](../ado-api/item-property-ado.md) .  
  
-   Возвращает количество столбцов, содержащихся в коллекции, с помощью свойства [Count](../ado-api/count-property-ado.md) .  
  
-   Удалите столбец из коллекции с помощью метода [Delete](./delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить схему текущей базы данных методом [Refresh](../ado-api/refresh-method-ado.md) .  
  
> [!NOTE]
>  При добавлении **столбца** в коллекцию **Columns** [индекса](./index-object-adox.md) , если **Столбец** не существует в [таблице](./table-object-adox.md) , уже присоединенной к коллекции [таблиц](./tables-collection-adox.md) , возникнет ошибка.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Columns](./columns-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример метода Close соединения, свойство типа таблицы (Visual Basic)](./connection-close-method-table-type-property-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](./parentcatalog-property-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](./sortorder-property-example-vb.md)   
 [Объект Column (ADOX)](./column-object-adox.md)