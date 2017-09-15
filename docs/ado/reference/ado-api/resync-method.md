---
title: "Повторная синхронизация метод | Документы Microsoft"
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
- Recordset20::raw_Resync
- Fields::Resync
- Recordset20::Resync
- Fields::raw_Resync
helpviewer_keywords:
- Resync method [ADO]
ms.assetid: 73b355d4-a4c0-434b-bfc4-039b1c76b32e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 392dd82f2b6412c537a86cc68331cffc852069b8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="resync-method"></a>Метод повторной синхронизации
Обновляет данные в текущем [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, или [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта из базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>Параметры  
 *AffectRecords*  
 Необязательно. [AffectEnum](../../../ado/reference/ado-api/affectenum.md) значение, которое определяет, сколько записей **Resync** повлияет на метод. Значение по умолчанию — **adAffectAll**. Это значение не может применяться к **Resync** метод **поля** коллекцию **записи** объекта.  
  
 *ResyncValues*  
 Необязательно. Объект [ResyncEnum](../../../ado/reference/ado-api/resyncenum.md) значение, которое указывает, перезаписываются ли базового значения. Значение по умолчанию — **adResyncAllValues**.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="recordset"></a>набор записей  
 Используйте **Resync** метод повторная синхронизация записей в текущем **записей** с основной базы данных. Это полезно в том случае, если вы используете статические или однонаправленного курсора, но вы хотите просмотреть все изменения в базе данных.  
  
 Если задать [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**, **Resync** доступен только для не только для чтения **набора записей** объектов.  
  
 В отличие от [Requery](../../../ado/reference/ado-api/requery-method.md) метод, **Resync** повторно не выполняет метод **записей** основным команды. Новые записи в базе данных не будут видны.  
  
 Если повторная синхронизация не удастся из-за конфликта с базовыми данными (например, запись удалена другим пользователем), поставщик возвращает предупреждения, чтобы [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции и во время выполнения возникает ошибка. Используйте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство (**adFilterConflictingRecords**) и [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойство для поиска записей с конфликтами.  
  
 Если [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и [Resync команда](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) динамических свойств и **записей** является результатом выполнения операции СОЕДИНЕНИЯ на несколько таблиц, а затем ** Повторная синхронизация** метод будет выполняться команду, заданную в **Resync команда** свойство только для таблицы, указанной в **уникальной таблицы** свойство.  
  
## <a name="fields"></a>Поля  
 Используйте **Resync** метода для повторной синхронизации значения **поля** коллекцию **записи** объекта с базового источника данных. [Число](../../../ado/reference/ado-api/count-property-ado.md) этот метод не повлияло на свойство.  
  
 Если *ResyncValues* равно **adResyncAllValues** (значение по умолчанию), [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md), [значение](../../../ado/reference/ado-api/value-property-ado.md), и [ OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) свойства [поле](../../../ado/reference/ado-api/field-object.md) синхронизацию объектов в коллекции. Если *ResyncValues* равно **adResyncUnderlyingValues**только **UnderlyingValue** свойство синхронизированным.  
  
 Значение **состояние** свойства каждого **поле** во время вызова также влияет на поведение **Resync**. Для **поле** объектов, у которых **состояние** значения **adFieldPendingUnknown** или **adFieldPendingInsert**, **повторной синхронизации ** не делает ничего. Для **состояние** значения **adFieldPendingChange** или **adFieldPendingDelete**, **Resync** синхронизирует значения данных для поля, по-прежнему существует в источнике данных.  
  
 **Повторная синхронизация** не будет изменять **состояние** значения **поля** объекты, пока не произойдет ошибка при **Resync** вызывается. Например, если оно больше не существует, то поставщик возвратит соответствующей **состояние** значение для **поле** объект, такой как **adFieldDoesNotExist**. Возвращаемый **состояние** значения могут быть логически объединены в значение **состояние** свойство.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также:  
 [Повторная синхронизация пример метода (Visual Basic)](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [Повторная синхронизация пример метода (VC ++)](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)

