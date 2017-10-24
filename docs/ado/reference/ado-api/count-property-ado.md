---
title: "Свойство Count (ADO) | Документы Microsoft"
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
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 173b2fc9073676e77ad3068e9e9dc3ca76089702
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="count-property-ado"></a>Свойство Count (ADO)
Указывает количество объектов в коллекции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **длинные** значение.  
  
## <a name="remarks"></a>Замечания  
 Используйте **число** свойство, чтобы определить, сколько объектов в данной коллекции.  
  
 Поскольку нумерация для членов коллекции начинается с нуля, всегда следует создавать циклы, начиная с нуля элемента и заканчивая значение **число** свойство минус 1. Если используется Microsoft Visual Basic для перебора элементов коллекции без проверки в **число** свойства, используйте **For Each... Далее** команды.  
  
 Если **число** свойство имеет значение 0, нет ни одного объекта в коллекции.  
  
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
 [Пример свойства Count (Visual Basic)](../../../ado/reference/ado-api/count-property-example-vb.md)   
 [Пример свойства Count (VC ++)](../../../ado/reference/ado-api/count-property-example-vc.md)   
 [Обновить метод (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)

