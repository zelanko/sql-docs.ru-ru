---
description: Метод Update
title: Метод Update | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Update
helpviewer_keywords:
- Update method [ADO]
ms.assetid: 6b2a9c31-1a7e-40db-8a53-30720d0f6cc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 906a2ffb29345a2bbefdbf5a6bde6e71cd1c5af1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441646"
---
# <a name="update-method"></a>Метод Update
Сохраняет любые изменения, внесенные в текущую строку объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , или коллекцию [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) объекта [Record](../../../ado/reference/ado-api/record-object-ado.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Update Fields, Values  
record.Fields.Update  
```  
  
#### <a name="parameters"></a>Параметры  
 *Поля*  
 Необязательный параметр. **Вариант** , представляющий одно имя или массив **Variant** , представляющий имена или порядковые позиции поля или полей, которые требуется изменить.  
  
 *Значения*  
 Необязательный параметр. **Вариант** , представляющий одиночное значение, или массив **Variant** , представляющий значения для поля или полей в новой записи.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="recordset"></a>набор записей  
 Используйте метод **Update** , чтобы сохранить изменения, внесенные в текущую запись объекта **набора записей** , с момента вызова метода [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) или изменения любых значений полей в существующей записи. Объект **набора записей** должен поддерживать обновления.  
  
 Чтобы задать значения полей, выполните одно из следующих действий.  
  
-   Присвойте значения свойству [значения](../../../ado/reference/ado-api/value-property-ado.md) объекта [поля](../../../ado/reference/ado-api/field-object.md) и вызовите метод **Update** .  
  
-   Передайте имя поля и значение в качестве аргументов в вызове **Update** .  
  
-   Передайте массив имен полей и массив значений с помощью вызова **Update** .  
  
 При использовании массивов полей и значений должно быть одинаковое число элементов в обоих массивах. Кроме того, порядок имен полей должен совпадать с порядком значений полей. Если число и порядок полей и значений не совпадают, возникает ошибка.  
  
 Если объект **Recordset** поддерживает пакетное обновление, можно кэшировать несколько изменений в одной или нескольких записях локально, пока не будет вызван метод [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) . Если вы изменяете текущую запись или добавляете новую запись при вызове метода **UpdateBatch** , ADO автоматически вызывает метод **Update** , чтобы сохранить все ожидающие изменения в текущей записи перед передачей пакетных изменений поставщику.  
  
 Если вы перейдете из записи, которая добавляется или редактируется перед вызовом метода **Update** , то ADO автоматически вызовет **Update** для сохранения изменений. Если необходимо отменить все изменения, внесенные в текущую запись, или удалить вновь добавленную запись, необходимо вызвать метод [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) .  
  
 Текущая запись остается текущей после вызова метода **Update** .  
  
## <a name="record"></a>Записей  
 Метод **Update** завершает Добавление, удаление и обновление полей в коллекции [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) объекта **Record** .  
  
 Например, поля, удаленные с помощью метода **Delete** , помечаются для удаления немедленно, но остаются в коллекции. Для фактического удаления этих полей из коллекции поставщика необходимо вызвать метод **Update** .  
  
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
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode, свойство](../../../ado/reference/ado-api/editmode-property.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
