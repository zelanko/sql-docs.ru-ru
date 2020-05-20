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
ms.openlocfilehash: 68a0e6fe0c595a79447cbf79155914606415df89
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759760"
---
# <a name="state-property-ado"></a>Свойство State (ADO)
Указывает для всех применимых объектов, является ли состояние объекта открытым или закрытым. Если объект выполняет асинхронный метод, указывает, является ли текущее состояние объекта подключением, выполнением или извлечением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** , которое может быть значением [обжектстатинум](../../../ado/reference/ado-api/objectstateenum.md) . Значение по умолчанию — **адстатеклосед**.  
  
## <a name="remarks"></a>Примечания  
 Свойство **State** можно использовать для определения текущего состояния данного объекта в любое время.  
  
 Свойство **State** объекта может иметь сочетание значений. Например, если выполняется инструкция, это свойство будет иметь объединенное значение **адстатеопен** и **адстатиксекутинг**.  
  
 Свойство **State** доступно только для чтения.  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>См. также  
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual Basic)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Пример свойств ConnectionString, ConnectionTimeout и State (Visual c++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
