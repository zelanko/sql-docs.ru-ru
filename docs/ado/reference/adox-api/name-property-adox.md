---
title: "Имя свойства (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
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
helpviewer_keywords: Name property [ADOX]
ms.assetid: 81b92baf-b6b9-4f4e-9f33-4503795518cd
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 47d95403232ef3b5a13fc5f7c30854591f837bab
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="name-property-adox"></a>Свойство Name (ADOX)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение.  
  
## <a name="remarks"></a>Замечания  
 Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 **Имя** свойство является чтение и запись на [столбца](../../../ado/reference/adox-api/column-object-adox.md), [группы](../../../ado/reference/adox-api/group-object-adox.md), [ключ](../../../ado/reference/adox-api/key-object-adox.md), [индекс](../../../ado/reference/adox-api/index-object-adox.md), [ Таблица](../../../ado/reference/adox-api/table-object-adox.md), и [пользователя](../../../ado/reference/adox-api/user-object-adox.md) объектов. **Имя** свойство доступно только для чтения на [каталога](../../../ado/reference/adox-api/catalog-object-adox.md), [процедура](../../../ado/reference/adox-api/procedure-object-adox.md), и [представление](../../../ado/reference/adox-api/view-object-adox.md) объектов.  
  
 Для чтения и записи объектов (**столбца**, **группы**, **ключ**, **индекс**, **таблицы** и  **Пользователь** объекты), значение по умолчанию — пустая строка (»»).  
  
> [!NOTE]
>  Для ключей, это свойство доступно только для чтения на **ключ** объектов уже добавлен в коллекцию. Для таблиц, это свойство доступно только для чтения для **таблицы** объектов уже добавлен в коллекцию.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект Index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Объект Key (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Объект Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>См. также:  
 [Столбцы и таблицы добавьте методы примера имя свойства (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
