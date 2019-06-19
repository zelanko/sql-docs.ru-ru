---
title: Свойство Ordinal (Многомерный объект ADO Cell) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c4a40c59ad222c943cefe089ffaddd53f2cec25a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708813"
---
# <a name="ordinal-property-ado-md-cell"></a>Свойство Ordinal (многомерный объект ADO Cell)
Уникально идентифицирует [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md) по его положению в наборе ячеек.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **Long** целое число и доступен только для чтения.  
  
## <a name="remarks"></a>Примечания  
 Значение порядкового номера ячейки уникально определена ячейка внутри набора ячеек. По существу, ячейки нумеруются в наборе ячеек, как если бы был в наборе ячеек *p*-мерный массив, где *p* число [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md). Ячейки нумеруются, начиная с нуля в строкам. Вот формула для вычисления порядкового номера ячейки:  
  
 Значение порядкового номера ячейки может использоваться с [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство [набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта для быстрого извлечения [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Cell (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта Axis (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Объект Cellset (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Свойство Item (Многомерный объект ADO Cellset)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Свойство Ordinal (многомерный объект ADO Position)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)
