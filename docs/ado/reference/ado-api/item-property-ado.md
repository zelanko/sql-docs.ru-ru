---
description: Свойство Item (ADO)
title: Свойство Item (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameters::GetItem
- Indexes::GetItem
- Parameters::Item
- Tables::Item
- Procedures::Item
- Users::GetItem
- Tables::GetItem
- Procedures::GetItem
- Users::get_Item
- Users::Item
- Views::GetItem
- Groups::Item
- Groups::get_Item
- Columns::Item
- Indexes::Item
- Fields15::GetItem
- Columns::GetItem
- Fields::Item
- Indexes::get_Item
- Columns::get_Item
- Fields15::Item
- Views::get_Item
- Groups::GetItem
- Errors::get_Item
- Fields15::get_Item
- Tables::get_Item
- Views::Item
- Errors::GetItem
- Parameters::get_Item
- Errors::Item
- Procedures::get_Item
helpviewer_keywords:
- Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bea35ef148aa2f5646420a1c2b46197ce66f0d6
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774683"
---
# <a name="item-property-ado"></a>Свойство Item (ADO)
Указывает конкретный элемент коллекции по имени или порядковому номеру.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает ссылку на объект.  
  
## <a name="parameters"></a>Параметры  
 *Index*  
 Выражение **типа Variant** , результатом которого является либо имя, либо порядковый номер объекта в коллекции.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Item** используется для возврата определенного объекта в коллекции. Если **элемент** не может найти объект в коллекции, соответствующей аргументу *index* , возникает ошибка. Кроме того, некоторые коллекции не поддерживают именованные объекты. для этих коллекций необходимо использовать ссылки на порядковые номера.  
  
 Свойство **Item** является свойством по умолчанию для всех коллекций; Поэтому следующие формы синтаксиса являются взаимозаменяемыми:  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Коллекция Axes (многомерные объекты ADO)](../ado-md-api/axes-collection-ado-md.md)  
        [Коллекция Columns (ADOX)](../adox-api/columns-collection-adox.md)  
        [Коллекция CubeDefs (многомерные объекты ADO)](../ado-md-api/cubedefs-collection-ado-md.md)  
        [Коллекция Dimensions (многомерные объекты ADO)](../ado-md-api/dimensions-collection-ado-md.md)  
        [Коллекция Errors (ADO)](./errors-collection-ado.md)  
        [Коллекция Fields (ADO)](./fields-collection-ado.md)  
        [Коллекция Groups (ADOX)](../adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Коллекция Hierarchies (многомерные объекты ADO)](../ado-md-api/hierarchies-collection-ado-md.md)  
        [Коллекция Indexes (ADOX)](../adox-api/indexes-collection-adox.md)  
        [Коллекция Keys (ADOX)](../adox-api/keys-collection-adox.md)  
        [Коллекция Levels (многомерные объекты ADO)](../ado-md-api/levels-collection-ado-md.md)  
        [Коллекция Members (многомерные объекты ADO)](../ado-md-api/members-collection-ado-md.md)  
        [Коллекция Parameters (ADO)](./parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Коллекция Positions (многомерные объекты ADO)](../ado-md-api/positions-collection-ado-md.md)  
        [Коллекция Procedures (ADOX)](../adox-api/procedures-collection-adox.md)  
        [Коллекция Properties (ADO)](./properties-collection-ado.md)  
        [Коллекция Tables (ADOX)](../adox-api/tables-collection-adox.md)  
        [Коллекция Users (ADOX)](../adox-api/users-collection-adox.md)  
        [Коллекция Views (ADOX)](../adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример свойства Item (Visual Basic)](./item-property-example-vb.md)   
 [Пример свойства Item (Visual C++)](./item-property-example-vc.md)