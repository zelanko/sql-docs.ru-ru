---
description: Объект Axis (многомерные объекты ADO)
title: Объект Axis (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Axis
helpviewer_keywords:
- Axis object [ADO MD]
ms.assetid: 5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada
author: rothja
ms.author: jroth
ms.openlocfilehash: 733a2962e381a7b8918fccfd076f44dbbc23da1e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441286"
---
# <a name="axis-object-ado-md"></a>Объект Axis (многомерные объекты ADO)
Представляет координату или ось фильтрации набора ячеек, содержащего выбранные элементы одного или нескольких измерений.  
  
## <a name="remarks"></a>Remarks  
 Объект **Axis** может содержаться в коллекции [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) или возвращаться свойством [филтераксис](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
 С помощью коллекций и свойств объекта **Axis** можно выполнять следующие действия.  
  
-   Определяет **ось** с помощью свойства [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) .  
  
-   Перебирает каждую позицию вдоль **оси** с помощью коллекции [Positions](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) .  
  
-   Получите количество измерений на **оси** со свойством [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) .  
  
-   Получите атрибуты **оси** , зависящие от поставщика, со стандартной коллекцией [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/axis-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример оси (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Коллекция осей (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Коллекция Positions (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
