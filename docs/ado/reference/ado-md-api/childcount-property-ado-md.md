---
title: "Свойство ChildCount (ADO MD) | Документы Microsoft"
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
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6ca8ee6c01299c3db45977a8e64c4f2afd46c7d3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="childcount-property-ado-md"></a>Свойство ChildCount (ADO MD)
Указывает количество элементов, для которого текущий [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объект является родительской в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинные** целое число со знаком и доступно только для чтения.  
  
## <a name="remarks"></a>Замечания  
 Используйте **ChildCount** свойство для возврата приблизительное количество детей **член** имеет. Фактическое дочерних элементов **член** может быть возвращен [дочерних](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойство.  
  
 Для **член** объектов из [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта возвращается не более 65536. Если реальное количество дочерних элементов превышает 65536, возвращаемое значение будет по-прежнему 65536. Таким образом, приложения должен быть способен интерпретировать **ChildCount** 65536 как равно или больше, чем 65536 дочерних элементов.  
  
 Для **член** объектов из [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) , используйте коллекцию ADO [число](../../../ado/reference/ado-api/count-property-ado.md) свойство **дочерние элементы** коллекции для определения точное число дочерних элементов. Определение точное число дочерних элементов может быть медленным, если существует большое число дочерних элементов в коллекции.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект члена (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство Children (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Члены коллекции (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)

