---
title: Свойство Children (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Children
- Children
helpviewer_keywords:
- Children property [ADO MD]
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f489a87573dabbd091f5d2dce8a084b53cc5771e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626132"
---
# <a name="children-property-ado-md"></a>Свойство Children (многомерные объекты ADO)
Возвращает [члены](../../../ado/reference/ado-md-api/members-collection-ado-md.md) коллекции, для которого текущий [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) является родителем в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **члены** коллекции и доступен только для чтения.  
  
## <a name="remarks"></a>Примечания  
 **Дочерние элементы** свойство содержит **члены** коллекции, для которого текущий **член** является иерархического родительского объекта. Конечный уровень **член** объекты не имеют дочерних элементов **члены** коллекции. Это свойство поддерживается только в **член** объекты, принадлежащие [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта. Произошла ошибка при ссылке на это свойство из **член** объекты, принадлежащие [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство ChildCount (многомерные объекты ADO)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
