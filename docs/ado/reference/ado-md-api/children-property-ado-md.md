---
title: Свойство Children (ADO MD) | Документы Microsoft
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
- Member::Children
- Children
helpviewer_keywords:
- Children property [ADO MD]
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2876adffe59d46cc3e0d0a83502f1e355153bc80
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="children-property-ado-md"></a>Свойство Children (ADO MD)
Возвращает [элементы](../../../ado/reference/ado-md-api/members-collection-ado-md.md) коллекции, для которого текущий [члена](../../../ado/reference/ado-md-api/member-object-ado-md.md) является родительской в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **члены** коллекции и доступен только для чтения.  
  
## <a name="remarks"></a>Замечания  
 **Дочерние элементы** свойство содержит **члены** коллекции, для которого текущий **член** является иерархической родительским. Конечный уровень **член** объекты не имеют дочерних элементов **члены** коллекции. Это свойство поддерживается только на **член** объектов, принадлежащих [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта. Произошла ошибка при обращении к этому свойству из **член** объектов, принадлежащих [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство ChildCount (многомерные объекты ADO)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
