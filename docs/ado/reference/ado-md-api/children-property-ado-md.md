---
title: Свойство Children (объекты данных ActiveX (MD)) | Документация Майкрософт
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
ms.openlocfilehash: cbec9733044127d23e75364697a41ccd7e8910e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67911523"
---
# <a name="children-property-ado-md"></a>Свойство Children (многомерные объекты ADO)
Возвращает коллекцию [Members](../../../ado/reference/ado-md-api/members-collection-ado-md.md) , для которой текущий [элемент](../../../ado/reference/ado-md-api/member-object-ado-md.md) является родительским в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает коллекцию **Members** и доступна только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Children** содержит коллекцию **Members** , для которой текущий **элемент** является иерархическим родителем. Объекты **элементов** конечного уровня не имеют дочерних элементов в коллекции **Members** . Это свойство поддерживается только для объектов- **членов** , принадлежащих объекту [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту- [положению](../../../ado/reference/ado-md-api/position-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство ChildCount (многомерные объекты ADO)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
