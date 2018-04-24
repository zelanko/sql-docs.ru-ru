---
title: Оси коллекции (ADO MD) | Документы Microsoft
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
- Axes
- Cellset::Axes
helpviewer_keywords:
- Axes collection [ADO MD]
ms.assetid: 072fb21a-ec0f-4b02-9022-1cef3ad4bfff
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b2728d025ee0ba850712ff56cad7ef46bcb0b996
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="axes-collection-ado-md"></a>Коллекция axes (ADO MD)
Содержит [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) объектами, которые определяют набор ячеек.  
  
## <a name="remarks"></a>Замечания  
 Объект [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объект содержит **осей** коллекции. Один раз **ячеек** будет открыт, эта коллекция будет содержать по крайней мере один **оси**. В разделе [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) объекта более подробное описание использования **оси** объектов.  
  
> [!NOTE]
>  Ось фильтра **ячеек** не содержится в **осей** коллекции. В разделе [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) получения дополнительных сведений.  
  
 **Оси** — это обычная коллекция ADO. С помощью свойств и методов в коллекции можно сделать следующее:  
  
-   Получить число объектов в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Вернуть объект из коллекции с заданным по умолчанию [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Обновление объектов в коллекции из поставщика с [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Объект Axis (многомерные объекты ADO)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)
