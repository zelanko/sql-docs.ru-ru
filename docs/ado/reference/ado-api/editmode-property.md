---
title: "Свойство EditMode | Документы Microsoft"
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
- Recordset15::EditMode
helpviewer_keywords:
- EditMode property
ms.assetid: a1b04bb2-8c8b-47f9-8477-bfd0368b6f68
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: be4670f359212f1079044341285ec2b0aff6c559
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="editmode-property"></a>Свойство EditMode
Указывает состояние редактирования текущей записи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) значение.  
  
## <a name="remarks"></a>Замечания  
 ADO поддерживает редактирования буфера, связанное с текущей записью. Это свойство указывает ли были внесены изменения в этот буфер или ли создана новая запись. Используйте **EditMode** свойства, чтобы определить состояние редактирования текущей записи. Можно проверить для ожидающих изменений, если был прерван процесс редактирования и определить, следует ли использовать [обновление](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод.  
  
 В *режим немедленного обновления* **EditMode** свойства сбрасывается до **как таковые** после успешного вызова **обновление** вызывается метод . При вызове [удаление](../../../ado/reference/ado-api/delete-method-ado-recordset.md) не удаляет успешно записи или записи в источнике данных (например, из-за нарушения ссылочной целостности), [записей](../../../ado/reference/ado-api/recordset-object-ado.md) остается в режиме редактирования (**EditMode** = **adEditInProgress**). Таким образом **CancelUpdate** должен вызываться перед перемещением текущей записи (например, с [переместить](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), или [закрыть](../../../ado/reference/ado-api/close-method-ado.md) ).  
  
 В *пакетный режим обновления* (в котором поставщик кэширует внесение нескольких изменений и записывает их в базовом источнике данных только при вызове [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод), значение **EditMode**  свойство изменяется, когда выполняется первой операции и не сбрасывается при вызове **обновление** метод. Последующие операции, не изменяйте значение **EditMode** свойства, даже если выполняются различные операции. Например, если первой операции для добавления новой записи, а второй вносит изменения в существующую запись, свойство **EditMode** по-прежнему будут **adEditAdd**. **EditMode** не сбрасывается свойство **как таковые** до и после вызова **UpdateBatch**. Чтобы определить, какие операции выполнены, задайте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойства [adFilterPending](../../../ado/reference/ado-api/filtergroupenum.md) , чтобы только записей с ожидающими изменениями будут отображаться и проверить [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойства каждой записи, чтобы определить, какие изменения были внесены в данные.  
  
> [!NOTE]
>  **EditMode** может возвращать допустимое значение только в том случае, если текущая запись. **EditMode** вернет ошибку, если [BOF или EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет значение true, или если текущая запись была удалена.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [CursorType LockType и пример EditMode свойства (Visual Basic)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType LockType и пример использования свойств EditMode (VC ++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Метод AddNew (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Удаление метода (набора записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод обновления](../../../ado/reference/ado-api/update-method.md)

