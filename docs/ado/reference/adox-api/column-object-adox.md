---
title: "Объект столбца (ADOX) | Документы Microsoft"
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
- Column
helpviewer_keywords:
- Column object [ADOX]
ms.assetid: 6e772783-1bc8-4ea7-94b2-7d7a52ea5c47
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 90ca5950c857ea5037381daae3568bc6c7becd71
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="column-object-adox"></a>Объект столбца (ADOX)
Представляет столбец из таблицы, индекса или ключа.  
  
## <a name="remarks"></a>Remarks  
 Следующий код создает новый **столбца**:  
  
 `Dim obj As New Column`  
  
 С помощью свойств и коллекций **столбца** объекта, вы можете:  
  
-   Определение столбца с [имя свойства (ADOX)](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Укажите тип данных столбца с [свойство Type (ключ) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md) свойство.  
  
-   Определить столбец фиксированной длины, или он может содержать значения null с [атрибуты свойства (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md) свойство.  
  
-   Укажите максимальный размер столбца с [DefinedSize свойство (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md) свойство.  
  
-   Для числовых значений данных, укажите масштаб с [NumericScale свойство (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md) свойство.  
  
-   Для значения числовых данных, указать максимальную точность с [свойство точности (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md) свойство.  
  
-   Укажите [объекта каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md) , которому принадлежит столбец с [ParentCatalog свойство (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md) свойство.  
  
-   Для ключевых столбцов, укажите имя связанного столбца в связанной таблице с [RelatedColumn свойство (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md) свойство.  
  
-   Для индексных столбцов, указывать ли порядок сортировки по возрастанию или по убыванию с [свойство SortOrder (ADOX)](../../../ado/reference/adox-api/sortorder-property-adox.md) свойство.  
  
-   Доступ к свойствам определенного поставщика с [свойства коллекции (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
> [!NOTE]
>  Не все свойства **столбца** объектов могут поддерживаться поставщика данных. Если вы задали значение для свойства, которое поставщик не поддерживает завершится ошибкой. Для новых **столбца** объектов, ошибка возникает, когда объект добавляется в коллекцию. Для существующих объектов ошибка возникает, когда для свойства.  
>   
>  При создании **столбца** объектов наличия соответствующего значения по умолчанию это необязательное свойство не гарантирует, что поставщик поддерживает свойство. Дополнительные сведения о свойствах поставщик поддерживает поставщик документации.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Column](../../../ado/reference/adox-api/column-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Столбцы и таблицы добавьте методы примера имя свойства (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Подключение метода закрытия, пример свойство типа таблицы (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ADOX кода примерах: NumericScale и точности свойства (Visual Basic)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Пример свойства SortOrder (Visual Basic)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [Коллекция столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
