---
title: Метод Resync | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 251c2f67861dd996ac78efc9a8e599d7ec191072
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711557"
---
# <a name="resync-method"></a>Метод Resync
Обновляет данные в текущем [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, или [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта из базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>Параметры  
 *AffectRecords*  
 Необязательный параметр. [AffectEnum](../../../ado/reference/ado-api/affectenum.md) значение, которое определяет, сколько записей **Resync** повлияет на метод. Значение по умолчанию — **adAffectAll**. Это значение не входит в состав **Resync** метод **поля** коллекцию **записи** объекта.  
  
 *ResyncValues*  
 Необязательный параметр. Объект [ResyncEnum](../../../ado/reference/ado-api/resyncenum.md) значение, которое указывает, перезаписываются ли базового значения. Значение по умолчанию — **adResyncAllValues**.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="recordset"></a>набор записей  
 Используйте **Resync** метод повторная синхронизация записей в текущем **записей** с основной базы данных. Это полезно в том случае, если вы используете статические или однопроходный курсор, но вы хотите просмотреть все изменения в основной базе данных.  
  
 Если задать [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**, **Resync** доступна только для не только для чтения **записей** объектов.  
  
 В отличие от [Requery](../../../ado/reference/ado-api/requery-method.md) метод, **Resync** метод нельзя будет выполнить повторно **записей** основным команды. Новые записи в основной базе данных, не будут видны.  
  
 Если произошел сбой попытки повторной синхронизации из-за конфликта с базовыми данными (например, записи был удален другим пользователем), поставщик возвращает предупреждения, чтобы [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции и ошибку во время выполнения происходит. Используйте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство (**adFilterConflictingRecords**) и [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойства для поиска записей с конфликтами.  
  
 Если [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и [Resync команда](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md) динамические свойства заданы и **записей** является результатом выполнения операции СОЕДИНЕНИЯ на несколько таблиц, а затем  **Повторная синхронизация** метод выполнит команду, заданную в **Resync команда** свойство только для таблицы с именем в **уникальной таблицы** свойство.  
  
## <a name="fields"></a>Поля  
 Используйте **Resync** метода для повторной синхронизации значения **поля** коллекцию **записи** объекта к базовому источнику данных. [Число](../../../ado/reference/ado-api/count-property-ado.md) этот метод не влияет на свойство.  
  
 Если *ResyncValues* присваивается **adResyncAllValues** (значение по умолчанию), [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md), [значение](../../../ado/reference/ado-api/value-property-ado.md), и [ Примеры OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) свойства [поле](../../../ado/reference/ado-api/field-object.md) синхронизации объектов в коллекции. Если *ResyncValues* присваивается **adResyncUnderlyingValues**, только **UnderlyingValue** свойство синхронизируется.  
  
 Значение **состояние** для каждой **поле** во время вызова также влияет на поведение **Resync**. Для **поле** объектов, имеющих **состояние** значения **adFieldPendingUnknown** или **adFieldPendingInsert**, **повторной синхронизации**  не оказывает влияния. Для **состояние** значения **adFieldPendingChange** или **adFieldPendingDelete**, **Resync** синхронизирует данные значения для полей, по-прежнему существует в источнике данных.  
  
 **Повторная синхронизация** не будет изменять **состояние** значения **поле** объектов, пока не произойдет ошибка при **Resync** вызывается. Например, если поле больше не существует, то поставщик возвратит соответствующей **состояние** значение **поле** объект, например **adFieldDoesNotExist**. Возвращаемый **состояние** значения могут быть логически объединены в значении элемента **состояние** свойство.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Повторная синхронизация пример метода (Visual Basic)](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [Повторная синхронизация пример метода (Visual C++)](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)
