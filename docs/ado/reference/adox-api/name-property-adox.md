---
title: Имя свойства (ADOX) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: 7f7b61dd2c1dc5899852234d23148969dad9c3dc
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66706373"
---
# <a name="name-property-adox"></a>Свойство Name (ADOX)
Указывает имя объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение.  
  
## <a name="remarks"></a>Примечания  
 Имена не обязательно должны быть уникальными в пределах коллекции.  
  
 **Имя** свойство доступно для чтения/записи на [столбец](../../../ado/reference/adox-api/column-object-adox.md), [группы](../../../ado/reference/adox-api/group-object-adox.md), [ключ](../../../ado/reference/adox-api/key-object-adox.md), [индекс](../../../ado/reference/adox-api/index-object-adox.md), [ Таблица](../../../ado/reference/adox-api/table-object-adox.md), и [пользователя](../../../ado/reference/adox-api/user-object-adox.md) объектов. **Имя** свойство доступно только для чтения на [каталога](../../../ado/reference/adox-api/catalog-object-adox.md), [процедуры](../../../ado/reference/adox-api/procedure-object-adox.md), и [представление](../../../ado/reference/adox-api/view-object-adox.md) объектов.  
  
 Для чтения и записи объектов (**столбец**, **группы**, **ключ**, **индекс**, **таблицы** и  **Пользователь** объекты), значение по умолчанию — пустая строка (»»).  
  
> [!NOTE]
>  Для ключей, это свойство только для чтения на **ключ** объектов, уже добавлен в коллекцию. Для таблиц, это свойство только для чтения для **таблицы** объектов, уже добавлен в коллекцию.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект Index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Объект Key (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Объект Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[Объект View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>См. также  
 [Столбцов и таблиц методов append для коллекций, пример свойства Name (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Append коллекции Keys метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Пример свойства ParentCatalog (Visual Basic)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
