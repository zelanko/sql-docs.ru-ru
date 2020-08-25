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
ms.openlocfilehash: 33839c31745976cc6df89e02b728a25ae8624fa5
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776712"
---
# <a name="axes-collection-ado-md"></a>Коллекция Axes (многомерные объекты ADO)
Содержит объекты [осей](./axis-object-ado-md.md) , определяющие набор ячеек.  
  
## <a name="remarks"></a>Remarks  
 Объект набора [ячеек](./cellset-object-ado-md.md) содержит коллекцию **осей** . После открытия набора **ячеек** эта коллекция будет содержать по крайней мере одну **ось**. Более подробное описание использования объектов **Axis** см. в объекте [Axis](./axis-object-ado-md.md) .  
  
> [!NOTE]
>  Ось фильтра набора **ячеек** не содержится в коллекции **осей** . Дополнительные сведения см. в свойстве [филтераксис](./filteraxis-property-ado-md.md) .  
  
 **Оси** — это стандартная коллекция ADO. С помощью свойств и методов коллекции можно выполнять следующие действия.  
  
-   Получите количество объектов в коллекции со свойством [Count](../ado-api/count-property-ado.md) .  
  
-   Возврат объекта из коллекции со свойством [элемента](../ado-api/item-property-ado.md) по умолчанию.  
  
-   Обновите объекты в коллекции от поставщика с помощью метода [Refresh](../ado-api/refresh-method-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](./axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример набора ячеек (Visual Basic)](./cellset-example-vb.md)   
 [Объект Axis (многомерные объекты ADO)](./axis-object-ado-md.md)