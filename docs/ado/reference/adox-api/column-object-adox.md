---
title: Объект Column (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Column
helpviewer_keywords:
- Column object [ADOX]
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7dcec7e665fec8ea1eb1e1dff8d08bb59ee92133
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66708024"
---
# <a name="column-object-adox"></a>Объект Column (ADOX)
Представляет столбец из таблицы, индекса или ключа.  
  
## <a name="remarks"></a>Примечания  
 В следующем коде создается новый **столбец**:  
  
 `Dim obj As New Column`  
  
 С помощью свойств и коллекций **столбец** объекта, вы можете:  
  
-   Определение столбца с [свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Укажите тип данных столбца с [свойство Type (ключ) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md) свойство.  
  
-   Определить, если столбец является фиксированной длины или он может содержать значения null с [атрибуты свойства (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) свойство.  
  
-   Укажите максимальный размер столбца с [свойство DefinedSize (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) свойство.  
  
-   Для числовых значений данных, укажите масштаб с [свойство NumericScale (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) свойство.  
  
-   Для значения числовых данных, укажите максимальную точность с [свойство Precision (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) свойство.  
  
-   Укажите [объекта Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) , которому принадлежит столбец с [свойство ParentCatalog (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) свойство.  
  
-   Для ключевых столбцов, укажите имя связанного столбца в связанной таблице с [свойство RelatedColumn (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) свойство.  
  
-   Для индексных столбцов, указывать ли порядок сортировки по возрастанию или по убыванию с [свойство SortOrder (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) свойство.  
  
-   Доступ к свойствам поставщика с [свойства коллекции (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
> [!NOTE]
>  Не все свойства **столбец** объекты, которые могут поддерживаться поставщиком данных. Если вы задали значение для свойства, которое поставщик не поддерживает, произойдет ошибка. Для новых **столбец** объектов, ошибка возникает в том случае, когда объект добавляется в коллекцию. Для существующих объектов ошибка возникает при задании свойства.  
>   
>  При создании **столбец** объекты, существование соответствующего значения по умолчанию необязательное свойство не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах используемый поставщик поддерживает см. в документации поставщика.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Column](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Столбцов и таблиц методов append для коллекций, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Подключение примеры метода Close, таблица тип свойства (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Append коллекции Keys метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример кода ADOX: Свойств NumericScale и Precision (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
