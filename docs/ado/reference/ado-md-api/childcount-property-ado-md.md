---
title: Свойство ChildCount (ADO MD) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 93052e44fdf7ce5e939478f9822653696dcc1b76
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Children (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Коллекция Members (многомерные объекты ADO)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
