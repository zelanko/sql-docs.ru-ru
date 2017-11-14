---
title: "Таблица объектов (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Table
helpviewer_keywords:
- Table object [ADOX]
ms.assetid: a6d74000-0828-49ba-850a-63da865f8802
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 198b59d624b2daa2e2451b8dbb61ae5868f7eb7d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="table-object-adox"></a>Объект таблицы (ADOX)
Представляет таблицу базы данных, включая столбцы, индексы и ключи.  
  
## <a name="remarks"></a>Замечания  
 Следующий код создает новый **таблицы**:  
  
```  
Dim obj As New Table  
```  
  
 С помощью свойств и коллекций **таблицы** объекта, вы можете:  
  
-   Определить таблицу с [имя свойства (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Определить тип таблицы с [свойство Type (таблица) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md) свойство.  
  
-   Доступ к базе данных столбцы таблицы с [коллекции столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md) коллекции.  
  
-   Доступ к индексы таблицы с [коллекции индексов (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md).  
  
-   Доступ к ключам таблицы с [ключи коллекции (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md).  
  
-   Укажите каталог, которому принадлежит таблица с [ParentCatalog свойство (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) свойство.  
  
-   Возвращает сведения о дате с [свойство DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md) и [свойство DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md) свойства.  
  
-   Доступ к свойствам поставщика таблицы с [свойства коллекции (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
> [!NOTE]
>  Поставщик данных может поддерживать не все свойства **таблицы** объектов. Если вы задали значение для свойства, которое поставщик не поддерживает завершится ошибкой. Для новых **таблицы** объектов, ошибка возникает, когда объект добавляется в коллекцию. Для существующих объектов ошибка возникает, когда для свойства.  
>   
>  При создании **таблицы** объектов наличия соответствующего значения по умолчанию это необязательное свойство не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах поставщик поддерживает поставщик документации.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства объекта таблицы, методы и события](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства ActiveConnection каталога (Visual Basic)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Столбцы и таблицы добавьте методы примера имя свойства (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Подключение метода закрытия, пример свойство типа таблицы (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Коллекция столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция индексов (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Коллекция ключей (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Коллекция таблиц (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)

