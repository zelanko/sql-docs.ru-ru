---
title: Свойство FilterAxis (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5015888cfafcce56c97f2369d418ed7be842dd28
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47725962"
---
# <a name="filteraxis-property-ado-md"></a>Свойство FilterAxis (многомерные объекты ADO)
Указывает фильтр сведения о текущем [cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) объекта и только для чтения.  
  
## <a name="remarks"></a>Примечания  
 Используйте **FilterAxis** свойство для возврата сведений об измерениях, которые были использованы для создания среза данных. [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) свойство **оси** возвращает число измерений среза. На этой оси обычно имеет только одну строку.  
  
 **Оси** возвращаемые **FilterAxis** не содержится в [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) коллекции для [набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Axis (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Объект Dimension (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Свойство DimensionCount (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
