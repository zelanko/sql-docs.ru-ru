---
title: Свойство Status (набора записей ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1a3c09b9613c2fe9bd84ea921aef8a3e09a14b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="status-property-ado-recordset"></a>Свойство Status (набора записей ADO)
Указывает состояние текущей записи в отношении пакета обновлений или других массовых операций.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает сумму одного или нескольких [RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md) значения.  
  
## <a name="remarks"></a>Замечания  
 Используйте **состояние** свойство, чтобы узнать, какие изменения ожидают для записей изменен во время обновления пакета. Можно также использовать **состояние** свойства для просмотра состояния записи с ошибкой во время массовых операций, например при вызове [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта или набора [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство **набора записей** в массив закладки. Это свойство можно определить, как сбой и его устранению данной записи.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства состояния (записей) (Visual Basic)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Пример свойства Status (Visual C++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
