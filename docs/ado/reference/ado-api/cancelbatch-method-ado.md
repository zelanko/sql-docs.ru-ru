---
title: Метод CancelBatch (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 572738c966651e35f2980ea75c3770ddc4bd029d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696179"
---
# <a name="cancelbatch-method-ado"></a>Метод CancelBatch (ADO)
Отменяет ожидающие пакетного обновления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>Параметры  
 *AffectRecords*  
 Необязательный параметр. [AffectEnum](../../../ado/reference/ado-api/affectenum.md) значение, указывающее, сколько записей **CancelBatch** повлияет на метод.  
  
## <a name="remarks"></a>Примечания  
 Используйте **CancelBatch** метод, чтобы отменить все имеющиеся обновления в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) в пакетном режиме обновления. Если **записей** находится в режиме немедленного обновления, вызвав **CancelBatch** без **adAffectCurrent** приводит к ошибке.  
  
 Если вы изменяете текущей записи или при добавлении новой записи, при вызове **CancelBatch**, сначала вызывает ADO [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод, чтобы отменить изменения в кэше. После этого все ожидающие изменения в **записей** будут отменены.  
  
 Текущая запись может быть неопределенной после **CancelBatch** вызвать, особенно в том случае, если были находится в процессе добавления новой записи. По этой причине лучше задать положение текущей записи в известном месте в **записей** после **CancelBatch** вызова. Например, вызвать [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) метод.  
  
 Если произошел сбой попытки отменить ожидающие изменения из-за конфликта с базовыми данными (например, если запись была удалена другим пользователем), поставщик возвращает предупреждения, чтобы [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции, но не останавливается выполнение программы. Ошибка времени выполнения возникает только в том случае, если есть конфликты запрошенными записями. Используйте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство (**adFilterAffectedRecords**) и [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойства для поиска записей с конфликтами.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов UpdateBatch и Cancelbatch по методы (Visual Basic)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch и Cancelbatch методы (Visual C++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод Cancel (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Метод Cancel (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод CancelUpdate (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
