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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f6d6e03dd3288a5b0ca71bb9e129e1a57abf7c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949321"
---
# <a name="parent-property-ado-md"></a>Свойство Parent (многомерные объекты ADO)
Указывает элемент, являющийся родительским по отношению к текущему [элементу](../../../ado/reference/ado-md-api/member-object-ado-md.md) в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает объект [члена](../../../ado/reference/ado-md-api/member-object-ado-md.md) и доступен только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Элемент, расположенный на верхнем уровне иерархии (корень), не имеет родителя. Это свойство поддерживается только для объектов- **членов** , принадлежащих объекту [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту- [положению](../../../ado/reference/ado-md-api/position-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство Children (многомерные объекты ADO)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
