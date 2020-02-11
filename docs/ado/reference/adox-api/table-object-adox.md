---
title: Объект Table (ADOX) | Документация Майкрософт
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
ms.openlocfilehash: 10f3add3cb243d54643c3294104ec2546e7737d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965169"
---
# <a name="table-object-adox"></a>Объект Table (ADOX)
Представляет таблицу базы данных, включая столбцы, индексы и ключи.  
  
## <a name="remarks"></a>Remarks  
 Следующий код создает новую **таблицу**:  
  
```  
Dim obj As New Table  
```  
  
 Свойства и коллекции объекта **Table** позволяют:  
  
-   Найдите таблицу с помощью свойства [Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Определите тип таблицы с помощью свойства [свойства типа (таблица) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md) .  
  
-   Получите доступ к столбцам базы данных таблицы со коллекцией [Columns Collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
-   Получите доступ к индексам таблицы с помощью [коллекции indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md).  
  
-   Получите доступ к ключам таблицы с помощью [коллекции Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md).  
  
-   Укажите каталог, которому принадлежит таблица со свойством [ParentCatalog (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) .  
  
-   Возвращает сведения о дате с помощью свойств [DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md) и свойства [DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md) .  
  
-   Доступ к зависящим от поставщика свойствам таблицы с помощью коллекции [свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  Поставщик данных может не поддерживать все свойства объектов **Table** . Если задано значение для свойства, которое не поддерживается поставщиком, возникнет ошибка. Для новых объектов **таблицы** ошибка возникает при добавлении объекта в коллекцию. Для существующих объектов при задании свойства возникнет ошибка.  
>   
>  При создании объектов **таблицы** существование соответствующего значения по умолчанию для необязательного свойства не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах, поддерживаемых поставщиком, см. в документации поставщика.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Table](../../../ado/reference/adox-api/table-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства ActiveConnection каталога (Visual Basic)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример метода Close соединения, свойство типа таблицы (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
