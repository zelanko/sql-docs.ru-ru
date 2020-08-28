---
description: Объект Axis (многомерные объекты ADO)
title: Объект Axis (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 6206ee753e42853dc0f209cb80fb9571806f68d6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987395"
---
# <a name="axis-object-ado-md"></a>Объект Axis (многомерные объекты ADO)
Представляет координату или ось фильтрации набора ячеек, содержащего выбранные элементы одного или нескольких измерений.  
  
## <a name="remarks"></a>Remarks  
 Объект **Axis** может содержаться в коллекции [осей](./axes-collection-ado-md.md) или возвращаться свойством [филтераксис](./filteraxis-property-ado-md.md) набора [ячеек](./cellset-object-ado-md.md).  
  
 С помощью коллекций и свойств объекта **Axis** можно выполнять следующие действия.  
  
-   Определяет **ось** с помощью свойства [Name](./name-property-ado-md.md) .  
  
-   Перебирает каждую позицию вдоль **оси** с помощью коллекции [Positions](./positions-collection-ado-md.md) .  
  
-   Получите количество измерений на **оси** со свойством [DimensionCount](./dimensioncount-property-ado-md.md) .  
  
-   Получите атрибуты **оси** , зависящие от поставщика, со стандартной коллекцией [свойств](../ado-api/properties-collection-ado.md) ADO.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](./axis-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример оси (VBScript)](./axis-example-vbscript.md)   
 [Коллекция осей (объекты данных ActiveX (MD))](./axes-collection-ado-md.md)   
 [Коллекция Positions (объекты данных ActiveX (MD))](./positions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../ado-api/properties-collection-ado.md)