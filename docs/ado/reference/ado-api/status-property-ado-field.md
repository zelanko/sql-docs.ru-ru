---
title: Свойство Status (поле ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field::Status
- Field::get_Status
- Field::GetStatus
helpviewer_keywords:
- Status property [ADO Field]
ms.assetid: 8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70baf781839fe9a606f1aed2c26676dffe102d69
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282013"
---
# <a name="status-property-ado-field"></a>Свойство Status (ADO поле)
Указывает состояние [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) значение. Значение по умолчанию — **adFieldOK**.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="record-field-status"></a>Статус поля записи  
 Изменяет значение **поле** объекта в коллекции полей [запись](../../../ado/reference/ado-api/record-object-ado.md) объекта кэшируются до объекта [обновление](../../../ado/reference/ado-api/update-method.md) вызывается метод. В этот момент, если изменение значения поля вызвала ошибку, OLE DB вызывает ошибку **DB_E_ERRORSOCCURRED** (2147749409). Свойство Status любого **поле** объекты в **поля** коллекции, который вызвал ошибку будет находиться в диапазоне от [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) описывающая причину проблема.  
  
 Для повышения производительности, добавление и удаление элементов [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции **запись** объекта кэшируются до **обновление** вызывается метод и затем изменения становятся оптимистического пакетного обновления. Если **обновление** метод не вызван, сервер не обновлен. При сбое любой обновлений, то возвращается ошибка поставщика OLE DB (DB_E_ERRORSOCCURRED) и **состояние** свойство указывает объединенных значений кода состояния операции и ошибки. Например **adFieldPendingInsert adFieldPermissionDenied или**. **Состояние** свойства каждого **поле** можно использовать, чтобы определить, почему **поле** не были добавлены, изменены или удалены.  
  
 Многие типы проблем, возникающих при добавлении, изменении и удалении **поле** передаются через **состояние** свойство. Например, если пользователь удаляет **поле**, она помечается для удаления из **поля** коллекции. Если последующие **обновление** возвращает сообщение об ошибке, поскольку пользователь попытался удалить **поле** для которого у пользователя нет разрешений, **поле** будет иметь  **Состояние** из **adFieldPermissionDenied adFieldPendingDelete или**. Вызов [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод восстанавливает исходные значения и наборы **состояние** для **adFieldOK**.  
  
 Аналогичным образом **обновление** метод может возвращать ошибку, так как новый **поле** был добавлен и задан неверное значение. В этом случае новый **поле** будет находиться в **поля** коллекции и имеют статус **adFieldPendingInsert** и, возможно, **adFieldCantCreate** (в зависимости поставщика). Можно указать соответствующее значение для нового **поле** и вызвать **обновление** еще раз.  
  
## <a name="recordset-field-status"></a>Статус поля набора записей  
 Примет значение **поле** объекта в коллекции полей либо [записей](../../../ado/reference/ado-api/recordset-object-ado.md) кэшируются до объекта [обновление](../../../ado/reference/ado-api/update-method.md) вызывается метод. В этот момент, если изменение значения поля вызвала ошибку, OLE DB вызывает ошибку **DB_E_ERRORSOCCURRED** (2147749409). Свойство Status любого **поле** объекты в **поля** коллекции, который вызвал ошибку будет находиться в диапазоне от [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md) описывающая причину проблема.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства состояния (поле) (Visual Basic)](../../../ado/reference/ado-api/status-property-example-field-vb.md)   
 [Пример свойства Status (Visual C++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
