---
title: Метод CancelUpdate (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CancelUpdate
helpviewer_keywords:
- CancelUpdate method [ADO]
ms.assetid: eaa856cc-c786-462e-890c-c896261b1741
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b53fa2e9d69b39218d846b57070b78ae230d81cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698813"
---
# <a name="cancelupdate-method-ado"></a>Метод CancelUpdate (ADO)
Отменяет все изменения, внесенные в текущей или новой строки [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, или [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md) объект перед вызовом [обновления ](../../../ado/reference/ado-api/update-method.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Примечания  
  
## <a name="recordset"></a>набор записей  
 Используйте **CancelUpdate** методу, чтобы отменить любые изменения, внесенные в текущую строку или отменить вновь добавленной строкой. Не удается отменить изменения для текущей строки или строки, после вызова метода **обновление** метод, если изменения являются частью транзакции, можно выполнить откат с [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) метода или часть из пакетного обновления. В случае пакетного обновления, вы можете отменить **обновление** с **CancelUpdate** или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) метод.  
  
 При добавлении новой строки при вызове **CancelUpdate** метод, текущая строка становится строка, которая была текущей до [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) вызова.  
  
 Если вы перейдете в режим редактирования и хотите отказаться от использования текущей записи (например, с помощью [переместить](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), или [закрыть](../../../ado/reference/ado-api/close-method-ado.md) методы), можно использовать  **CancelUpdate** отменить все ожидающие изменения. Может потребоваться сделать, если обновления не могут быть зарегистрированы успешно к источнику данных. Например, попытка удалить оставит что завершается сбоем из-за нарушений целостности **записей** в режиме редактирования после вызова [удалить](../../../ado/reference/ado-api/delete-method-ado-recordset.md).  
  
## <a name="record"></a>Записей  
 **CancelUpdate** метод отменяет все ожидающие Вставка и удаление [поле](../../../ado/reference/ado-api/field-object.md) объектов и отменяет ожидающие обновления существующих полей и восстанавливает их к исходным значениям. [Состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойства всех полей в **поля** коллекции имеет значение **adFieldOK**.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Обновление методов и Cancelupdate (Visual Basic)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Обновление методов и Cancelupdate (Visual C++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [Метод AddNew (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Метод Cancel (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Метод Cancel (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод CancelUpdate (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Свойство EditMode](../../../ado/reference/ado-api/editmode-property.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
