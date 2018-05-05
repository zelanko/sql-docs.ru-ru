---
title: Родительского свойства (ADO MD) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parent
- Member::Parent
helpviewer_keywords:
- Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3825851d516b0b2d4ff430dcc017a3cc2cebebc9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="parent-property-ado-md"></a>Родительское свойство (ADO MD)
Указывает элемент, который является родительским для текущего [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объекта и доступно только для чтения.  
  
## <a name="remarks"></a>Замечания  
 Элемент, который находится на верхнем уровне иерархии (корневой) не имеет родителя. Это свойство поддерживается только в **член** объектов, принадлежащих [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта. Произошла ошибка при обращении к этому свойству из **член** объектов, принадлежащих [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Children (многомерные объекты ADO)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
