---
title: "Индекс объекта (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Index
helpviewer_keywords:
- Index object [ADOX]
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb35b814dbd06136c9ce0a47a82e5956e98b6945
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="index-object-adox"></a>Объект индекса (ADOX)
Представляет индекс из таблицы базы данных.  
  
## <a name="remarks"></a>Remarks  
 Следующий код создает новый **индекс**:  
  
```  
Dim obj As New Index  
```  
  
 С помощью свойств и коллекций **индекс** объекта, вы можете:  
  
-   Определить индекс с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойства.  
  
-   Доступ к базе данных столбцам индекса с [столбцы](../../../ado/reference/adox-api/columns-collection-adox.md) коллекции.  
  
-   Укажите, должны ли быть уникальными с ключей индекса [Unique](../../../ado/reference/adox-api/unique-property-adox.md) свойство.  
  
-   Укажите, является ли индекс первичным ключом для таблицы с [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) свойство.  
  
-   Укажите, имеют ли записи, имеющие значения null в полях индекс записи индекса с [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) свойство.  
  
-   Укажите, является ли индекс кластеризованным с [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md) свойство.  
  
-   Доступ к свойствам индекса поставщика с [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
> [!NOTE]
>  Произойдет ошибка при наращивании [столбца](../../../ado/reference/adox-api/column-object-adox.md) для **столбцы** коллекцию **индекс** Если **столбца** не существует в [Таблицы](../../../ado/reference/adox-api/table-object-adox.md) объекта, уже добавлены [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) коллекции.  
  
> [!NOTE]
>  Поставщик данных может поддерживать не все свойства **индекс** объектов. Если вы задали значение для свойства, которое не поддерживается поставщиком, произойдет ошибка. Для новых **индекс** объектов, ошибка возникает, когда объект добавляется в коллекцию. Для существующих объектов ошибка возникает, когда для свойства.  
  
> [!NOTE]
>  При создании **индекс** объектов наличия соответствующего значения по умолчанию это необязательное свойство не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах поставщик поддерживает поставщик документации.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Index](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Индексы Append пример метода (Visual Basic)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Пример свойства IndexNulls (Visual Basic)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [PrimaryKey и пример уникальные свойства (Visual Basic)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Коллекция столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция индексов (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
