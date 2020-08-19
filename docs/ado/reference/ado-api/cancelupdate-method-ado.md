---
description: Метод CancelUpdate (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6482336ceed00e131da38b151a8b6ffe33b3638c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451026"
---
# <a name="cancelupdate-method-ado"></a>Метод CancelUpdate (ADO)
Отменяет все изменения, внесенные в текущую или новую строку объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , или коллекцию [полей](../../../ado/reference/ado-api/fields-collection-ado.md) объекта [Record](../../../ado/reference/ado-api/record-object-ado.md) перед вызовом метода [Update](../../../ado/reference/ado-api/update-method.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Remarks  
  
## <a name="recordset"></a>набор записей  
 Используйте метод **CancelUpdate** для отмены всех изменений, внесенных в текущую строку, или для удаления вновь добавленной строки. Нельзя отменить изменения текущей строки или новой строки после вызова метода **Update** , если только изменения не являются частью транзакции, которую можно откатить методом [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) или частью пакетного обновления. В случае пакетного обновления можно отменить **Обновление** с помощью метода **CancelUpdate** или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) .  
  
 При добавлении новой строки при вызове метода **CancelUpdate** текущая строка преобразуется в текущую строку до вызова [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) .  
  
 Если вы используете режим редактирования и хотите переместить текущую запись (например, с помощью методов [Move](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)или [Close](../../../ado/reference/ado-api/close-method-ado.md) ), можно использовать **CancelUpdate** для отмены всех ожидающих изменений. Это может потребоваться, если обновление не удается успешно опубликовать в источнике данных. Например, попытка удаления, которая завершилась сбоем из-за нарушений ссылочной целостности, оставляет **набор записей** в режиме редактирования после вызова метода [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md).  
  
## <a name="record"></a>Записей  
 Метод **CancelUpdate** отменяет все ожидающие вставки или удаления объектов [полей](../../../ado/reference/ado-api/field-object.md) и отменяет отложенные обновления существующих полей и восстанавливает их исходные значения. Свойство [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) всех полей в коллекции **Fields** имеет значение **адфиелдок**.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Примеры методов Update и CancelUpdate (Visual Basic)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Примеры методов Update и CancelUpdate (Visual c++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [Метод AddNew (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Метод Cancel (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Метод Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [EditMode, свойство](../../../ado/reference/ado-api/editmode-property.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
