---
title: Таблицы объект (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table
helpviewer_keywords:
- Table object [ADOX]
ms.assetid: a6d74000-0828-49ba-850a-63da865f8802
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5af59dbc50f6e1a2cd95cbdf99874d860eceeb1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281595"
---
# <a name="table-object-adox"></a>Объект Table (ADOX)
Представляет таблицу базы данных, включая столбцы, индексы и ключи.  
  
## <a name="remarks"></a>Примечания  
 В следующем коде создается новый **таблицы**:  
  
```  
Dim obj As New Table  
```  
  
 С помощью свойств и коллекций **таблицы** объекта, вы можете:  
  
-   Определите таблицу с [свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Определите тип таблицы с [свойство Type (Table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md) свойство.  
  
-   Доступ к базе данных столбцы таблицы с [коллекции столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md) коллекции.  
  
-   Доступ к индексы таблицы с [коллекции индексов (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md).  
  
-   Доступ к ключам таблицы с [ключи коллекции (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md).  
  
-   Укажите каталог, к которой принадлежит таблица с [свойство ParentCatalog (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) свойство.  
  
-   Возвращает сведения о дате с [свойство DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md) и [свойство DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md) свойства.  
  
-   Доступ к свойствам поставщика таблицы с [свойства коллекции (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
> [!NOTE]
>  Поставщик данных может не поддерживать все свойства **таблицы** объектов. Если вы задали значение для свойства, которое поставщик не поддерживает, произойдет ошибка. Для новых **таблицы** объектов, ошибка возникает в том случае, когда объект добавляется в коллекцию. Для существующих объектов ошибка возникает при задании свойства.  
>   
>  При создании **таблицы** объекты, существование соответствующего значения по умолчанию необязательное свойство не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах используемый поставщик поддерживает см. в документации поставщика.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Table](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ActiveConnection объекта Catalog (Visual Basic)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Столбцов и таблиц методов append для коллекций, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Подключение примеры метода Close, таблица тип свойства (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Append коллекции Keys метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
