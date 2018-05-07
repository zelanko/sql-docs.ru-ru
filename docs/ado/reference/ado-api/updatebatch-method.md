---
title: Метод UpdateBatch | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::UpdateBatch
- Recordset15::raw_UpdateBatch
helpviewer_keywords:
- UpdateBatch method [ADO]
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75fa802b85b1bdb9f2dcd97af8c244a41f7ec37b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="updatebatch-method"></a>Метод UpdateBatch
Записывает все ожидающие пакетных обновлений на диск.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Параметры  
 *AffectRecords*  
 Необязательно. [AffectEnum](../../../ado/reference/ado-api/affectenum.md) значение, указывающее, сколько записей **UpdateBatch** повлияет на метод.  
  
 *PreserveStatus*  
 Необязательно. Объект **логическое** значение, указывающее ли изменения, как указано в [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойство, должна быть зафиксирована. Если это значение равно **True**, **состояние** свойства каждой записи остается неизменным после завершения обновления.  
  
## <a name="remarks"></a>Замечания  
 Используйте **UpdateBatch** метод при изменении **записей** объекта в пакетный режим обновления для передачи все изменения, внесенные в **записей** объекта в основной базе данных.  
  
 Если **записей** объект поддерживает обновление пакета, можно кэшировать внесение нескольких изменений в одну или несколько записей локально до вызова **UpdateBatch** метод. При изменении текущей записи или добавления новой записи, при вызове **UpdateBatch** метода ADO будет автоматически вызывать [обновление](../../../ado/reference/ado-api/update-method.md) метод, чтобы сохранить все ожидающие изменения для текущей записи, прежде чем передает пакет изменений к поставщику. Следует использовать пакетного обновления с набором ключей или статическом курсоре только.  
  
> [!NOTE]
>  Указание **adAffectGroup** как значение для этого параметра приведет к произошла ошибка при записи не видны в текущем **записей** (например, фильтр, для которого нет записей, соответствующих).  
  
 Если произошел сбой попытки передачи изменений для нескольких или всех записей из-за конфликта с базовыми данными (например, запись уже был удален другим пользователем), поставщик возвращает предупреждения, чтобы [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции и возникает ошибка во время выполнения. Используйте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство (**adFilterAffectedRecords**) и [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойство для поиска записей с конфликтами.  
  
 Чтобы отменить все ожидающие пакетные обновления, используйте [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) метод.  
  
 Если [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и [Resync обновление](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) динамических свойств и **набора записей** является результатом выполнения операции СОЕДИНЕНИЯ на несколько таблиц, то выполнение **UpdateBatch** метод неявно следуют [Resync](../../../ado/reference/ado-api/resync-method.md) метод в зависимости от параметров [обновление Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) свойство.  
  
 Порядок выполнения отдельных обновлений пакета в источнике данных не обязательно является таким же, как порядок, в котором они были выполнены на локальном **записей**. Порядок обновления зависит от поставщика. Это учитывать при программировании обновлений, которые связаны друг с другом, например ограничения внешнего ключа для вставки или обновления.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [UpdateBatch и пример CancelBatch методы (Visual Basic)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch и CancelBatch примере методы (VC ++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Метод Update](../../../ado/reference/ado-api/update-method.md)
