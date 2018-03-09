---
title: "Состояние свойства (ADO MD) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1886dae43bdb764a67fa5e44b1e8fe9744c0cb5f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="state-property-ado-md"></a>Свойство State (ADO MD)
Указывает текущее состояние набора ячеек.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинные** целое число, указывающее текущее состояние [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта и доступно только для чтения. Допустимы следующие значения: **adStateClosed** (0) и **adStateOpen** (1).  
  
## <a name="remarks"></a>Remarks  
 Для использования [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) имена констант, необходимо иметь ADO библиотеки типов, на которые ссылается проект. В разделе [с помощью ADO с ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md) для получения дополнительной информации.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Close-метод (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Метод Open (многомерные объекты ADO)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
