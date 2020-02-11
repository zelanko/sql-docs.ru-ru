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
ms.openlocfilehash: db2c2dbe6af2a50fc2507a9ade92d83e0502f2ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67966911"
---
# <a name="column-object-adox"></a>Объект Column (ADOX)
Представляет столбец из таблицы, индекса или ключа.  
  
## <a name="remarks"></a>Remarks  
 Следующий код создает новый **столбец**:  
  
 `Dim obj As New Column`  
  
 Свойства и коллекции объекта **Column** позволяют:  
  
-   Найдите столбец с помощью свойства [Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Укажите тип данных столбца с помощью свойства [свойства Type (Key) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md) .  
  
-   Определите, имеет ли столбец фиксированную длину или может ли он содержать значения NULL со свойством [Attributes (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) .  
  
-   Укажите максимальный размер столбца с помощью свойства [DefinedSize (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) .  
  
-   Для числовых значений данных укажите масштаб с помощью свойства [NumericScale (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) .  
  
-   Для значения числовых данных укажите максимальную точность с помощью свойства [Precision (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) .  
  
-   Укажите [объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) , которому принадлежит столбец со свойством [ParentCatalog (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) .  
  
-   Для ключевых столбцов укажите имя связанного столбца в связанной таблице со свойством [RelatedColumn (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) .  
  
-   Для столбцов индекса укажите, будет ли порядок сортировки по возрастанию или убыванию со свойством [SortOrder (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) .  
  
-   Доступ к свойствам, зависящим от поставщика, с коллекцией [коллекций свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
> [!NOTE]
>  Поставщик данных может поддерживать не все свойства объектов **Column** . Если задано значение для свойства, которое не поддерживается поставщиком, возникнет ошибка. Для новых объектов **столбцов** ошибка возникает при добавлении объекта в коллекцию. Для существующих объектов при задании свойства возникнет ошибка.  
>   
>  При создании объектов **столбцов** наличие соответствующего значения по умолчанию для необязательного свойства не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах, поддерживаемых поставщиком, см. в документации поставщика.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Column](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример метода Close соединения, свойство типа таблицы (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример кода ADOX: пример свойства NumericScale и Precision (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
