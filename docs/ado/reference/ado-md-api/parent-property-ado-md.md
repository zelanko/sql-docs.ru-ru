---
title: Свойство Parent (объекты данных ActiveX (MD)) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 94e6e920d6ab44265c42b9ca26e2410c43c3659e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765055"
---
# <a name="parent-property-ado-md"></a>Свойство Parent (многомерные объекты ADO)
Указывает элемент, являющийся родительским по отношению к текущему [элементу](../../../ado/reference/ado-md-api/member-object-ado-md.md) в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает объект [члена](../../../ado/reference/ado-md-api/member-object-ado-md.md) и доступен только для чтения.  
  
## <a name="remarks"></a>Примечания  
 Элемент, расположенный на верхнем уровне иерархии (корень), не имеет родителя. Это свойство поддерживается только для объектов- **членов** , принадлежащих объекту [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту- [положению](../../../ado/reference/ado-md-api/position-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Children (многомерные объекты ADO)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
