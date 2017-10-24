---
title: "Метод обновления | Документы Microsoft"
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
- Recordset15::Update
helpviewer_keywords:
- Update method [ADO]
ms.assetid: 6b2a9c31-1a7e-40db-8a53-30720d0f6cc1
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 287fb5bf8b87a8371ee84d89ba4e5efee6b3587f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="update-method"></a>Метод обновления
Сохраняет любые изменения, внесенные в текущей строке [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, или [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Update Fields, Values  
record.Fields.Update  
```  
  
#### <a name="parameters"></a>Параметры  
 *Поля*  
 Необязательно. Объект **Variant** , представляющий одно имя или **Variant** массив, представляющий имена или порядковые номера полей, которые вы хотите изменить.  
  
 *Значения*  
 Необязательно. Объект **Variant** , представляющий одно значение или **Variant** массив, представляющий значения для поля или поля в новой записи.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="recordset"></a>набор записей  
 Используйте **обновление** метод, чтобы сохранить любые изменения, внесенные в текущую запись **записей** объект с момента вызова [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) метода или с момента изменять любые значения полей в существующие записи. **Записей** объект должен поддерживать обновлений.  
  
 Для задания значений полей, выполните одно из следующих действий.  
  
-   Назначить значения для [поле](../../../ado/reference/ado-api/field-object.md) объекта [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство и вызвать **обновление** метод.  
  
-   Передайте имя поля и значение в качестве аргументов с **обновление** вызова.  
  
-   Передайте массив имен полей и массив значений с **обновление** вызова.  
  
 При использовании массивов поля и значения, должен быть равен числу элементов в обоих массивов. Кроме того порядок имена полей должен соответствовать порядку значений полей. Если число и порядок полей и значения не совпадают, происходит ошибка.  
  
 Если **записей** объект поддерживает обновление пакета, можно кэшировать внесение нескольких изменений в одну или несколько записей локально до вызова [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод. При изменении текущей записи или добавления новой записи, при вызове **UpdateBatch** метода ADO будет автоматически вызывать **обновление** метод, чтобы сохранить все ожидающие изменения для текущей записи, прежде чем передает пакет изменений к поставщику.  
  
 При перемещении из записи при добавлении или изменении перед вызовом **обновление** метода ADO будет автоматически вызывать **обновление** для сохранения изменений. Необходимо вызвать [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод, если вы хотите отменить изменения, внесенные в текущую запись или отменить вновь добавленной записи.  
  
 Текущая запись остаются актуальными, после вызова метода **обновление** метод.  
  
## <a name="record"></a>Записей  
 **Обновление** завершает метод дополнения, удаления и обновления полей в [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию **записи** объекта.  
  
 Например, поля, удаленные с помощью **удалить** метода, помечаются для удаления сразу, но остаются в коллекции. **Обновление** метод должен вызываться Действительно удалить эти поля из коллекции поставщиков.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также:  
 [Обновление и пример CancelUpdate методы (Visual Basic)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Обновление и пример методы CancelUpdate (VC ++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [Метод AddNew (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Свойство EditMode](../../../ado/reference/ado-api/editmode-property.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)

