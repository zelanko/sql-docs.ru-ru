---
title: Удаление метода (объект Recordset ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Delete
- Recordset15::Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 1eb9209c-602c-4507-b0c2-6527a599b67d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 272b953a39a9ccbb01d94acc59d374304bda3ad0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140188"
---
# <a name="delete-method-ado-recordset"></a>Метод Delete (объект Recordset ADO)
Удаляет текущую запись или группу записей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Delete AffectRecords  
```  
  
#### <a name="parameters"></a>Параметры  
 *AffectRecords*  
 [AffectEnum](../../../ado/reference/ado-api/affectenum.md) значение, которое определяет, сколько записей **удалить** повлияет на метод. Значение по умолчанию — **adAffectCurrent**.  
  
> [!NOTE]
>  **adAffectAll** и **adAffectAllChapters** не являются допустимыми аргументами для **удалить**.  
  
## <a name="remarks"></a>Примечания  
 С помощью **удалить** метод помечает текущую запись или группу записей в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект для удаления. Если **записей** объекта не допускает удаление записей, возникает ошибка. Если вы находитесь в режим немедленного обновления, удаления происходит в базе данных немедленно. Если запись не удалось успешно (из-за нарушений целостности базы данных, например), запись будет оставаться в режиме редактирования после вызова [обновления](../../../ado/reference/ado-api/update-method.md). Это означает, что необходимо отменить обновление с помощью [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) перед перемещением текущей записи (например, с помощью [закрыть](../../../ado/reference/ado-api/close-method-ado.md), [переместить](../../../ado/reference/ado-api/move-method-ado.md), или [ NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 Если вы находитесь в пакетный режим обновления, записи, помечаются для удаления из кэша и фактическое удаление происходит при вызове [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод. Используйте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство, чтобы просмотреть удаленные записи.  
  
 Получение значений полей из удаленной записи приводит к ошибке. После удаления текущей записи, удаленная запись остается в текущей до перехода к другой записи. Один раз перемещении из удаленной записи, он больше не доступен.  
  
 Если вы вложить удалений в транзакции, можно выполнить восстановление удаленных записей с [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) метод. Если вы находитесь в пакетный режим обновления, вы можете отменить Ожидается удаление или группой ожидающих удаления с [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) метод.  
  
 Если произошел сбой попытки удаления записей из-за конфликта с базовыми данными (например, запись уже был удален другим пользователем), поставщик возвращает предупреждения, чтобы [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции, но не привела к остановке программы выполнение. Ошибка времени выполнения возникает только в том случае, если есть конфликты запрошенными записями.  
  
 Если [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) динамическое свойство задано и **записей** является результатом выполнения операции СОЕДИНЕНИЯ на несколько таблиц, то **удалить** метод будет удален только строки из таблицы, указанной в [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) свойство.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод пример DELETE (Visual Basic)](../../../ado/reference/ado-api/delete-method-example-vb.md)   
 [Пример метода (VBScript) DELETE](../../../ado/reference/ado-api/delete-method-example-vbscript.md)   
 [Удалить пример метода (Visual C++)](../../../ado/reference/ado-api/delete-method-example-vc.md)   
 [Метод Delete (коллекция Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (коллекция Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
