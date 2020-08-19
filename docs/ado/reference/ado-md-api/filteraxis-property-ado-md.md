---
description: Свойство FilterAxis (многомерные объекты ADO)
title: Свойство Филтераксис (объекты данных ActiveX (MD)) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 07bc04f345659bbaeb97f754bb00b124977276c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441036"
---
# <a name="filteraxis-property-ado-md"></a>Свойство FilterAxis (многомерные объекты ADO)
Указывает данные фильтра о текущем наборе [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает объект [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) и доступен только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **филтераксис** , чтобы получить сведения об измерениях, которые использовались для среза данных. Свойство [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) **оси** возвращает число измерений среза. Эта ось обычно содержит только одну строку.  
  
 **Ось** , возвращенная **филтераксис** , не содержится в коллекции [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) для объекта набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект Axis (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Объект Dimension (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Свойство DimensionCount (многомерные объекты ADO)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
