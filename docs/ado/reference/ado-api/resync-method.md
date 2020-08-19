---
description: Метод Resync
title: Повторно синхронизировать метод | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_Resync
- Fields::Resync
- Recordset20::Resync
- Fields::raw_Resync
helpviewer_keywords:
- Resync method [ADO]
ms.assetid: 73b355d4-a4c0-434b-bfc4-039b1c76b32e
author: rothja
ms.author: jroth
ms.openlocfilehash: 68ece4d9ad109defafa8a0c64dbf901fb20a87b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442276"
---
# <a name="resync-method"></a>Метод Resync
Обновляет данные в текущем объекте [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) или коллекции [полей](../../../ado/reference/ado-api/fields-collection-ado.md) объекта [записи](../../../ado/reference/ado-api/record-object-ado.md) из базовой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>Параметры  
 *аффектрекордс*  
 Необязательный параметр. Значение [аффектенум](../../../ado/reference/ado-api/affectenum.md) , определяющее количество записей, на которые будет влиять метод повторной **синхронизации** . Значение по умолчанию — **адаффекталл**. Это значение недоступно в методе **Resync** коллекции **Fields** объекта **Record** .  
  
 *ресинквалуес*  
 Необязательный параметр. Значение [ресинценум](../../../ado/reference/ado-api/resyncenum.md) , указывающее, перезаписываются ли базовые значения. Значение по умолчанию — **адресинкаллвалуес**.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="recordset"></a>набор записей  
 Используйте метод **Resync** для повторной синхронизации записей в текущем **наборе записей** с базовой базой данных. Это полезно, если используется либо статический, либо однонаправленный курсор, но вы хотите видеть изменения в основной базе данных.  
  
 Если для свойства [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) задано значение **адусеклиент**, **Повторная синхронизация** доступна только для объектов **Recordset** , не являющихся доступными только для чтения.  
  
 В отличие от метода [Resync](../../../ado/reference/ado-api/requery-method.md) , метод **Resync** не выполняет повторное выполнение базовой команды объекта **Recordset** . Новые записи в базовой базе данных не будут видны.  
  
 Если попытка повторной синхронизации завершается сбоем из-за конфликта с базовыми данными (например, запись была удалена другим пользователем), поставщик возвращает предупреждения в коллекцию [ошибок](../../../ado/reference/ado-api/errors-collection-ado.md) и возникает ошибка времени выполнения. Используйте свойство [Filter](../../../ado/reference/ado-api/filter-property.md) (**адфилтерконфликтингрекордс**) и свойство [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) для обнаружения записей с конфликтами.  
  
 Если заданы динамические свойства [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и повторной [синхронизации](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) , а **набор записей** является результатом выполнения операции объединения нескольких таблиц, то метод **Resync** выполняет команду, указанную в свойстве Command повторной **синхронизации** , только для таблицы, указанной в свойстве **уникальной таблицы** .  
  
## <a name="fields"></a>Поля  
 Используйте метод **Resync** для повторной синхронизации значений коллекции **Fields** объекта **Record** с базовым источником данных. Этот метод не влияет на свойство [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
 Если для *ресинквалуес* задано значение **адресинкаллвалуес** (по умолчанию), то свойства [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md), [value](../../../ado/reference/ado-api/value-property-ado.md)и [originalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) объектов [field](../../../ado/reference/ado-api/field-object.md) в коллекции синхронизируются. Если для *ресинквалуес* задано значение **адресинкундерлингвалуес**, то синхронизируется только свойство **UnderlyingValue** .  
  
 Значение свойства **Status** для каждого объекта **поля** во время вызова также влияет на поведение повторной **синхронизации**. Для **объектов Field** , имеющих **значения состояния** **адфиелдпендингункновн** или **адфиелдпендингинсерт**, **Повторная синхронизация** не действует. Для значений **состояния** **адфиелдпендингчанже** или **адфиелдпендингделете**повторная **Синхронизация** синхронизирует значения данных для полей, которые еще существуют в источнике данных.  
  
 **Повторная синхронизация** не приведет к изменению значений **состояния** объектов **полей** , если не возникает ошибка при вызове повторной **синхронизации** . Например, если поле больше не существует, поставщик возвратит соответствующее значение **состояния** для объекта **поля** , например **адфиелддоеснотексист**. Возвращаемые значения **состояния** могут быть логически объединены в значение свойства **Status** .  
  
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
 [Пример метода Resync (Visual Basic)](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [Пример метода Resync (Visual c++)](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)
