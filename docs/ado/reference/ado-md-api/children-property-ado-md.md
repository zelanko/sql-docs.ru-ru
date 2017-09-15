---
title: "Свойство Children (ADO MD) | Документы Microsoft"
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
- Member::Children
- Children
helpviewer_keywords:
- Children property [ADO MD]
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c851f06ecd3cec67769f761cb2aea400c5b06d9e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="children-property-ado-md"></a>Свойство Children (ADO MD)
Возвращает [элементы](../../../ado/reference/ado-md-api/members-collection-ado-md.md) коллекции, для которого текущий [члена](../../../ado/reference/ado-md-api/member-object-ado-md.md) является родительской в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **члены** коллекции и доступен только для чтения.  
  
## <a name="remarks"></a>Замечания  
 **Дочерние элементы** свойство содержит **члены** коллекции, для которого текущий **член** является иерархической родительским. Конечный уровень **член** объекты не имеют дочерних элементов **члены** коллекции. Это свойство поддерживается только на **член** объектов, принадлежащих [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта. Произошла ошибка при обращении к этому свойству из **член** объектов, принадлежащих [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект члена (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство ChildCount (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
