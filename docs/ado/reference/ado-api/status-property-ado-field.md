---
title: Свойство Status (объект Field ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field::Status
- Field::get_Status
- Field::GetStatus
helpviewer_keywords:
- Status property [ADO Field]
ms.assetid: 8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a647051e7953d6f2977074feda94cf7e9f3d9d82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711013"
---
# <a name="status-property-ado-field"></a>Свойство Status (объект Field ADO)
Указывает состояние [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) значение. Значение по умолчанию — **adFieldOK**.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="record-field-status"></a>Статус поля записи  
 Изменяет значение **поле** объекта в коллекции полей [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта кэшируются до объекта [обновления](../../../ado/reference/ado-api/update-method.md) вызывается метод. В таком случае, если изменение значения поля вызвала ошибку, OLE DB вызывает ошибку **DB_E_ERRORSOCCURRED** (2147749409). Свойство Status любого из **поле** объекты в **поля** коллекции, которая вызвала ошибку будет находиться в диапазоне от [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) описывающая причину проблема.  
  
 Для повышения производительности, добавление и удаление элементов [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции **записи** объекта кэшируются до **обновления** вызывается метод и затем изменения было сделано в оптимистичный пакетного обновления. Если **обновления** метод не вызывается, сервер не обновлен. Если все обновления, то не будет возвращена ошибка (DB_E_ERRORSOCCURRED) поставщика OLE DB и **состояние** свойство указывает объединенных значений кода состояния операции и ошибке. Например **adFieldPendingInsert OR adFieldPermissionDenied**. **Состояние** для каждой **поле** можно использовать, чтобы определить, почему **поле** не были добавлены, изменены или удалены.  
  
 Множество типов проблем, возникающих при добавлении, изменении и удалении **поле** передаются через **состояние** свойство. Например, если пользователь удаляет **поле**, она помечена для удаления из **поля** коллекции. Если последующий **обновление** возвращает сообщение об ошибке, поскольку пользователь попытался удалить **поле** для которого у них нет разрешений, **поле** будет иметь  **Состояние** из **adFieldPermissionDenied OR adFieldPendingDelete**. Вызов [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод восстанавливает исходные значения и наборы **состояние** для **adFieldOK**.  
  
 Аналогичным образом **обновление** метод может вернуть ошибку, так как новый **поле** был добавлен и задан неверное значение. В этом случае новый **поле** будет находиться в **поля** коллекции и имеют статус **adFieldPendingInsert** и, возможно, **adFieldCantCreate** (в зависимости от поставщика). Можно указать соответствующее значение для нового **поле** и вызвать **обновления** еще раз.  
  
## <a name="recordset-field-status"></a>Статус поля набора записей  
 Изменяет значение **поля** объекта в коллекции полей либо [записей](../../../ado/reference/ado-api/recordset-object-ado.md) кэшируются до объекта [обновления](../../../ado/reference/ado-api/update-method.md) вызывается метод. В таком случае, если изменение значения поля вызвала ошибку, OLE DB вызывает ошибку **DB_E_ERRORSOCCURRED** (2147749409). Свойство Status любого из **поле** объекты в **поля** коллекции, которая вызвала ошибку будет находиться в диапазоне от [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) описывающая причину проблема.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Status (объект Field) (Visual Basic)](../../../ado/reference/ado-api/status-property-example-field-vb.md)   
 [Пример свойства Status (Visual C++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
