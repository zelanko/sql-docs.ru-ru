---
description: Свойство Name (ADOX)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0376017e4ab74822a076379385b4b5ab457afca0
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769963"
---
# <a name="name-property-adox"></a>Свойство Name (ADOX)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение.  
  
## <a name="remarks"></a>Remarks  
 Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 Свойство **Name** доступно для чтения и записи в объектах [столбца](./column-object-adox.md), [группы](./group-object-adox.md), [ключа](./key-object-adox.md), [индекса](./index-object-adox.md), [таблицы](./table-object-adox.md)и [пользователя](./user-object-adox.md) . Свойство **Name** доступно только для чтения в объектах [каталога](./catalog-object-adox.md), [процедуры](./procedure-object-adox.md)и [представления](./view-object-adox.md) .  
  
 Для объектов, предназначенных для чтения и записи (**столбцов**, **групп**, **ключевых**, **индексов**, **таблиц** и **пользовательских** объектов), значением по умолчанию является пустая строка ("").  
  
> [!NOTE]
>  Для ключей это свойство доступно только для чтения в объектах **ключей** , уже добавленных в коллекцию. Для таблиц это свойство доступно только для чтения для объектов **таблицы** , уже добавленных в коллекцию.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Column (ADOX)](./column-object-adox.md)  
        [Объект Group (ADOX)](./group-object-adox.md)  
        [Объект Index (ADOX)](./index-object-adox.md)  
    :::column-end:::
    :::column:::
        [Объект Key (ADOX)](./key-object-adox.md)  
        [Объект Procedure (ADOX)](./procedure-object-adox.md)  
        [Объект Property (ADO)](../ado-api/property-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Table (ADOX)](./table-object-adox.md)  
        [Объект User (ADOX)](./user-object-adox.md)  
        [Объект View (ADOX)](./view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Методы добавления столбцов и таблиц, пример свойства Name (Visual Basic)](./columns-and-tables-append-methods-name-property-example-vb.md)   
 [Пример свойств для добавления ключей, типа ключа, RelatedColumn, RelatedTable и UpdateRule (Visual Basic)](./keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](./parentcatalog-property-example-vb.md)