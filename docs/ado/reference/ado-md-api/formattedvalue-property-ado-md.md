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
ms.openlocfilehash: ba8b3469d017b79027670cb4de9f8b3761c8dcc7
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778133"
---
# <a name="formattedvalue-property-ado-md"></a>Свойство FormattedValue (многомерные объекты ADO)
Указывает отформатированное отображение значения [ячейки](./cell-object-ado-md.md) .  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **строку** и доступна только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **FormattedValue** для получения форматированного отображаемого значения свойства [value](./value-property-ado-md.md) объекта [ячейки](./cell-object-ado-md.md) . Например, если значение ячейки 1056,87, а это значение представляло собой сумму в долларах, **FormattedValue** будет $1 056,87.  
  
## <a name="applies-to"></a>Применение  
 [Объект Cell (многомерные объекты ADO)](./cell-object-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Пример набора ячеек (Visual Basic)](./cellset-example-vb.md)   
 [Свойство Value (многомерные объекты ADO)](./value-property-ado-md.md)