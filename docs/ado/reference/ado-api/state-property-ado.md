---
title: Состоянии свойство (ADO) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e8a46dd9358b085fb6079f03df88474b72440068
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711256"
---
# <a name="state-property-ado"></a>Свойство State (ADO)
Указывает для всех объектов, применимо ли состояние объекта открытым или закрытым. Если объект выполняется асинхронный метод, указывает ли текущее состояние объекта подключение, выполнение или извлечения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Long** значение, которое может быть [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) значение. Значение по умолчанию — **adStateClosed**.  
  
## <a name="remarks"></a>Примечания  
 Можно использовать **состояние** свойства, чтобы определить текущее состояние данного объекта в любое время.  
  
 Объекта **состояние** свойство может иметь сочетания значений. Например, если инструкция выполняется, это свойство будет иметь общее значение **adStateOpen** и **adStateExecuting**.  
  
 **Состояние** свойство доступно только для чтения.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>См. также  
 [Пример свойства состояния (Visual Basic), ConnectionString и ConnectionTimeout](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout и пример свойства состояния (Visual C++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
