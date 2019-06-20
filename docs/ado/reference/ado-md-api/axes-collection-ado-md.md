---
title: Коллекция (многомерные Объекты ADO) осей | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f30d7fed3748e954410272d8c1a019194c335ea1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66709943"
---
# <a name="axes-collection-ado-md"></a>Коллекция Axes (многомерные объекты ADO)
Содержит [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) объектами, которые определяют набор ячеек.  
  
## <a name="remarks"></a>Примечания  
 Объект [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объект содержит **осей** коллекции. Один раз **набора ячеек** будет открыт, эта коллекция будет содержать по крайней мере **оси**. См. в разделе [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) объекта более подробное описание способов использования **оси** объектов.  
  
> [!NOTE]
>  Ось фильтра **Cellset** не содержится в **осей** коллекции. См. в разделе [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) получения дополнительных сведений.  
  
 **Оси** является стандартной коллекции ADO. С помощью свойства и методы коллекции сделайте следующее:  
  
-   Получить число объектов в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Вернуть объект из коллекции со значением по умолчанию [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Обновление объектов в коллекции от поставщика с [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/axes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта Cellset (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Объект Axis (многомерные объекты ADO)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)
