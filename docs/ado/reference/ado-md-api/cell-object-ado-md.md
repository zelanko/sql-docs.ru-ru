---
title: Ячейки объект (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bbf97a4095f2295b8851f87ba20ab083938e70ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67947749"
---
# <a name="cell-object-ado-md"></a>Объект Cell (многомерные объекты ADO)
Представляет данные на пересечении координатах оси, содержащиеся в наборе ячеек.  
  
## <a name="remarks"></a>Примечания  
 Объект **ячейки** объект, возвращаемый методом [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство [набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта.  
  
 С помощью коллекций и свойств **ячейки** объекта, можно выполнять следующие:  
  
-   Возвращать данные в **ячейки** с [значение](../../../ado/reference/ado-md-api/value-property-ado-md.md) свойства.  
  
-   Возвращает строку, содержащую форматированный вывод **значение** свойство с [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) свойство.  
  
-   Возвращает порядковый номер **ячейки** в **Cellset** с [порядковый номер](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) свойство.  
  
-   Определить положение **ячейки** в [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) с [позиций](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) коллекции.  
  
-   Получить другие сведения о **ячейки** с помощью стандартных ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 **Свойства** коллекция содержит свойства, предоставляемые поставщиком. Ниже перечислены свойства, которые могут быть доступны. В списке свойств фактическое может различаться в зависимости от реализации поставщика. См. в документации поставщика более полный список доступных свойств.  
  
|Name|Описание|  
|----------|-----------------|  
|BackColor|Цвет фона, используемый при отображении ячейки.|  
|FontFlags|Битовая шрифта.|  
|FontName|Шрифт, используемый для отображения значения ячейки.|  
|FontSize|Размер шрифта, используемый для отображения значения ячейки.|  
|ForeColor|Цвет переднего плана, используемый при отображении ячейки.|  
|FormatString|Значение в форматированную строку.|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта Axis (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Объект Cellset (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Коллекции Positions (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
