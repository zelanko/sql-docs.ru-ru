---
title: "Имя свойства (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Table::PutName
- _Table::GetName
- _Key::Name
- _Key::get_Name
- _Column::GetName
- _Index::Name
- _Index::put_Name
- _Column::PutName
- _Key::put_Name
- _Table::put_Name
- _User25::PutName
- _Index::get_Name
- _Column::get_Name
- _Group25::Name
- _Group25::get_Name
- _Column::Name
- _User25::get_Name
- _Table::Name
- _Group25::GetName
- _Index::PutName
- _Column::put_Name
- _Key::GetName
- _Table::get_Name
- _User25::Name
- _User25::put_Name
- _Index::GetName
- _User25::GetName
helpviewer_keywords:
- Name property [ADOX]
ms.assetid: 81b92baf-b6b9-4f4e-9f33-4503795518cd
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 96a4d83770ee986c781efb9859eb071d197b112c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="name-property-adox"></a>Свойство Name (ADOX)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение.  
  
## <a name="remarks"></a>Замечания  
 Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 **Имя** свойство является чтение и запись на [столбца](../../../ado/reference/adox-api/column-object-adox.md), [группы](../../../ado/reference/adox-api/group-object-adox.md), [ключ](../../../ado/reference/adox-api/key-object-adox.md), [индекс](../../../ado/reference/adox-api/index-object-adox.md), [ Таблица](../../../ado/reference/adox-api/table-object-adox.md), и [пользователя](../../../ado/reference/adox-api/user-object-adox.md) объектов. **Имя** свойство доступно только для чтения на [каталога](../../../ado/reference/adox-api/catalog-object-adox.md), [процедура](../../../ado/reference/adox-api/procedure-object-adox.md), и [представление](../../../ado/reference/adox-api/view-object-adox.md) объектов.  
  
 Для чтения и записи объектов (**столбца**, **группы**, **ключ**, **индекс**, **таблицы** и ** Пользователь** объекты), значение по умолчанию — пустая строка (»»).  
  
> [!NOTE]
>  Для ключей, это свойство доступно только для чтения на **ключ** объектов уже добавлен в коллекцию. Для таблиц, это свойство доступно только для чтения для **таблицы** объектов уже добавлен в коллекцию.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект столбца (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Объект группы (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект индекса (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Объект ключа (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Объект процедуры (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Свойства объекта (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Объект таблицы (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Объект пользователя (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[Объект представления (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>См. также:  
 [Столбцы и таблицы добавьте методы примера имя свойства (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)

