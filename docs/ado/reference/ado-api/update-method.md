---
title: Обновите метод | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae2645057670ba65a33bb8b5da238c7e01790ae9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042240"
---
# <a name="update-method"></a>Метод Update
Сохраняет любые изменения, вносимые в текущей строке [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, или [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Update Fields, Values  
record.Fields.Update  
```  
  
#### <a name="parameters"></a>Параметры  
 *Fields*  
 Необязательный параметр. Объект **Variant** , представляющий одно имя, или **Variant** массив, представляющий имена или порядковые номера поле или поля, которую нужно изменить.  
  
 *Значения*  
 Необязательный. Объект **Variant** , представляющий одно значение, или **Variant** массив, представляющий значения для поля или поля в новой записи.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="recordset"></a>набор записей  
 Используйте **обновление** метод, чтобы сохранить любые изменения, внесенные в текущую запись **записей** объекта с момента вызова [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) метод или после изменения значения поля в существующей записи. **Записей** объект должен поддерживать обновления.  
  
 Чтобы задать значения полей, выполните одно из следующих действий.  
  
-   Назначение значений [поле](../../../ado/reference/ado-api/field-object.md) объекта [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство и вызвать **обновления** метод.  
  
-   Передать имя поля и значение в качестве аргументов с **обновления** вызова.  
  
-   Передайте массив имен полей и массив значений с **обновления** вызова.  
  
 При использовании массивов полей и значений, должно быть одинаковое число элементов в обоих массивах. Кроме того порядок имен полей должен соответствовать порядку значений полей. Если число и порядок полей и значения не совпадают, возникает ошибка.  
  
 Если **записей** объект поддерживает обновление пакета, внесение нескольких изменений в одну или несколько записей можно кэшировать локально до вызова метода [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод. При изменении текущей записи или добавления новой записи, при вызове **UpdateBatch** метод, автоматически вызывает ADO **обновления** метод для сохранения любых ожидающих изменений в текущую запись, прежде чем передает пакет изменений к поставщику.  
  
 При перемещении из записи при добавлении или редактировании перед вызовом **обновление** метод, автоматически вызывает ADO **обновления** для сохранения изменений. Необходимо вызвать [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод, если вы хотите отменить любые изменения, внесенные в текущую запись или отменить вновь добавленной записи.  
  
 Текущая запись остается текущее, после вызова метода **обновления** метод.  
  
## <a name="record"></a>Записей  
 **Обновление** метод завершает дополнения, удаления и обновления полей в [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию **записи** объекта.  
  
 Например, поля, удаляется при помощи **удалить** метода, помечаются для удаления немедленно, но остаются в коллекции. **Обновления** метод должен вызываться действительности удалить эти поля из коллекции поставщика.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Обновление методов и Cancelupdate (Visual Basic)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Обновление методов и Cancelupdate (Visual C++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [Метод AddNew (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Свойство EditMode](../../../ado/reference/ado-api/editmode-property.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
