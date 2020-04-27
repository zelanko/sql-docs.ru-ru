---
title: Метод Delete (набор записей ADO) | Документация Майкрософт
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
ms.openlocfilehash: b978e3d885e3ff06dda18859384f88eb4c564254
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919121"
---
# <a name="delete-method-ado-recordset"></a>Метод Delete (объект Recordset ADO)
Удаляет текущую запись или группу записей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Delete AffectRecords  
```  
  
#### <a name="parameters"></a>Параметры  
 *аффектрекордс*  
 Значение [аффектенум](../../../ado/reference/ado-api/affectenum.md) , определяющее, сколько записей будет влиять на метод **Delete** . Значение по умолчанию — **адаффекткуррент**.  
  
> [!NOTE]
>  **адаффекталл** и **адаффекталлчаптерс** не являются допустимыми аргументами для **удаления**.  
  
## <a name="remarks"></a>Remarks  
 Использование метода **Delete** помечает текущую запись или группу записей в объекте [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) для удаления. Если объект **набора записей** не допускает удаления записей, возникает ошибка. Если вы используете режим немедленного обновления, немедленное удаление происходит в базе данных. Если запись не может быть успешно удалена (например, из-за нарушений целостности базы данных), после вызова метода [Update](../../../ado/reference/ado-api/update-method.md)запись остается в режиме редактирования. Это означает, что необходимо отменить обновление с помощью [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) , прежде чем перемещаться по текущей записи (например, с помощью [закрытия](../../../ado/reference/ado-api/close-method-ado.md), [перемещения](../../../ado/reference/ado-api/move-method-ado.md)или [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 Если вы используете режим пакетного обновления, записи помечаются для удаления из кэша, а фактическое удаление происходит при вызове метода [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) . Используйте свойство [Filter](../../../ado/reference/ado-api/filter-property.md) для просмотра удаленных записей.  
  
 Получение значений полей из удаленной записи приводит к ошибке. После удаления текущей записи удаленная запись остается текущей до тех пор, пока вы не перейдете к другой записи. После выхода из удаленной записи она становится недоступной.  
  
 При вложении операций удаления в транзакцию удаленные записи можно восстановить с помощью метода [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) . В режиме пакетного обновления можно отменить ожидающее удаление или группу ожидающих удалений с помощью метода [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) .  
  
 Если попытка удаления записей завершается сбоем из-за конфликта с базовыми данными (например, запись уже удалена другим пользователем), поставщик возвращает предупреждения в коллекцию [ошибок](../../../ado/reference/ado-api/errors-collection-ado.md) , но не останавливает выполнение программы. Ошибка времени выполнения возникает только в случае возникновения конфликтов во всех запрошенных записях.  
  
 Если задано динамическое свойство [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) , а **набор записей** является результатом выполнения операции объединения нескольких таблиц, то метод **Delete** удаляет только строки из таблицы с именем в свойстве [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Delete (Visual Basic)](../../../ado/reference/ado-api/delete-method-example-vb.md)   
 [Пример метода Delete (VBScript)](../../../ado/reference/ado-api/delete-method-example-vbscript.md)   
 [Пример метода Delete (Visual c++)](../../../ado/reference/ado-api/delete-method-example-vc.md)   
 [Метод Delete (коллекция полей ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Метод Delete (Коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Метод DeleteRecord (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
