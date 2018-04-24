---
title: Свойство FilterAxis (ADO MD) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f7c137f5b555dca6711ad46ae4c20ac1f6d5805d
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="filteraxis-property-ado-md"></a>Свойство FilterAxis (ADO MD)
Указывает фильтр сведений о текущей [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) объекта и доступно только для чтения.  
  
## <a name="remarks"></a>Замечания  
 Используйте **FilterAxis** свойство для возврата сведений об измерениях, которые использовались для создания среза данных. [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) свойство **оси** возвращает число измерений среза. Эта ось обычно имеет только одну строку.  
  
 **Оси** возвращенных **FilterAxis** не содержится в [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) коллекции для [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Axis (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Объект измерения (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Свойство DimensionCount (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
