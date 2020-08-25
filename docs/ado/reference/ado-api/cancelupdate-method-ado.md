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
ms.openlocfilehash: 9e845757f510c6e81260fbd735fd1e1c05ac87fb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776293"
---
# <a name="cancelupdate-method-ado"></a>Метод CancelUpdate (ADO)
Отменяет все изменения, внесенные в текущую или новую строку объекта [набора записей](./recordset-object-ado.md) , или коллекцию [полей](./fields-collection-ado.md) объекта [Record](./record-object-ado.md) перед вызовом метода [Update](./update-method.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Remarks  
  
## <a name="recordset"></a>набор записей  
 Используйте метод **CancelUpdate** для отмены всех изменений, внесенных в текущую строку, или для удаления вновь добавленной строки. Нельзя отменить изменения текущей строки или новой строки после вызова метода **Update** , если только изменения не являются частью транзакции, которую можно откатить методом [RollbackTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md) или частью пакетного обновления. В случае пакетного обновления можно отменить **Обновление** с помощью метода **CancelUpdate** или [CancelBatch](./cancelbatch-method-ado.md) .  
  
 При добавлении новой строки при вызове метода **CancelUpdate** текущая строка преобразуется в текущую строку до вызова [AddNew](./addnew-method-ado.md) .  
  
 Если вы используете режим редактирования и хотите переместить текущую запись (например, с помощью методов [Move](./move-method-ado.md), [NextRecordset](./nextrecordset-method-ado.md)или [Close](./close-method-ado.md) ), можно использовать **CancelUpdate** для отмены всех ожидающих изменений. Это может потребоваться, если обновление не удается успешно опубликовать в источнике данных. Например, попытка удаления, которая завершилась сбоем из-за нарушений ссылочной целостности, оставляет **набор записей** в режиме редактирования после вызова метода [Delete](./delete-method-ado-recordset.md).  
  
## <a name="record"></a>Записей  
 Метод **CancelUpdate** отменяет все ожидающие вставки или удаления объектов [полей](./field-object.md) и отменяет отложенные обновления существующих полей и восстанавливает их исходные значения. Свойство [Status](./status-property-ado-recordset.md) всех полей в коллекции **Fields** имеет значение **адфиелдок**.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Коллекция Fields (ADO)](./fields-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Recordset (ADO)](./recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Примеры методов Update и CancelUpdate (Visual Basic)](./update-and-cancelupdate-methods-example-vb.md)   
 [Примеры методов Update и CancelUpdate (Visual c++)](./update-and-cancelupdate-methods-example-vc.md)   
 [Метод AddNew (ADO)](./addnew-method-ado.md)   
 [Метод Cancel (ADO)](./cancel-method-ado.md)   
 [Метод Cancel (RDS)](../rds-api/cancel-method-rds.md)   
 [Метод CancelBatch (ADO)](./cancelbatch-method-ado.md)   
 [Метод CancelUpdate (RDS)](../rds-api/cancelupdate-method-rds.md)   
 [EditMode, свойство](./editmode-property.md)   
 [Метод Update](./update-method.md)