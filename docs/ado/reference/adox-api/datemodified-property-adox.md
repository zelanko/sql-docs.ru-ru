---
title: "Свойство DateModified (ADOX) | Документы Microsoft"
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
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f76f2f250ae7a40cdb2184ce29c5e20772f7ccaf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="datemodified-property-adox"></a>Свойство DateModified (ADOX)
Указывает дату последнего изменения объекта.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **Variant** значение, указывающее, изменен. Имеет значение null при **DateModified** не поддерживается поставщиком.  
  
## <a name="remarks"></a>Замечания  
 **DateModified** свойство имеет значение null для добавленного объектов. После добавления нового [представление](../../../ado/reference/adox-api/view-object-adox.md) или [процедура](../../../ado/reference/adox-api/procedure-object-adox.md), необходимо вызвать [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод [представления](../../../ado/reference/adox-api/views-collection-adox.md) или [процедуры ](../../../ado/reference/adox-api/procedures-collection-adox.md) коллекции для получения значений для **DateModified** свойство.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект процедуры (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Объект таблицы (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Объект представления (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>См. также:  
 [DateCreated и DateModified-пример свойства (Visual Basic)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Свойство DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)

