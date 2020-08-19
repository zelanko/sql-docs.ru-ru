---
description: Свойство FormattedValue (многомерные объекты ADO)
title: Свойство FormattedValue (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell::FormattedValue
- FormattedValue
helpviewer_keywords:
- FormattedValue property [ADO MD]
ms.assetid: 5c06451e-06ec-4da6-9a87-2d043469248a
author: rothja
ms.author: jroth
ms.openlocfilehash: 99509ff8d72a8ad5ec587674b6c35f96a674e4db
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441026"
---
# <a name="formattedvalue-property-ado-md"></a>Свойство FormattedValue (многомерные объекты ADO)
Указывает отформатированное отображение значения [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md) .  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строку** и доступна только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **FormattedValue** для получения форматированного отображаемого значения свойства [value](../../../ado/reference/ado-md-api/value-property-ado-md.md) объекта [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md) . Например, если значение ячейки 1056,87, а это значение представляло собой сумму в долларах, **FormattedValue** будет $1 056,87.  
  
## <a name="applies-to"></a>Применение  
 [Объект Cell (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Свойство Value (многомерные объекты ADO)](../../../ado/reference/ado-md-api/value-property-ado-md.md)
