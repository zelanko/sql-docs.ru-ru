---
title: Объект Cell (объекты данных ActiveX (MD)) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947749"
---
# <a name="cell-object-ado-md"></a>Объект Cell (многомерные объекты ADO)
Представляет данные на пересечении координат осей, содержащихся в наборе ячеек.  
  
## <a name="remarks"></a>Remarks  
 Объект **ячейки** возвращается свойством [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) объекта набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) .  
  
 С помощью коллекций и свойств объекта **ячейки** можно выполнять следующие действия.  
  
-   Возврат данных в **ячейке** со свойством [value](../../../ado/reference/ado-md-api/value-property-ado-md.md) .  
  
-   Возвращает строку, представляющую отформатированный вывод свойства **value** со свойством [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) .  
  
-   Возврат порядкового значения **ячейки** в наборе **ячеек** с помощью свойства [Ordinal](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) .  
  
-   Определите позицию **ячейки** в [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) с коллекцией [Positions](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) .  
  
-   Получите другие сведения о **ячейке** со стандартной коллекцией [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO.  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|Имя|Description|  
|----------|-----------------|  
|BackColor|Цвет фона, используемый при отображении ячейки.|  
|FontFlags|Битовая маска, определяющая влияние на шрифт.|  
|FontName|Шрифт, используемый для вывода значения ячейки.|  
|FontSize|Размер шрифта, используемый для вывода значения ячейки.|  
|ForeColor|Цвет переднего плана, используемый при отображении ячейки.|  
|FormatString|Значение в форматированной строке.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример оси (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Объект набора ячеек (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Коллекция Positions (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
