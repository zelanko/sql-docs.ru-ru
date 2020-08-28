---
description: Свойство Children (многомерные объекты ADO)
title: Свойство Children (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7f6af5f18de07a3d9eb2f74ace77a9b4032303f1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987125"
---
# <a name="children-property-ado-md"></a>Свойство Children (многомерные объекты ADO)
Возвращает коллекцию [Members](./members-collection-ado-md.md) , для которой текущий [элемент](./member-object-ado-md.md) является родительским в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает коллекцию **Members** и доступна только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Свойство **Children** содержит коллекцию **Members** , для которой текущий **элемент** является иерархическим родителем. Объекты **элементов** конечного уровня не имеют дочерних элементов в коллекции **Members** . Это свойство поддерживается только для объектов- **членов** , принадлежащих объекту [уровня](./level-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту- [положению](./position-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Member (многомерные объекты ADO)](./member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство ChildCount (многомерные объекты ADO)](./childcount-property-ado-md.md)