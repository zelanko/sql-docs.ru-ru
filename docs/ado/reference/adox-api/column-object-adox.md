---
description: Объект Column (ADOX)
title: Объект Column (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b6cc15e82091da2161a01c1c0a468e86095dd0d6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985105"
---
# <a name="column-object-adox"></a>Объект Column (ADOX)
Представляет столбец из таблицы, индекса или ключа.  
  
## <a name="remarks"></a>Remarks  
 Следующий код создает новый **столбец**:  
  
 `Dim obj As New Column`  
  
 Свойства и коллекции объекта **Column** позволяют:  
  
-   Найдите столбец с помощью свойства [Name (ADOX)](./name-property-adox.md) .  
  
-   Укажите тип данных столбца с помощью свойства [свойства Type (Key) (ADOX)](./type-property-key-adox.md) .  
  
-   Определите, имеет ли столбец фиксированную длину или может ли он содержать значения NULL со свойством [Attributes (ADOX)](./attributes-property-adox.md) .  
  
-   Укажите максимальный размер столбца с помощью свойства [DefinedSize (ADOX)](./definedsize-property-adox.md) .  
  
-   Для числовых значений данных укажите масштаб с помощью свойства [NumericScale (ADOX)](./numericscale-property-adox.md) .  
  
-   Для значения числовых данных укажите максимальную точность с помощью свойства [Precision (ADOX)](./precision-property-adox.md) .  
  
-   Укажите [объект каталога (ADOX)](./catalog-object-adox.md) , которому принадлежит столбец со свойством [ParentCatalog (ADOX)](./parentcatalog-property-adox.md) .  
  
-   Для ключевых столбцов укажите имя связанного столбца в связанной таблице со свойством [RelatedColumn (ADOX)](./relatedcolumn-property-adox.md) .  
  
-   Для столбцов индекса укажите, будет ли порядок сортировки по возрастанию или убыванию со свойством [SortOrder (ADOX)](./sortorder-property-adox.md) .  
  
-   Доступ к свойствам, зависящим от поставщика, с коллекцией [коллекций свойств (ADO)](../ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  Поставщик данных может поддерживать не все свойства объектов **Column** . Если задано значение для свойства, которое не поддерживается поставщиком, возникнет ошибка. Для новых объектов **столбцов** ошибка возникает при добавлении объекта в коллекцию. Для существующих объектов при задании свойства возникнет ошибка.  
>   
>  При создании объектов **столбцов** наличие соответствующего значения по умолчанию для необязательного свойства не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах, поддерживаемых поставщиком, см. в документации поставщика.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Column](./column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример метода Close соединения, свойство типа таблицы (Visual Basic)](./connection-close-method-table-type-property-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример кода ADOX: пример свойства NumericScale и Precision (Visual Basic)](./adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](./parentcatalog-property-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](./sortorder-property-example-vb.md)   
 [Коллекция Columns (ADOX)](./columns-collection-adox.md)   
 [Коллекция Properties (ADO)](../ado-api/properties-collection-ado.md)