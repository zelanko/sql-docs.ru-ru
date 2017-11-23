---
title: "Свойство DrilledDown (ADO MD) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- DrilledDown
- Member::DrilledDown
helpviewer_keywords: DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5148ba1d2b349ff23af4961445d73348772cd088
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="drilleddown-property-ado-md"></a>Свойство DrilledDown (ADO MD)
Указывает, следуют ли дочерние элементы [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) на оси.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **логическое** значение и доступно только для чтения. **DrilledDown** возвращает **True** при наличии нет дочерних элементов текущего элемента по оси. **DrilledDown** возвращает **False** Если текущий элемент имеет один или несколько дочерних элементов на оси.  
  
## <a name="remarks"></a>Замечания  
 Используйте **DrilledDown** свойства, чтобы определить, существует ли хотя бы одного дочернего элемента этот элемент на оси сразу после этого элемента. Эта информация полезна при отображении элемента.  
  
 Это свойство поддерживается только на [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объектов, принадлежащих [позиции](../../../ado/reference/ado-md-api/position-object-ado-md.md) объекта. Произошла ошибка при обращении к этому свойству из **член** объектов, принадлежащих [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Member (многомерные объекты ADO)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство ParentSameAsPrev (многомерные объекты ADO)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
