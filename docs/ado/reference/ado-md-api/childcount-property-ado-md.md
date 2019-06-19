---
title: Свойство ChildCount (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8d9a0d746d88423c699907e266a93a2b3a08e031
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66709564"
---
# <a name="childcount-property-ado-md"></a>Свойство ChildCount (многомерные объекты ADO)
Указывает количество элементов, для которого текущий [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объект является родительской в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **Long** целое число и доступен только для чтения.  
  
## <a name="remarks"></a>Примечания  
 Используйте **ChildCount** возвращаемого приблизительное количество дочерних элементов свойства **член** имеет. Фактический дочерних элементов **член** может возвращаться [дочерние элементы](../../../ado/reference/ado-md-api/children-property-ado-md.md) свойство.  
  
 Для **член** объектов из [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объект, максимальное число возвращаемых 65536. Если фактическое число дочерних элементов превышает 65536, возвращаемое значение будет по-прежнему 65536. Таким образом, приложения должны интерпретировать **ChildCount** 65 536 как равным или больше, чем 65536 дочерних элементов.  
  
 Для **член** объектов из [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) , используйте коллекции ADO [число](../../../ado/reference/ado-api/count-property-ado.md) свойство **дочерние элементы** коллекции, чтобы определить точное число дочерних элементов. Определение точное число дочерних элементов может быть медленным, если велико число дочерних объектов в коллекции.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Children (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Коллекция Members (многомерные объекты ADO)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
