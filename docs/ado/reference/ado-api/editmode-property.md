---
title: Свойство EditMode | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 147528e9400d6befe9d5cb3c5d3cc3f882e48ad0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735962"
---
# <a name="editmode-property"></a>Свойство EditMode
Указывает состояние редактирования текущей записи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) значение.  
  
## <a name="remarks"></a>Примечания  
 ADO поддерживает редактирования буфер, связанный с текущей записи. Это свойство указывает ли были внесены изменения для данного буфера или ли создана новая запись. Используйте **EditMode** свойство, чтобы определить состояние редактирования текущей записи. Можно проверить для ожидающих изменений, если процесс редактирования был прерван и определить, нужно ли использовать [обновление](../../../ado/reference/ado-api/update-method.md) или [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод.  
  
 В *режим немедленного обновления* **EditMode** свойство сбрасывается до **как таковые** после успешного вызова **обновление** вызывается метод . При вызове [удалить](../../../ado/reference/ado-api/delete-method-ado-recordset.md) не удаляет успешно одной или нескольких записей в источнике данных (например, из-за нарушения ссылочной целостности), [записей](../../../ado/reference/ado-api/recordset-object-ado.md) остается в режиме правки (**EditMode** = **adEditInProgress**). Таким образом **CancelUpdate** должен вызываться перед перемещением текущей записи (например с помощью [переместить](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), или [закрыть](../../../ado/reference/ado-api/close-method-ado.md) ).  
  
 В *пакетный режим обновления* (в котором поставщик кэширует несколько изменений и записывает их в базовом источнике данных только в том случае, когда вы вызываете [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод), значение **EditMode**  свойство изменяется в том случае, если первая операция выполняется, и он не сбрасывается, путем вызова **обновления** метод. Последующие операции не изменяйте значение **EditMode** свойства, даже в том случае, если выполняются различные операции. Например, если первая операция для добавления новой записи, а второй вносит изменения в существующую запись, свойство **EditMode** по-прежнему будут **adEditAdd**. **EditMode** свойство не сбрасывается до **как таковые** до и после вызова **UpdateBatch**. Чтобы определить, какие операции были выполнены, задайте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойства [adFilterPending](../../../ado/reference/ado-api/filtergroupenum.md) , чтобы только записи с ожидающими изменениями будут отображаться и изучите [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойство каждой записи, чтобы определить, какие изменения были внесены в данные.  
  
> [!NOTE]
>  **EditMode** может возвращать допустимое значение только в том случае, если имеется текущей записи. **EditMode** возвратит ошибку, если [BOF и EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет значение true, или если текущая запись была удалена.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры CursorType, LockType и EditMode по свойства (Visual Basic)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Примеры CursorType, LockType и EditMode пример свойства (Visual C++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Метод AddNew (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Удаление метода (объект Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
