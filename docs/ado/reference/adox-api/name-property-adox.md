---
title: Свойство Name (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 52808cf9e90c6779efb9f95e385f8df501bae870
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965764"
---
# <a name="name-property-adox"></a>Свойство Name (ADOX)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение.  
  
## <a name="remarks"></a>Remarks  
 Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 Свойство **Name** доступно для чтения и записи в объектах [столбца](../../../ado/reference/adox-api/column-object-adox.md), [группы](../../../ado/reference/adox-api/group-object-adox.md), [ключа](../../../ado/reference/adox-api/key-object-adox.md), [индекса](../../../ado/reference/adox-api/index-object-adox.md), [таблицы](../../../ado/reference/adox-api/table-object-adox.md)и [пользователя](../../../ado/reference/adox-api/user-object-adox.md) . Свойство **Name** доступно только для чтения в объектах [каталога](../../../ado/reference/adox-api/catalog-object-adox.md), [процедуры](../../../ado/reference/adox-api/procedure-object-adox.md)и [представления](../../../ado/reference/adox-api/view-object-adox.md) .  
  
 Для объектов, предназначенных для чтения и записи (**столбцов**, **групп**, **ключевых**, **индексов**, **таблиц** и **пользовательских** объектов), значением по умолчанию является пустая строка ("").  
  
> [!NOTE]
>  Для ключей это свойство доступно только для чтения в объектах **ключей** , уже добавленных в коллекцию. Для таблиц это свойство доступно только для чтения для объектов **таблицы** , уже добавленных в коллекцию.  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект Index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Объект Key (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Объект Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>См. также:  
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
