---
title: "Свойство Status (набора записей ADO) | Документы Microsoft"
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
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 28842b05cf75282252450475372a8955dfd28cbd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="status-property-ado-recordset"></a>Свойство Status (набора записей ADO)
Указывает состояние текущей записи в отношении пакета обновлений или других массовых операций.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает сумму одного или нескольких [RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md) значения.  
  
## <a name="remarks"></a>Замечания  
 Используйте **состояние** свойство, чтобы узнать, какие изменения ожидают для записей изменен во время обновления пакета. Можно также использовать **состояние** свойства для просмотра состояния записи с ошибкой во время массовых операций, например при вызове [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта или набора [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство **набора записей** в массив закладки. Это свойство можно определить, как сбой и его устранению данной записи.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства состояния (записей) (Visual Basic)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Пример свойства состояния (VC ++)](../../../ado/reference/ado-api/status-property-example-vc.md)   

