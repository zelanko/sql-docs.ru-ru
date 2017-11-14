---
title: "Размер свойств (поток ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c5a4027bf589a469092a6605743df3d08147e7d2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="size-property-ado-stream"></a>Свойство Size (поток ADO)
Указывает размер потока в байтах.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинные** значение, указывающее размер потока в байтах. Значение по умолчанию — размер потока или значение -1, если известен размер потока.  
  
## <a name="remarks"></a>Замечания  
 **Размер** может использоваться только с открытым [поток](../../../ado/reference/ado-api/stream-object-ado.md) объектов.  
  
> [!NOTE]
>  Любое количество битов, которые могут храниться в **поток** объекта, ограничиваемое только системными ресурсами. Если **поток** содержит дополнительные биты не могут быть представлены **длинные** значение, **размер** усекается и поэтому неточно представлять длину **Поток**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект потока (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство Size (параметр ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)

