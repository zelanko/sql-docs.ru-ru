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
author: rothja
ms.author: jroth
ms.openlocfilehash: c2e9f3b57137b4c113b9e177e9fecefec4070ac0
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763175"
---
# <a name="cancelbatch-method-ado"></a>Метод CancelBatch (ADO)
Отменяет ожидающее пакетное обновление.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>Параметры  
 *аффектрекордс*  
 Необязательный элемент. Значение [аффектенум](../../../ado/reference/ado-api/affectenum.md) , указывающее, сколько записей будет влиять на метод **CancelBatch** .  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **CancelBatch** , чтобы отменить все ожидающие обновления в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md) в режиме пакетного обновления. Если **набор записей** находится в режиме немедленного обновления, вызов **CancelBatch** без **адаффекткуррент** выдает ошибку.  
  
 Если редактируется текущая запись или добавляется новая запись при вызове **CancelBatch**, то ADO сначала вызывает метод [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) для отмены любых кэшированных изменений. После этого все ожидающие изменения в **наборе записей** будут отменены.  
  
 Текущая запись может быть недетерминированной после вызова **CancelBatch** , особенно если вы находились в процессе добавления новой записи. По этой причине лучше установить текущую позицию записи в известное место в **наборе записей** после вызова **CancelBatch** . Например, вызовите метод [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) .  
  
 Если попытка отмены ожидающих обновлений завершается сбоем из-за конфликта с базовыми данными (например, если запись была удалена другим пользователем), поставщик возвращает предупреждения в коллекцию [ошибок](../../../ado/reference/ado-api/errors-collection-ado.md) , но не останавливает выполнение программы. Ошибка времени выполнения возникает только в случае возникновения конфликтов во всех запрошенных записях. Используйте свойство [Filter](../../../ado/reference/ado-api/filter-property.md) (**адфилтераффектедрекордс**) и свойство [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) для обнаружения записей с конфликтами.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов UpdateBatch и CancelBatch (Visual Basic)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Примеры методов UpdateBatch и CancelBatch (Visual c++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод Cancel (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Метод Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
