---
title: Удаление метода (набора записей ADO) | Документы Microsoft
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
- Recordset15::raw_Delete
- Recordset15::Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 1eb9209c-602c-4507-b0c2-6527a599b67d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d46ae9982b7675615ffc27321871ac94b67388e6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="delete-method-ado-recordset"></a>Удаление метода (набора записей ADO)
Удаление текущей записи или группы записей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Delete AffectRecords  
```  
  
#### <a name="parameters"></a>Параметры  
 *AffectRecords*  
 [AffectEnum](../../../ado/reference/ado-api/affectenum.md) значение, которое определяет, сколько записей **удалить** повлияет на метод. Значение по умолчанию — **adAffectCurrent**.  
  
> [!NOTE]
>  **adAffectAll** и **adAffectAllChapters** не являются допустимыми аргументами для **удалить**.  
  
## <a name="remarks"></a>Замечания  
 С помощью **удаление** метод помечает текущей записи или группы записей в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект для удаления. Если **записей** объекта не допускает удаление записей происходит ошибка. Если вы находитесь в режим немедленного обновления, удаления происходит в базе данных немедленно. Если запись не может успешно удалены (из-за нарушения целостности базы данных, например), запись будет оставаться в режиме редактирования после вызова [обновление](../../../ado/reference/ado-api/update-method.md). Это означает, что необходимо отменить обновление с [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) перед перемещением текущей записи (например, с помощью [закрыть](../../../ado/reference/ado-api/close-method-ado.md), [переместить](../../../ado/reference/ado-api/move-method-ado.md), или [ NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 При работе в пакетном режиме обновления записи, помечаются для удаления из кэша и фактическое удаление происходит при вызове [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод. Используйте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство, чтобы просмотреть список удаленных записей.  
  
 Получение значения полей из удаленной записи приводит к ошибке. После удаления текущей записи, удаленная запись остается в текущей до перехода к другой записи. Один раз перемещении из удаленной записи, он больше не доступен.  
  
 При вложении удалений в транзакции можно восстановить удаленные записи с [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) метод. Если вы находитесь в пакетный режим обновления, можно отменить Ожидается удаление или группой ожидающих удаления с [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) метод.  
  
 Если происходит сбой попытки удалить записи из-за конфликта с базовыми данными (например, запись уже был удален другим пользователем), поставщик возвращает предупреждения, чтобы [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции, но не остановки программы выполнение. Ошибка во время выполнения возникает только в том случае, если запрошенными записями конфликтуют.  
  
 Если [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) динамическое свойство задано и **записей** является результатом выполнения операции СОЕДИНЕНИЯ на несколько таблиц, то **удалить** метод будет удален только строки из таблицы, указанной в [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) свойство.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Удаление примера метод (Visual Basic)](../../../ado/reference/ado-api/delete-method-example-vb.md)   
 [Удалить пример метода (VBScript)](../../../ado/reference/ado-api/delete-method-example-vbscript.md)   
 [Удалить пример метода (VC ++)](../../../ado/reference/ado-api/delete-method-example-vc.md)   
 [Метод Delete (ADO поля коллекции)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
