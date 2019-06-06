---
title: Индекс объекта (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Index
helpviewer_keywords:
- Index object [ADOX]
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b6fd63de0b6147b86aa0d6b548669c56aefdcf20
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66706715"
---
# <a name="index-object-adox"></a>Объект Index (ADOX)
Представляет индекс из таблицы базы данных.  
  
## <a name="remarks"></a>Примечания  
 В следующем коде создается новый **индекс**:  
  
```  
Dim obj As New Index  
```  
  
 С помощью свойств и коллекций **индекс** объекта, вы можете:  
  
-   Определение индекса с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Доступ к базе данных столбцы индекса с помощью [столбцы](../../../ado/reference/adox-api/columns-collection-adox.md) коллекции.  
  
-   Укажите, должны ли быть уникальными в ключи индекса [Unique](../../../ado/reference/adox-api/unique-property-adox.md) свойство.  
  
-   Укажите, является ли индекс первичным ключом для таблицы с [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) свойство.  
  
-   Укажите, имеют ли записи со значениями null в полях индекс записи индекса с [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) свойство.  
  
-   Укажите, является ли индекс кластеризованным с [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md) свойство.  
  
-   Доступ к свойствам индекса поставщика с [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
> [!NOTE]
>  Произойдет ошибка при добавлении [столбец](../../../ado/reference/adox-api/column-object-adox.md) для **столбцы** коллекцию **индекс** Если **столбца** не существует в [Таблицы](../../../ado/reference/adox-api/table-object-adox.md) объекта, уже добавлен к [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) коллекции.  
  
> [!NOTE]
>  Поставщик данных может не поддерживать все свойства **индекс** объектов. Если вы задали значение для свойства, которое не поддерживается поставщиком, произойдет ошибка. Для новых **индекс** объектов, ошибка возникает в том случае, когда объект добавляется в коллекцию. Для существующих объектов ошибка возникает при задании свойства.  
  
> [!NOTE]
>  При создании **индекс** объекты, существование соответствующего значения по умолчанию необязательное свойство не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах используемый поставщик поддерживает см. в документации поставщика.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Index](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода (Visual Basic) Append](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Пример свойства IndexNulls (Visual Basic)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [PrimaryKey и уникальные свойства (Visual Basic)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
