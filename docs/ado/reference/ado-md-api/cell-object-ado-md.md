---
description: Объект Cell (многомерные объекты ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 28058d792b0525aafe8850158a71afcc4423b38f
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778333"
---
# <a name="cell-object-ado-md"></a>Объект Cell (многомерные объекты ADO)
Представляет данные на пересечении координат осей, содержащихся в наборе ячеек.  
  
## <a name="remarks"></a>Remarks  
 Объект **ячейки** возвращается свойством [Item](./item-property-ado-md-cellset.md) объекта набора [ячеек](./cellset-object-ado-md.md) .  
  
 С помощью коллекций и свойств объекта **ячейки** можно выполнять следующие действия.  
  
-   Возврат данных в **ячейке** со свойством [value](./value-property-ado-md.md) .  
  
-   Возвращает строку, представляющую отформатированный вывод свойства **value** со свойством [FormattedValue](./formattedvalue-property-ado-md.md) .  
  
-   Возврат порядкового значения **ячейки** в наборе **ячеек** с помощью свойства [Ordinal](./ordinal-property-ado-md-cell.md) .  
  
-   Определите позицию **ячейки** в [CubeDef](./cubedef-object-ado-md.md) с коллекцией [Positions](./positions-collection-ado-md.md) .  
  
-   Получите другие сведения о **ячейке** со стандартной коллекцией [свойств](../ado-api/properties-collection-ado.md) ADO.  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|Название|Описание:|  
|----------|-----------------|  
|BackColor|Цвет фона, используемый при отображении ячейки.|  
|FontFlags|Битовая маска, определяющая влияние на шрифт.|  
|FontName|Шрифт, используемый для вывода значения ячейки.|  
|FontSize|Размер шрифта, используемый для вывода значения ячейки.|  
|ForeColor|Цвет переднего плана, используемый при отображении ячейки.|  
|FormatString|Значение в форматированной строке.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](./cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример оси (VBScript)](./axis-example-vbscript.md)   
 [Объект набора ячеек (объекты данных ActiveX (MD))](./cellset-object-ado-md.md)   
 [Коллекция Positions (объекты данных ActiveX (MD))](./positions-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../ado-api/properties-collection-ado.md)