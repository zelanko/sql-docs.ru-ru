---
title: Таблицы (ADOX) сбора | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog::Tables
- Tables
helpviewer_keywords:
- Tables collection [ADOX]
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b9ae2422e9d0d3a776bf786f77be5c8c5025d21
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281502"
---
# <a name="tables-collection-adox"></a>Коллекция Tables (ADOX)
Содержит все [таблицы](../../../ado/reference/adox-api/table-object-adox.md) объектов каталога.  
  
## <a name="remarks"></a>Примечания  
 [Append](../../../ado/reference/adox-api/append-method-adox-tables.md) метод **таблиц** является уникальным для ADOX. Можно выполнить следующие действия:   
  
-   Добавить новую таблицу в коллекцию с **Append** метод.  
  
 Остальные свойства и методы являются стандартными для коллекции ADO. Можно выполнить следующие действия:   
  
-   Доступ к таблице в коллекции с [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Возвращает количество таблиц, содержащихся в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Удалить таблицу из коллекции с [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод.  
  
-   Обновление объектов в коллекции в соответствии с текущей схемы базы данных с помощью [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
 Некоторые поставщики могут возвращать другие объекты схемы, например представления, в **таблиц** коллекции. Таким образом некоторые коллекции ADOX может содержать несколько ссылок на тот же объект. Следует ли удалить объект из одной коллекции, изменения не будут отображаться в другой коллекции, который ссылается на удаленный объект до **обновить** метод вызывается для коллекции. Например, с помощью поставщика OLE DB для Jet (Майкрософт), представления с возвращаются **таблиц** коллекции. При удалении представления, необходимо обновить **таблиц** коллекции, прежде чем изменения будут отражены коллекции.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события коллекции Tables](../../../ado/reference/adox-api/tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ActiveConnection объекта Catalog (Visual Basic)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Столбцов и таблиц методов append для коллекций, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Подключение примеры метода Close, таблица тип свойства (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Append коллекции Keys метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)
