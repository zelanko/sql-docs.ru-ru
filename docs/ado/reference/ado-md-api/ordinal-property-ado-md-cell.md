---
description: Свойство Ordinal (многомерный объект ADO Cell)
title: Свойство Ordinal (объекты данных ActiveX (MD) ячейка) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 55db23316b4d920154f00aa3b03fb101b2382483
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440816"
---
# <a name="ordinal-property-ado-md-cell"></a>Свойство Ordinal (многомерный объект ADO Cell)
Однозначно определяет [ячейку](../../../ado/reference/ado-md-api/cell-object-ado-md.md) по ее положению в наборе ячеек.  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **длинное** целое число и доступно только для чтения.  
  
## <a name="remarks"></a>Remarks  
 Порядковое значение ячейки однозначно определяет ячейку в наборе ячеек. По сути, ячейки нумеруются в наборе ячеек, как если *бы набор ячеек*был многомерным массивом, где *p* — это число [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md). Нумерация ячеек начинается с нуля в построчном порядке. Ниже приведена формула для вычисления порядкового номера ячейки.  
  
 Порядковое значение ячейки можно использовать со свойством [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) объекта набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) для быстрого извлечения [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md).  
  
## <a name="applies-to"></a>Применение  
 [Объект Cell (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример оси (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Объект набора ячеек (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Свойство Item (объекты данных ActiveX (MD) набор ячеек)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Свойство Ordinal (многомерный объект ADO Position)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)
