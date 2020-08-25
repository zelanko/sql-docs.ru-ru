---
description: Метод UpdateBatch
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b462fb22758481f3237a2a8c793b76dc50956ad
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776963"
---
# <a name="updatebatch-method"></a>Метод UpdateBatch
Записывает все ожидающие пакетные обновления на диск.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>Параметры  
 *аффектрекордс*  
 Необязательный элемент. Значение [аффектенум](./affectenum.md) , указывающее, сколько записей будет влиять на метод **UpdateBatch** .  
  
 *пресервестатус*  
 Необязательный элемент. **Логическое** значение, указывающее, должны ли быть зафиксированы локальные изменения, указанные в свойстве [Status](./status-property-ado-recordset.md) . Если это значение равно **true**, свойство **Status** каждой записи остается неизменным после завершения обновления.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **UpdateBatch** при изменении объекта **набора записей** в режиме пакетного обновления для передачи всех изменений, внесенных в объект **набора записей** , в основную базу данных.  
  
 Если объект **Recordset** поддерживает пакетное обновление, можно кэшировать несколько изменений в одной или нескольких записях локально, пока не будет вызван метод **UpdateBatch** . Если вы изменяете текущую запись или добавляете новую запись при вызове метода **UpdateBatch** , ADO автоматически вызывает метод [Update](./update-method.md) , чтобы сохранить все ожидающие изменения в текущей записи перед передачей пакетных изменений поставщику. Пакетное обновление следует использовать только с курсором KEYSET или static.  
  
> [!NOTE]
>  Указание **адаффектграуп** в качестве значения для этого параметра приведет к ошибке, если в текущем **наборе записей** нет видимых записей (например, фильтра, для которого не совпадают записи).  
  
 Если попытка передать изменения для всех или всех записей завершается неудачей из-за конфликта с базовыми данными (например, запись уже удалена другим пользователем), поставщик возвращает предупреждения в коллекцию [ошибок](./errors-collection-ado.md) и возникает ошибка времени выполнения. Используйте свойство [Filter](./filter-property.md) (**адфилтераффектедрекордс**) и свойство [Status](./status-property-ado-recordset.md) для обнаружения записей с конфликтами.  
  
 Чтобы отменить все отложенные обновления пакетов, используйте метод [CancelBatch](./cancelbatch-method-ado.md) .  
  
 Если задана [уникальная таблица](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) и динамические свойства повторной [синхронизации обновления](./update-resync-property-dynamic-ado.md) , а **набор записей** является результатом выполнения операции JOIN над несколькими таблицами, то при выполнении метода **UpdateBatch** в зависимости от параметров свойства " [Обновить повторную](./update-resync-property-dynamic-ado.md) синхронизацию" неявно следует метод повторной [синхронизации](./resync-method.md) .  
  
 Порядок, в котором отдельные обновления пакета выполняются в источнике данных, не обязательно совпадает с порядком, в котором они были выполнены в локальном **наборе записей**. Порядок обновления зависит от поставщика. Примите это во внимание при программировании обновлений, связанных друг с другом, таких как ограничения внешнего ключа при вставке или обновлении.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов UpdateBatch и CancelBatch (Visual Basic)](./updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Примеры методов UpdateBatch и CancelBatch (Visual c++)](./updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод CancelBatch (ADO)](./cancelbatch-method-ado.md)   
 [Метод Clear (ADO)](./clear-method-ado.md)   
 [Свойство LockType (ADO)](./locktype-property-ado.md)   
 [Метод Update](./update-method.md)