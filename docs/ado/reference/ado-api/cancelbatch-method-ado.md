---
description: Метод CancelBatch (ADO)
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
ms.openlocfilehash: db1ae959094c07ea44e7e236e540070bea7814e5
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776313"
---
# <a name="cancelbatch-method-ado"></a>Метод CancelBatch (ADO)
Отменяет ожидающее пакетное обновление.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>Параметры  
 *аффектрекордс*  
 Необязательный элемент. Значение [аффектенум](./affectenum.md) , указывающее, сколько записей будет влиять на метод **CancelBatch** .  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **CancelBatch** , чтобы отменить все ожидающие обновления в [наборе записей](./recordset-object-ado.md) в режиме пакетного обновления. Если **набор записей** находится в режиме немедленного обновления, вызов **CancelBatch** без **адаффекткуррент** выдает ошибку.  
  
 Если редактируется текущая запись или добавляется новая запись при вызове **CancelBatch**, то ADO сначала вызывает метод [CancelUpdate](./cancelupdate-method-ado.md) для отмены любых кэшированных изменений. После этого все ожидающие изменения в **наборе записей** будут отменены.  
  
 Текущая запись может быть недетерминированной после вызова **CancelBatch** , особенно если вы находились в процессе добавления новой записи. По этой причине лучше установить текущую позицию записи в известное место в **наборе записей** после вызова **CancelBatch** . Например, вызовите метод [MoveFirst](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) .  
  
 Если попытка отмены ожидающих обновлений завершается сбоем из-за конфликта с базовыми данными (например, если запись была удалена другим пользователем), поставщик возвращает предупреждения в коллекцию [ошибок](./errors-collection-ado.md) , но не останавливает выполнение программы. Ошибка времени выполнения возникает только в случае возникновения конфликтов во всех запрошенных записях. Используйте свойство [Filter](./filter-property.md) (**адфилтераффектедрекордс**) и свойство [Status](./status-property-ado-recordset.md) для обнаружения записей с конфликтами.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов UpdateBatch и CancelBatch (Visual Basic)](./updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Примеры методов UpdateBatch и CancelBatch (Visual c++)](./updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод Cancel (ADO)](./cancel-method-ado.md)   
 [Метод Cancel (RDS)](../rds-api/cancel-method-rds.md)   
 [Метод CancelUpdate (ADO)](./cancelupdate-method-ado.md)   
 [Метод CancelUpdate (RDS)](../rds-api/cancelupdate-method-rds.md)   
 [Метод Clear (ADO)](./clear-method-ado.md)   
 [Свойство LockType (ADO)](./locktype-property-ado.md)   
 [Метод UpdateBatch](./updatebatch-method.md)