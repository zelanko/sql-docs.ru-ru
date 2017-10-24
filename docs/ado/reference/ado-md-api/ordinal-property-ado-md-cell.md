---
title: "Порядковый номер свойства (ADO MD ячейка) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b6928eeeb7450b2edbd244d70d3c6a8aa999343a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="ordinal-property-ado-md-cell"></a>Порядковый номер свойства (ADO MD ячейка)
Уникально идентифицирует [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md) по его положению в наборе ячеек.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинные** целое число со знаком и доступно только для чтения.  
  
## <a name="remarks"></a>Замечания  
 Порядковый номер ячейки уникально определена ячейка внутри набора ячеек. По существу, ячейки нумеруются в наборе ячеек так, будто набора ячеек *p*-мерный массив, где *p* число [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md). Ячейки нумеруются, начиная с нуля в строках заказа. Вот формула для вычисления порядкового номера ячейки.  
  
 Порядковый номер ячейки, которые можно использовать с [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта для быстрого извлечения [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект ячейки (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример оси (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Объект набора ячеек (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Свойство Item (ячеек ADO MD)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Порядковый номер свойства (позиция ADO MD)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)

