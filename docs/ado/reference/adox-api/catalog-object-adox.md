---
title: Объект Catalog (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog
helpviewer_keywords:
- Catalog object [ADOX]
ms.assetid: bb651639-a488-4e38-b6de-0ed99fa4dd92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5547090443e2f22a135234853b76480fb8295e14
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634422"
---
# <a name="catalog-object-adox"></a>Объект Catalog (ADOX)
Содержит коллекции ([таблиц](../../../ado/reference/adox-api/tables-collection-adox.md), [представления](../../../ado/reference/adox-api/views-collection-adox.md), [пользователей](../../../ado/reference/adox-api/users-collection-adox.md), [группы](../../../ado/reference/adox-api/groups-collection-adox.md), и [процедуры](../../../ado/reference/adox-api/procedures-collection-adox.md)), описания каталога схемы источника данных.  
  
## <a name="remarks"></a>Примечания  
 Вы можете изменить **каталога** объекта путем добавления или удаления объектов или путем изменения существующих объектов. Некоторые поставщики могут не поддерживать все **каталога** объектов или может поддерживать только для просмотра сведений о схеме.  
  
 С помощью свойств и методов **каталога** объекта, вы можете:  
  
-   Открыть каталог, задав [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) свойства ADO [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта или допустимую строку соединения.  
  
-   Создать новый каталог с [создать](../../../ado/reference/adox-api/create-method-adox.md) метод.  
  
-   Определить владельцев объектов в **каталога** с [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) и [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) методы.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Catalog](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ActiveConnection объекта Catalog (Visual Basic)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Команды и свойства CommandText (Visual Basic)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Подключение примеры метода Close, таблица тип свойства (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Создайте пример метода (Visual Basic)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Append коллекции Keys метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Примеры коллекции Parameters, команда свойства (Visual Basic)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Процедуры добавления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Процедуры удаления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Процедуры обновления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Представления и коллекции полей (Visual Basic)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Представления метода пример Append (Visual Basic)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Коллекция Views, пример свойства CommandText (Visual Basic)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Delete коллекции Views пример метода (Visual Basic)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Представления метод пример Refresh (Visual Basic)](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
