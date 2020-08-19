---
description: Коллекция Axes (многомерные объекты ADO)
title: Коллекция осей (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Axes
- Cellset::Axes
helpviewer_keywords:
- Axes collection [ADO MD]
ms.assetid: 072fb21a-ec0f-4b02-9022-1cef3ad4bfff
author: rothja
ms.author: jroth
ms.openlocfilehash: cc93e9ea8568a535067addbd51258074945200db
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441324"
---
# <a name="axes-collection-ado-md"></a>Коллекция Axes (многомерные объекты ADO)
Содержит объекты [осей](../../../ado/reference/ado-md-api/axis-object-ado-md.md) , определяющие набор ячеек.  
  
## <a name="remarks"></a>Remarks  
 Объект набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) содержит коллекцию **осей** . После открытия набора **ячеек** эта коллекция будет содержать по крайней мере одну **ось**. Более подробное описание использования объектов **Axis** см. в объекте [Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md) .  
  
> [!NOTE]
>  Ось фильтра набора **ячеек** не содержится в коллекции **осей** . Дополнительные сведения см. в свойстве [филтераксис](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) .  
  
 **Оси** — это стандартная коллекция ADO. С помощью свойств и методов коллекции можно выполнять следующие действия.  
  
-   Получите количество объектов в коллекции со свойством [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Возврат объекта из коллекции со свойством [элемента](../../../ado/reference/ado-api/item-property-ado.md) по умолчанию.  
  
-   Обновите объекты в коллекции от поставщика с помощью метода [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Объект Axis (многомерные объекты ADO)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)
