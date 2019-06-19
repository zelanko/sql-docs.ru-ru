---
title: Родительского свойства (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parent
- Member::Parent
helpviewer_keywords:
- Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f37e6cf355e035044e25979f4e76256936b7e240
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708798"
---
# <a name="parent-property-ado-md"></a>Свойство Parent (многомерные объекты ADO)
Указывает элемент, который является родительским для текущего [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объекта и доступен только для чтения.  
  
## <a name="remarks"></a>Примечания  
 Элемент, который находится на верхнем уровне иерархии (корень) не имеет родителя. Это свойство поддерживается только в **член** объекты, принадлежащие [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта. Произошла ошибка при ссылке на это свойство из **член** объекты, принадлежащие [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Children (многомерные объекты ADO)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
