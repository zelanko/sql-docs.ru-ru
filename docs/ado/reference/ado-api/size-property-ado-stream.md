---
title: Размер свойств (поток ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6d39bb563acfde83a08f08c00fee66cc9b81967
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281889"
---
# <a name="size-property-ado-stream"></a>Свойство Size (поток ADO)
Указывает размер потока в байтах.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинные** значение, указывающее размер потока в байтах. Значение по умолчанию — размер потока или значение -1, если известен размер потока.  
  
## <a name="remarks"></a>Примечания  
 **Размер** может использоваться только с открытым [поток](../../../ado/reference/ado-api/stream-object-ado.md) объектов.  
  
> [!NOTE]
>  Любое количество битов, которые могут храниться в **поток** объекта, ограничиваемое только системными ресурсами. Если **поток** содержит дополнительные биты не могут быть представлены **длинные** значение, **размер** усекается и поэтому неточно представлять длину **Поток**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Size (объект Parameter ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
