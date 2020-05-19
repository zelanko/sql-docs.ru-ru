---
title: Объект index (ADOX) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 840484cbfcb1feeb56022835b6c1b3157101edb8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763885"
---
# <a name="index-object-adox"></a>Объект Index (ADOX)
Представляет индекс из таблицы базы данных.  
  
## <a name="remarks"></a>Примечания  
 Следующий код создает новый **индекс**:  
  
```  
Dim obj As New Index  
```  
  
 С помощью свойств и коллекций объекта **index** можно:  
  
-   Найдите индекс с помощью свойства [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Доступ к столбцам базы данных индекса с помощью коллекции [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
-   Укажите, должны ли ключи индекса быть уникальными с [уникальным](../../../ado/reference/adox-api/unique-property-adox.md) свойством.  
  
-   Укажите, является ли индекс первичным ключом для таблицы со свойством [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) .  
  
-   Укажите, будут ли записи, имеющие значения NULL в полях индекса, содержать элементы индекса со свойством [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) .  
  
-   Укажите, кластеризован ли индекс с помощью свойства [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md) .  
  
-   Доступ к свойствам индекса для конкретного поставщика с помощью коллекции [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  При добавлении [столбца](../../../ado/reference/adox-api/column-object-adox.md) в коллекцию **Columns** **индекса** , если **Столбец** не существует в объекте [таблицы](../../../ado/reference/adox-api/table-object-adox.md) , уже добавленном в коллекцию [таблиц](../../../ado/reference/adox-api/tables-collection-adox.md) , возникнет ошибка.  
  
> [!NOTE]
>  Поставщик данных может не поддерживать все свойства объектов **индекса** . Если задано значение для свойства, которое не поддерживается поставщиком, возникнет ошибка. Для новых объектов **индекса** ошибка возникает при добавлении объекта в коллекцию. Для существующих объектов при задании свойства возникнет ошибка.  
  
> [!NOTE]
>  При создании объектов **индекса** наличие соответствующего значения по умолчанию для необязательного свойства не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах, поддерживаемых поставщиком, см. в документации поставщика.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Index](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Append для индексов (Visual Basic)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [Пример свойства IndexNulls (Visual Basic)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [Пример PrimaryKey и уникальных свойств (Visual Basic)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
