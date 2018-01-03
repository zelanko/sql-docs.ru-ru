---
title: "Свойство (ADO) элемента | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
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
helpviewer_keywords: Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bec4236ff89d27a4db3e4606ea95401e75ba2590
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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
 *Index*  
 Объект **Variant** выражение, результатом которого является имя или порядковый номер объекта в коллекции.  
  
## <a name="remarks"></a>Remarks  
 Используйте **элемент** свойство для возврата объекта в коллекции. Если **элемент** не удается найти объект в коллекции, соответствующий *индекс* аргументов, возникает ошибка. Кроме того некоторые коллекции не поддерживают именованные объекты; для таких коллекций необходимо использовать порядковый номер ссылки.  
  
 **Элемент** свойство является свойством по умолчанию для всех коллекций; таким образом, являются взаимозаменяемыми следующие формы синтаксиса:  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Коллекция Axes (многомерные объекты ADO)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Коллекция CubeDefs (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Коллекция Dimensions (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Коллекция Hierarchies (многомерные объекты ADO)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Коллекция Indexes (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Коллекция Keys (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Коллекция Levels (многомерные объекты ADO)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Коллекция Members (многомерные объекты ADO)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Коллекция Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Коллекция Positions (многомерные объекты ADO)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства элементов (Visual Basic)](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [Пример свойства Item (Visual C++)](../../../ado/reference/ado-api/item-property-example-vc.md)   
