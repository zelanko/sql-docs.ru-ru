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
ms.openlocfilehash: 0100363a013dc3ea3435ca205822a4f88b56735b
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778143"
---
# <a name="filteraxis-property-ado-md"></a>Свойство FilterAxis (многомерные объекты ADO)
Указывает данные фильтра о текущем наборе [ячеек](./cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает объект [оси](./axis-object-ado-md.md) и доступен только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **филтераксис** , чтобы получить сведения об измерениях, которые использовались для среза данных. Свойство [DimensionCount](./dimensioncount-property-ado-md.md) **оси** возвращает число измерений среза. Эта ось обычно содержит только одну строку.  
  
 **Ось** , возвращенная **филтераксис** , не содержится в коллекции [осей](./axes-collection-ado-md.md) для объекта набора [ячеек](./cellset-object-ado-md.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Cellset (многомерные объекты ADO)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Axis (объекты данных ActiveX (MD))](./axis-object-ado-md.md)   
 [Объект Dimension (объекты данных ActiveX (MD))](./dimension-object-ado-md.md)   
 [Свойство DimensionCount (многомерные объекты ADO)](./dimensioncount-property-ado-md.md)