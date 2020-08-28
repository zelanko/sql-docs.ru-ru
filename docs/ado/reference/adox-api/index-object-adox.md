---
description: Объект Index (ADOX)
title: Объект index (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 58b9e80dc57ddfdbd95bcb9523e428031fcebff0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984295"
---
# <a name="index-object-adox"></a>Объект Index (ADOX)
Представляет индекс из таблицы базы данных.  
  
## <a name="remarks"></a>Remarks  
 Следующий код создает новый **индекс**:  
  
```  
Dim obj As New Index  
```  
  
 С помощью свойств и коллекций объекта **index** можно:  
  
-   Найдите индекс с помощью свойства [Name](./name-property-adox.md) .  
  
-   Доступ к столбцам базы данных индекса с помощью коллекции [Columns](./columns-collection-adox.md) .  
  
-   Укажите, должны ли ключи индекса быть уникальными с [уникальным](./unique-property-adox.md) свойством.  
  
-   Укажите, является ли индекс первичным ключом для таблицы со свойством [PrimaryKey](./primarykey-property-adox.md) .  
  
-   Укажите, будут ли записи, имеющие значения NULL в полях индекса, содержать элементы индекса со свойством [IndexNulls](./indexnulls-property-adox.md) .  
  
-   Укажите, кластеризован ли индекс с помощью свойства [Clustered](./clustered-property-adox.md) .  
  
-   Доступ к свойствам индекса для конкретного поставщика с помощью коллекции [свойств](../ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  При добавлении [столбца](./column-object-adox.md) в коллекцию **Columns** **индекса** , если **Столбец** не существует в объекте [таблицы](./table-object-adox.md) , уже добавленном в коллекцию [таблиц](./tables-collection-adox.md) , возникнет ошибка.  
  
> [!NOTE]
>  Поставщик данных может не поддерживать все свойства объектов **индекса** . Если задано значение для свойства, которое не поддерживается поставщиком, возникнет ошибка. Для новых объектов **индекса** ошибка возникает при добавлении объекта в коллекцию. Для существующих объектов при задании свойства возникнет ошибка.  
  
> [!NOTE]
>  При создании объектов **индекса** наличие соответствующего значения по умолчанию для необязательного свойства не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах, поддерживаемых поставщиком, см. в документации поставщика.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Index](./index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Append для индексов (Visual Basic)](./indexes-append-method-example-vb.md)   
 [Пример свойства IndexNulls (Visual Basic)](./indexnulls-property-example-vb.md)   
 [Пример PrimaryKey и уникальных свойств (Visual Basic)](./primarykey-and-unique-properties-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](./sortorder-property-example-vb.md)   
 [Коллекция Columns (ADOX)](./columns-collection-adox.md)   
 [Коллекция indexes (ADOX)](./indexes-collection-adox.md)   
 [Коллекция Properties (ADO)](../ado-api/properties-collection-ado.md)