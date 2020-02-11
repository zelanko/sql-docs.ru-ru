---
title: EditMode, свойство | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::EditMode
helpviewer_keywords:
- EditMode property
ms.assetid: a1b04bb2-8c8b-47f9-8477-bfd0368b6f68
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0ffc6fb258799b0ab0bb03e7acbd922f6a67d1f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918980"
---
# <a name="editmode-property"></a>Свойство EditMode
Указывает состояние редактирования текущей записи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение [едитмодинум](../../../ado/reference/ado-api/editmodeenum.md) .  
  
## <a name="remarks"></a>Remarks  
 ADO поддерживает буфер редактирования, связанный с текущей записью. Это свойство указывает, были ли внесены изменения в этот буфер или создана ли новая запись. Чтобы определить состояние редактирования текущей записи, используйте свойство **EditMode** . Вы можете проверить наличие ожидающих изменений в случае, если процесс редактирования был прерван, и определить, нужно ли использовать метод [Update](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) .  
  
 В *режиме немедленного обновления* свойство **EditMode** сбрасывается в **адедитноне** после вызова успешного вызова метода **Update** . Если при вызове [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md) не удается удалить записи или записи в источнике данных (например, из-за нарушений ссылочной целостности), [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) остается в режиме редактирования (**EditMode** = **адедитинпрогресс**). Поэтому **CancelUpdate** должен вызываться перед переходом от текущей записи (например, с [Move](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)или [Close](../../../ado/reference/ado-api/close-method-ado.md) ).  
  
 В *режиме пакетного обновления* (в котором поставщик кэширует несколько изменений и записывает их в базовый источник данных только при вызове метода [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) ) значение свойства **EditMode** изменяется при выполнении первой операции и не сбрасывается при вызове метода **Update** . Последующие операции не изменяют значение свойства **EditMode** , даже если выполняются различные операции. Например, если первая операция заключается в добавлении новой записи, а вторая вносит изменения в существующую запись, свойство **EditMode** по-прежнему будет **адедитадд**. Свойство **EditMode** не сбрасывается в **Адедитноне** до вызова **UpdateBatch**. Чтобы определить, какие операции были выполнены, присвойте свойству [Filter](../../../ado/reference/ado-api/filter-property.md) значение [адфилтерпендинг](../../../ado/reference/ado-api/filtergroupenum.md) , чтобы были видны только записи с ожидающими изменениями, и проверьте свойство [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) каждой записи, чтобы определить, какие изменения были внесены в данные.  
  
> [!NOTE]
>  **EditMode** может возвращать допустимое значение только при наличии текущей записи. **EditMode** вернет ошибку, если [BOF или EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет значение true, или если текущая запись была удалена.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств примеры CursorType, LockType и EditMode (Visual Basic)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Пример свойств примеры CursorType, LockType и EditMode (Visual c++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Метод AddNew (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Метод Delete (набор записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
