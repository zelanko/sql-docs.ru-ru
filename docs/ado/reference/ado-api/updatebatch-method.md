---
title: Метод UpdateBatch | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::UpdateBatch
- Recordset15::raw_UpdateBatch
helpviewer_keywords:
- UpdateBatch method [ADO]
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 11c930efdffe5eb685494843f2b0abe7b753ea3d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710419"
---
# <a name="updatebatch-method"></a>Метод UpdateBatch
Записывает все ожидающие пакетных обновлений на диск.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Параметры  
 *AffectRecords*  
 Необязательный параметр. [AffectEnum](../../../ado/reference/ado-api/affectenum.md) значение, указывающее, сколько записей **UpdateBatch** повлияет на метод.  
  
 *PreserveStatus*  
 Необязательный. Объект **логическое** значение, указывающее ли изменения, как указано в [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойство, должен быть зафиксирован. Если это значение **True**, **состояние** свойство каждой записи остается неизменным после завершения обновления.  
  
## <a name="remarks"></a>Примечания  
 Используйте **UpdateBatch** метод при изменении **записей** объекта в пакетный режим обновления для передачи все изменения, внесенные в **записей** объекта в основную базу данных.  
  
 Если **записей** объект поддерживает обновление пакета, внесение нескольких изменений в одну или несколько записей можно кэшировать локально до вызова метода **UpdateBatch** метод. При изменении текущей записи или добавления новой записи, при вызове **UpdateBatch** метод, автоматически вызывает ADO [обновления](../../../ado/reference/ado-api/update-method.md) метод для сохранения любых ожидающих изменений в текущую запись, прежде чем передает пакет изменений к поставщику. Следует использовать пакетного обновления с набором ключей или только для статического курсора.  
  
> [!NOTE]
>  Указание **adAffectGroup** так как значение для этого параметра вызовет ошибку при записи не отображается в текущем **записей** (например, для которого нет записей, соответствующих фильтра).  
  
 Если произошел сбой попытки передачи изменений для любого или всех записей из-за конфликта с базовыми данными (например, запись уже был удален другим пользователем), поставщик возвращает предупреждения, чтобы [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции и возникает ошибка времени выполнения. Используйте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство (**adFilterAffectedRecords**) и [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойства для поиска записей с конфликтами.  
  
 Чтобы отменить все ожидающие пакетные обновления, используйте [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) метод.  
  
 Если [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) динамические свойства заданы и **записей** является результатом выполнения операции СОЕДИНЕНИЯ на несколько таблиц, то выполнение **UpdateBatch** метод неявно следуют [Resync](../../../ado/reference/ado-api/resync-method.md) метод, в зависимости от параметров [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) свойство.  
  
 Порядок выполнения отдельных обновлений пакета в источнике данных не обязательно так же, как порядок, в котором они были выполнены на локальном **записей**. Порядок обновления зависит от поставщика. Это учитывать при написании кода обновления, которые связаны друг с другом, например ограничения внешнего ключа в инструкции insert или update.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов UpdateBatch и Cancelbatch по методы (Visual Basic)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch и Cancelbatch методы (Visual C++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
