---
description: Свойство State (ADO)
title: Свойство State (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: d118ed6d695f8f047640f0ef16c139204ae36277
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988845"
---
# <a name="state-property-ado"></a>Свойство State (ADO)
Указывает для всех применимых объектов, является ли состояние объекта открытым или закрытым. Если объект выполняет асинхронный метод, указывает, является ли текущее состояние объекта подключением, выполнением или извлечением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** , которое может быть значением [обжектстатинум](./objectstateenum.md) . Значение по умолчанию — **адстатеклосед**.  
  
## <a name="remarks"></a>Remarks  
 Свойство **State** можно использовать для определения текущего состояния данного объекта в любое время.  
  
 Свойство **State** объекта может иметь сочетание значений. Например, если выполняется инструкция, это свойство будет иметь объединенное значение **адстатеопен** и **адстатиксекутинг**.  
  
 Свойство **State** доступно только для чтения.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Command (ADO)](./command-object-ado.md)  
        [Объект Connection (ADO)](./connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Record (ADO)](./record-object-ado.md)  
        [Объект Recordset (ADO)](./recordset-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Stream (ADO)](./stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual Basic)](./connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual c++)](./connectionstring-connectiontimeout-and-state-properties-example-vc.md)