---
title: "Свойство (ADO) элемента | Документы Microsoft"
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
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 59779714027c0ff619293d01de851daec7bbe158
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="item-property-ado"></a>Свойство Item (ADO)
Указывает конкретный элемент коллекции по имени или порядковый номер.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает ссылку на объект.  
  
## <a name="parameters"></a>Параметры  
 *Индекс*  
 Объект **Variant** выражение, результатом которого является имя или порядковый номер объекта в коллекции.  
  
## <a name="remarks"></a>Замечания  
 Используйте **элемент** свойство для возврата объекта в коллекции. Если **элемент** не удается найти объект в коллекции, соответствующий *индекс* аргументов, возникает ошибка. Кроме того некоторые коллекции не поддерживают именованные объекты; для таких коллекций необходимо использовать порядковый номер ссылки.  
  
 **Элемент** свойство является свойством по умолчанию для всех коллекций; таким образом, являются взаимозаменяемыми следующие формы синтаксиса:  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Коллекция axes (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Коллекция столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Коллекция CubeDefs (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Коллекции измерений (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Коллекция ошибок (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Коллекция групп (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Коллекция hierarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Коллекция индексов (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Коллекция ключей (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Коллекция уровней (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Члены коллекции (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Коллекция параметров (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Коллекция позиций (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Коллекция процедур (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Коллекция таблиц (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Коллекции пользователей (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Коллекции представлений (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства элементов (Visual Basic)](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [Пример свойства элемента (VC ++)](../../../ado/reference/ado-api/item-property-example-vc.md)   

