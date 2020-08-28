---
description: Свойство Parent (многомерные объекты ADO)
title: Свойство Parent (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 93d7d550c4d70f207c3ab0fdeea0fa4ab0812c79
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986215"
---
# <a name="parent-property-ado-md"></a>Свойство Parent (многомерные объекты ADO)
Указывает элемент, являющийся родительским по отношению к текущему [элементу](./member-object-ado-md.md) в иерархии.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает объект [члена](./member-object-ado-md.md) и доступен только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Элемент, расположенный на верхнем уровне иерархии (корень), не имеет родителя. Это свойство поддерживается только для объектов- **членов** , принадлежащих объекту [уровня](./level-object-ado-md.md) . Ошибка возникает, когда на это свойство ссылаются объекты- **члены** , принадлежащие объекту- [положению](./position-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Member (многомерные объекты ADO)](./member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Children (многомерные объекты ADO)](./children-property-ado-md.md)