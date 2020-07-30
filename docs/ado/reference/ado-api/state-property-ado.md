---
title: Свойство State (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
author: rothja
ms.author: jroth
ms.openlocfilehash: f4fa19bf21764437d3713c434e288b3bb3a3d25d
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242574"
---
# <a name="state-property-ado"></a>Свойство State (ADO)
Указывает для всех применимых объектов, является ли состояние объекта открытым или закрытым. Если объект выполняет асинхронный метод, указывает, является ли текущее состояние объекта подключением, выполнением или извлечением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** , которое может быть значением [обжектстатинум](../../../ado/reference/ado-api/objectstateenum.md) . Значение по умолчанию — **адстатеклосед**.  
  
## <a name="remarks"></a>Remarks  
 Свойство **State** можно использовать для определения текущего состояния данного объекта в любое время.  
  
 Свойство **State** объекта может иметь сочетание значений. Например, если выполняется инструкция, это свойство будет иметь объединенное значение **адстатеопен** и **адстатиксекутинг**.  
  
 Свойство **State** доступно только для чтения.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
        [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
        [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual Basic)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual c++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
