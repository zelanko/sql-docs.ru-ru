---
title: "Ячейки объекта (ADO MD) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a8b634548700a92a2524a50cbac7548eea871d7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="cell-object-ado-md"></a>Объект ячейки (ADO MD)
Представляет данные пересечения оси координат, содержащаяся в наборе ячеек.  
  
## <a name="remarks"></a>Remarks  
 Объект **ячейки** возвращенный объект [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта.  
  
 С коллекциями и свойствами **ячейки** объекта, можно сделать следующее:  
  
-   Возвращает данные в **ячейки** с [значение](../../../ado/reference/ado-md-api/value-property-ado-md.md) свойства.  
  
-   Возвращает строку, представляющую форматированный вывод **значение** свойство с [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) свойство.  
  
-   Возвращает порядковый номер **ячейки** в **ячеек** с [порядковый номер](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) свойство.  
  
-   Определить положение **ячейки** в [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) с [позиций](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) коллекции.  
  
-   Получить другие сведения о **ячейки** с помощью стандартных ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 **Свойства** коллекция содержит указанный поставщик свойства. В следующей таблице перечислены свойства, которые могут быть доступны. Фактическое свойство списка могут различаться в зависимости от реализации поставщика. См. в документации для поставщика более полный список доступных свойств.  
  
|Название|Описание|  
|----------|-----------------|  
|BackColor|Цвет фона, используемый при отображении ячейки.|  
|FontFlags|Битовая маска, определяющая стиль шрифта.|  
|FontName|Шрифт, используемый для отображения значения ячейки.|  
|FontSize|Размер шрифта, используемого для отображения значения ячейки.|  
|ForeColor|Цвет переднего плана, используемый при отображении ячейки.|  
|FormatString|Значение в форматированную строку.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример оси (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Объект набора ячеек (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Коллекция позиций (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
